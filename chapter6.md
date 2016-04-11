# Chapter 6 Combining R and Distributed Computing Platforms

---

The most popular solution for using R in large scale distributed computing is to injesting R into one of the existing distributed computing platforms, like Hadoop and Spark.

- [Tessera](http://tessera.io/)
  - Hadoop YARN/MRv2 as the computing backend
  - HDFS as distributed data storage
  - R as the front end
  - Rhipe as the connector between R and Hadoop

- [SparkR](https://spark.apache.org/docs/latest/sparkr.html)
  - Spark as the computing backend
    
    Apache Spark is an open-source data analytics cluster computing framework. Spark is not tied to the two-stage MapReduce paradigm, and promises performance up to 100 times faster than Hadoop MapReduce for certain applications. Spark provides primitives for in-memory cluster computing that allows user programs to load data into a cluster's memory and query it repeatedly, making it well suited to machine learning algorithms. [[reference](https://www.rcac.purdue.edu/compute/hathi/guide/#run_hadoop_examples_spark)]
    
    * DAG
    * In-memory computing
      
      This makes iterative computing possible and efficient in Spark
      
    * Core API (Scala, Python) is general purpose
    * Interactive programming environment

  - SparkR allows code evaluation in R
    * Key features in its implementation 
      +  R-JVM bridge
    * More packages are under development, e.g. ggplot2.sparkr

- [RHadoop](https://github.com/RevolutionAnalytics/RHadoop/wiki)


