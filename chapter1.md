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
    
      Rapid access to the totality of the data.[^rapid_access_data]
      
      Keep a large data set close. This is important for interactive data analysis.
      
      Centrality of data makes it easy to perform large analytical stud‐ ies, like population genetics, large-scale QC analyses, and so on.[^central_data]
      
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

- Other Considerations
  * Data storage format    
    + Supported data types (e.g. int, double string, array, record)
    + File format (e.g. columnar[^columnar_file_format])
  * Data model
    
    <font color='red'>TODO: What are the difference and relationship between these two? -- It (Parquet) is largely based on the underlying data storage format used in Google’s Dremel system (see “Dremel: Interactive Analysis of Web-scale Datasets” Proc. VLDB, 2010, by Melnik et al.), and has a data model that is compatible with Avro, Thrift, and Protocol Buffers.</font>


[^maprfs]: https://en.wikipedia.org/wiki/MapR#MapR_Converged_Data_Platform
[^rapid_access_data]: Advanced Analytics with Spark p203.
[^central_data]: Advanced Analytics with Spark p203.
[^columnar_file_format]: It means that values for a particular column from many records are stored contiguously on disk. See Figure 10-2 on p205 of Advanced Analytics with Spark.