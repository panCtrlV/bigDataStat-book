# Spark and SparkR

---

- Spark as the Computing Backend

  Apache Spark is an open-source data analytics cluster computing framework. Spark is not tied to the two-stage MapReduce paradigm, and promises performance up to 100 times faster than Hadoop MapReduce for certain applications. Spark provides primitives for in-memory cluster computing that allows user programs to load data into a cluster's memory and query it repeatedly, making it well suited to machine learning algorithms. [[reference](https://www.rcac.purdue.edu/compute/hathi/guide/#run_hadoop_examples_spark)]
  
  * Resilient Distributed Datasets (RDDs)

  * DAG
    
    Applications create linked sequences of operations. <font color='red'>Catalyst as the optimizer?</font>
    
  * In-memory computing

    Spark stores data in memory between operations, as opposed to writing data to disk required by Hadoop. This makes iterative algorithm and interactive data analysis possible and efficient in Spark

  * Core API (Scala, Python) is general purpose

    All language functionality of Scala can be accessed by Spark. <font color='red'>But SparkR only exposes a small subset of high-level operations.</font>
  
  * Interactive programming environment

- SparkR Architecture

  <font color='red'>TODO: Refer to the paper "SparkR: Scaling R Programs with Spark"</font>
  
  * R-JVM bridge
  
    Older versions use rJava to call Java/Scala code. Now has its own implementation. Refer to the paper.
       
  * Scala code spawns Rscript processes.
  
    <font color='red'>Currently, Rscript process is launched and terminated for each operation. But it should be optimized via something like DAG.</font> 
    
    Scala communicates with worker process via stdin/stdout, using custom protocol.[^how_communicate]
    
    Serializes data via R serialization, simple binary serialization of integers, strings, raw bytes.[^serialize]

  [Link to examples](./sparkr_examples.md) 

---

[^R-JVM_overhead]: Advanced Analytics with Spark p24.
[^SparkR_low_level_api_slow]: [Reading Text file in SparkR 1.4.0](http://stackoverflow.com/questions/31157649/reading-text-file-in-sparkr-1-4-0)
[^how_communicate]: [A Friendly Critique of SparkR](http://www.labs.hpe.com/research/systems-research/R-workshop/Sannella-talk7.pdf) p8
[^serialize]: [A Friendly Critique of SparkR](http://www.labs.hpe.com/research/systems-research/R-workshop/Sannella-talk7.pdf) p8
