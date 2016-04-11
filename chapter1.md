# Chapter 1 Big Data, Statistics and Computing

- What is big data and the importance of big data.
- What we believe about statistical analysis on big data.
  * Exploratory data analysis
  * Modeling
  * Estimation
  * Inference
- Statistical analysis requires a suitable programming environment
- Big data brings new challenges to the computing environment
  * Distributed file systems
    + Why using a distributed file system?
    
      Archiving the raw data using a distributed FS such as Hadoop ensures that the data stays relatively warm (compared with, say, tape archive).[^warmdata]
      
      Keep a large data set close. This is important for interactive data analysis.
      
    + Desired properties for a distributed FS
    + Hadoop HDFS
    + MapR FS 
      
      MapR FS implements the HDFS API with a native C distributed read-write file system[^maprfs]
      
  * Parallel and distributed computing models
    + Hadoop YARN/MRv2
    + Spark in-memory computing
  * Suitable programming language
    + R
    + Scala
    + Python


[^maprfs]: https://en.wikipedia.org/wiki/MapR#MapR_Converged_Data_Platform
[^warmdata]: Advanced Analytics with Spark p203