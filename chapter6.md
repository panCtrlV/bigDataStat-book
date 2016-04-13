
# Chapter 6 Combining R and Distributed Computing Platforms

---

## Outline

The most popular solution for using R in large scale distributed computing is to injesting R into one of the existing distributed computing platforms, like Hadoop and Spark.

- Tessera

- [SparkR](https://spark.apache.org/docs/latest/sparkr.html)

- [**RHadoop**](https://github.com/RevolutionAnalytics/RHadoop/wiki) <font color='red'>(development seems to be paused)</font>

- Limitations of the approaches in this chapter
  * It reduces performance overhead

    Running an algorithm in R on top of a JVM-based language like Java or Scala, we have to do some work to pass code and data across the different environments.[^R-JVM_overhead]

  * Lack native language support for R

    For example, SparkR is an R wrapper for Spark. Its API only provide limited high-level operations. Typical RDD operations like map, flatMap, reduce or filter are gone in SparkR. Lacking low level ETL prohibits it from many use cases.

    **Note** Some low level API are available through `SparkR:::`. But it is in general not a good practice to use those private functions in your coding. In addition, Pre 1.4 low level API is embarrassingly slow and clumsy and without all the goodness of the Catalyst optimizer it is most likely the same when it comes to internal 1.4 API.[^SparkR_low_level_api_slow]

  * More statistical and machine learning packages need to be developed for each solution