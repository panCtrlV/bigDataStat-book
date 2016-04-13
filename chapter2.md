# Chapter 2 Computing Infrastructures for Big Data Statistics
---

- Motivation

  * Clock speed saturates at 3 to 4 GHz. 
  * Computational intensive models (e.g. iterative)
  * Large datasets
  
  **So, the future is parallel.**
  
   ![35 Year CPU Trend](./figures/35years_cpu_trend.png)
  
  **Note** The explanation and raw data for this figure can be found on [Karl Rupp's webpage](https://www.karlrupp.net/2015/06/40-years-of-microprocessor-trend-data/).
  
- Multicore computing (shared memory)
  * Computer architecture
  * Multithreading
    + Most programs running on multicore systems are threaded.
    + A key point is that the threads share memory, making it easy for them to cooperate. 
    + Writing threaded code directly is messy, so higher-level systems have been developed to hide the messy details from the programmer, thus making his/her life far easier. <font color='red'>TODO:How?</font>
  * Multiprocessing
  * Shared memory parallel computing
    + OpenMP
    + Intel’s Threading Building Blocks (TBB) system

- Cluster computing (distributed memory)
  * Cluster architecture
  * Distributed (memory) computing
  * Distributed data storage
  * Cloud computing
    + Cloud architecture (virtualization)

- GPU computing

## 1. Parallel Computing on Multicore Computers

Multi-core CPUs are very common these days. This is true even for laptop's CUPs. Intel Core i5 is duel-core and Intel Core i7 is usaually quad-core. Intel has a proprietary simultaneous multithreading (SMT) technology called Hyper-threading Technology (HTT). It improves parallelization of computations performed on x86 microprocessors. With HTT, one physical core appears as two processors to the operating system, allowing concurrent scheduling of two processes per core.[^TODO1]

[^TODO1]: Copied from https://en.wikipedia.org/wiki/Hyper-threading, need to be rephrased] 

The wide adoption of multi-core architectures makes it possible to parallelize data analysis on our personal computers. Parallel computing libraries such as OpenMP can be used to develop statistical packages for parallel computing on personal computers. 

# OpenMP

[The most popular way to program on multicore machines is to use OpenMP, a C/C++ (and FORTRAN) callable system that runs on Linux, Mac and Windows.  (For Macs, you need the OpenMP-enabled version of Mac’s clang compiler.)](https://matloff.wordpress.com/2015/01/16/openmp-tutorial-with-r-interface/)