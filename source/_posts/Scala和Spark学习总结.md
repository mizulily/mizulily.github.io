---
title: Scala和Spark学习总结
date: 2017-08-01 15:03:26
tags:
- scala
- spark
- study
---
在两个多月的实习时间里，我学习并掌握了Hive、Scala、Spark的基本用法，并将它们用在处理大规模的LBS数据来完成用户家庭、工作地址预测和POI信息关联及推荐等任务。期间遇到了很多坑，慢慢摸索之后才把它们都处理好。<!--more-->
## 学习资料推荐
### Scala
* [网站-Scala官方文档](http://docs.scala-lang.org)
* [书籍-Scala编程实战](https://book.douban.com/subject/26826535/)
* [编程环境-IDEA及其Scala插件](https://www.jetbrains.com/idea/)

### Spark
* [网站-Spark官方文档](http://spark.apache.org/docs/latest/)
* [书籍-Spark快速大数据分析](https://book.douban.com/subject/26616244/)
* [网站-Spark第三方包索引](https://spark-packages.org)

## 遇到的坑
在应用的过程中，由于自己学习时间并不长，很多细节没有太注意，经验也不足，遇到了一些坑，大多数在网上搜索一番后找到了解决办法。我把它们一个个罗列在下面。
### #0:广播变量Broadcast与App特质的Bug
这个bug的描述和解决方法参见[这里](https://stackoverflow.com/questions/31303827/spark-broadcasted-variable-returns-nullpointerexception-when-run-in-amazon-emr-c)。广播变量在Spark中是用来将你的变量发送到集群的各个工作节点上以便被它们使用。App特质是Scala中比较常用的特质，定义好了很多实用的方法，如计时器，而且不用定义主函数，object本身即是主函数。但是这两个特性合起来就会出问题，如果使用了App特质，那么程序中的广播变量就会不起作用，解决办法就是不使用App特质。

### #1:Scala中的case class的equals方法与普通class不同
这个细节问题是我在改写GitHub上的DBSCAN算法的代码时发现的。为了防止算法在处理大规模数据时会出现内存耗尽的问题，我需要使用集合Set来判断现在处理的数据点是否已经在Set中，防止重复添加大量相同的点到处理队列中导致内存耗尽。数据点是用case class定义的，初始定义代码如下：

 ``` scala
import org.apache.spark.mllib.linalg.Vector
import scala.math._
case class DBSCANPoint(val vector: Vector) {

  def x = vector(0)
  def y = vector(1)

  def distanceSquared(other: DBSCANPoint): Double = {
    val dx = other.x - x
    val dy = other.y - y
    (dx * dx) + (dy * dy)
  }
    }
}
 ```
 
因为这个DBSCANPoint是用case class定义的，参数是vector，而case class会帮你把诸如equals、toString、hashCode这些方法都按照一定的规范实现好。而当定义两个用相同的vector创建的DBSCANPoint实例时，用equals去比较两个实例时会返回true，因为它们的成员变量是相等的。但是如果在定义这个类不使用case class而使用普通的class，用equals去比较它们会返回false。但是我在处理LBS数据（即经纬度数据）时，会碰到很多经纬度一样的数据点，但是在算法处理它们时，并不能把它们看成同一个点，所以用上面这种方法定义DBSCANPoint就会出问题。我的解决办法就是在类的定义中添加一个id作为参数，这样就可以把经纬度相同的点给区分开来。

### #2:RDD的first操作只会执行一个分区的转换操作
由于Spark中的转化操作是采用惰性求值的机制(参见《Spark快速大数据分析》3.3.3），所以程序会在行动操作前将多个转化操作合并起来优化执行。但是当我们想去估计每个转化操作的时间时就不对了，因为当程序执行到转换操作时，其实它们并没有真正的执行，你在每个步骤之间用计时的函数去估计时间时就会发现每一步都很快，只有在行动操作时会消耗很长的时间。本应该使用collect这个执行操作去强制执行转换操作来估计时间，但是在出来大规模数据时collect操作很有可能会因为数据量太大，导致driver节点的内存被耗尽。所以我采用了first这个执行操作，本以为first这个操作也会强制执行前面的转化操作，但是后来我发现first操作只会对其中的一个partition执行转化操作，其他的分区并不会执行，因为我在log中发现，每次执行到first这一步骤的时候，都只有一个partition输出，无论我原来的RDD有多少分区，让我一度以为我的partition失败了。所以用first操作去强制执行转化操作来估计时间是不行的，后来我采用count操作来强制执行前面的转化操作，来估计每一个转化操作的时间。

 ``` scala
import scala.compat.Platform.currentTime

object Test {
	def main(args: Array[String]): Unit = {
		/**
		  * Code to create a rdd
		  * /
		var start = currentTime
		val rdd2 = rdd.map(myMapFunction(_)).cache()
		rdd2.count()
		println(s"Time for map is ${(currentTime-start).toDouble / 1000.0} seconds.")
	}
}
 ```

### #3:Java在Spark中的函数传递方法
虽然平常写的是Scala代码，但是有很多jar包都是用Java来编程和编译的，所以对Spark的Java API也要有所了解，相比Scala，Java（Java 8以前的版本，Java 8 引入了lambda表达式）就麻烦很多，需要实现 org.apache.spark.api.java.function包中的函数接口，见《Spark快速大数据分析》3.4.3。了解这些之后对理解Java版的Spark代码有很大帮助。

### #4:spark-submit中client和cluster模式的区别
在spark-submit命令中可以设定deploy-mode，有client和cluster模式，这两者之间的区别参见《Spark快速大数据分析》7.3的表7-2中的描述：在客户端（client）模式下，spark-submit会将驱动器程序运行在spark-submit被调用的这台机器上；在集群（cluster）模式下，驱动器程序会被传输并执行于集群的一个工作节点上。client模式的优势在于，程序运行的log都会在命令行窗口中显示出来，方便调试；而cluster模式下只能到Web UI中才能查看log，但是好处在于程序运行时，与本地的电脑没有任何关系，适合应用于生产环境。除了在deploy-mode参数中设置以外，还可以通过master参数设置，例如yarn-client或者yarn-cluster就代表这两种模式。

### #5:默认的文件读取与保存的路径
在spark中读取某个文件时，默认是在hdfs上去找这个文件，例如textFile函数，如果路径参数是"./a.txt"，那么Spark会去"hdfs:///users/your_username/a.txt"这个路径上去读取文件，如果要让Spark在本地的目录读取文件，需要在路径前面加上"File://",例如"File:///home/your_username/a.txt"。

## Spark学习笔记
### Hive和Spark的接口
通常大规模数据都在集群上的数据仓库Hive中，数据庞大以至于我们不可能把数据都download到本地来处理，我们需要把Hive中的数据读取出来并转换成Spark可以操作的RDD，进行一系列处理，然后再把运行结果RDD转换成一个表保存起来。这就需要我们利用Spark和Hive的接口来进行这一系列操作，参见[官网教程](http://spark.apache.org/docs/latest/sql-programming-guide.html#hive-metastore-parquet-table-conversion)。
#### 从Hive中读取数据保存成RDD
 ``` scala
import org.apache.spark.sql.Row
import org.apache.spark.sql.SparkSession
import org.apache.spark.rdd.RDD
import org.apache.spark.sql.types._

def main(args: Array[String]) {
    val spark = SparkSession.builder().appName("Hive Spark Test").enableHiveSupport().getOrCreate()
    import spark.implicits._
    import spark.sql
    sql("use your_database")
    val df = sql(s"select * from your_table")
    val rdd = df.rdd
    val rdd2 = rdd.map(x => (x._1.toString, x._2.toString))
  }
}
 ```
其中rdd是一个RDD[Row]类型的变量，Row是一个tuple，这个RDD中的每一行就是原来表中的每一行，tuple在scala中是通过"._x"去索引的，x是从1开始的整数，这个数字代表数据是原来表中的第几列。
#### 将RDD保存成Hive表
 ``` scala
/**
  *接上一小节代码
  */
  val schema = StructType(Seq(
      StructField("Col_1", StringType, true),
      StructField("Col_2", StringType, true)))
  val rowRDD = rdd2.map(x => Row(x._1, x._2))
  val result_df = spark.createDataFrame(rowRDD, schema)
  result_df.registerTempTable("tmp_table")
  sql("drop table if exists new_table")
  sql("create table if not exists new_table as select * from tmp_table")
  sql("select * from new_table").show()
 ```
这个过程就是上一个过程的逆过程，把RDD通过一个schema转换成一个DataFrame，然后保存到Hive中。



