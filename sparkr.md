# SparkR

---

- Spark as the computing backend

  Apache Spark is an open-source data analytics cluster computing framework. Spark is not tied to the two-stage MapReduce paradigm, and promises performance up to 100 times faster than Hadoop MapReduce for certain applications. Spark provides primitives for in-memory cluster computing that allows user programs to load data into a cluster's memory and query it repeatedly, making it well suited to machine learning algorithms. [[reference](https://www.rcac.purdue.edu/compute/hathi/guide/#run_hadoop_examples_spark)]
  
  * Resilient Distributed Datasets (RDDs)

  * DAG
    
    Applications create linked sequences of operations. <font color='red'>Catalyst as the optimizer?</font>
    
  * In-memory computing

    Spark stores data in memory between operations, as opposed to writing data to disk required by Hadoop. This makes iterative algorithm and interactive data analysis possible and efficient in Spark

  * Core API (Scala, Python) is general purpose

    All language functionality of Scala can be accessed by Spark. <font color='red'>But SparkR only exposes a small subset of high-level operations.</font>
  
  * Interactive programming environment

- SparkR architecture

  <font color='red'>TODO: Refer to the paper "SparkR: Scaling R Programs with Spark"</font>

  * Key features in its implementation 
    +  R-JVM bridge
       Older versions use rJava. Now has its own implementation.
       
  * More packages are under development, e.g. ggplot2.sparkr

- [RHadoop](https://github.com/RevolutionAnalytics/RHadoop/wiki) <font color='red'>(development seems to be paused)</font>

- Limitations of the approaches in this chapter
* It reduces performance overhead

  Running an algorithm in R on top of a JVM-based language like Java or Scala, we have to do some work to pass code and data across the different environments.[^R-JVM_overhead]

* Lack native language support for R

  For example, SparkR is an R wrapper for Spark. Its API only provide limited high-level operations. Typical RDD operations like map, flatMap, reduce or filter are gone in SparkR. Lacking low level ETL prohibits it from many use cases.

  **Note** Some low level API are available through `SparkR:::`. But it is in general not a good practice to use those private functions in your coding. In addition, Pre 1.4 low level API is embarrassingly slow and clumsy and without all the goodness of the Catalyst optimizer it is most likely the same when it comes to internal 1.4 API.[^SparkR_low_level_api_slow]


[Examples](./sparkr_examples.md)


---

[^R-JVM_overhead]: Advanced Analytics with Spark p24.
[^SparkR_low_level_api_slow]: [Reading Text file in SparkR 1.4.0](http://stackoverflow.com/questions/31157649/reading-text-file-in-sparkr-1-4-0)


