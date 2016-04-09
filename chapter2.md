# Chapter 2 Computing Systems and Platforms for Big Data Statistics
---

- Parallel computing on a multicore personal computer
  * Computer architecture
  * Multithreading and multiprocessing
  * Shared memory parallel computing
    + OpenMP
- Cluster computing
  * Cluster architecture
  * Distributed (memory) computing
  * Distributed data storage
- Cloud computing
  * Cloud architecture (virtualization)

## 1. Parallel Computing on Personal Computer

Multi-core CPUs are very common these days. This is true even for laptop's CUPs. Intel Core i5 is duel-core and Intel Core i7 is usaually quad-core. Intel has a proprietary simultaneous multithreading (SMT) technology called Hyper-threading Technology (HTT). It improves parallelization of computations performed on x86 microprocessors. With HTT, one physical core appears as two processors to the operating system, allowing concurrent scheduling of two processes per core.[^TODO1]

[^TODO1]: Copied from https://en.wikipedia.org/wiki/Hyper-threading, need to be rephrased] 

The wide adoption of multi-core architectures makes it possible to parallelize data analysis on our personal computers. Parallel computing libraries such as OpenMP can be used to develop statistical packages for parallel computing on personal computers. 

# OpenMP

[The most popular way to program on multicore machines is to use OpenMP, a C/C++ (and FORTRAN) callable system that runs on Linux, Mac and Windows.  (For Macs, you need the OpenMP-enabled version of Mac’s clang compiler.)](https://matloff.wordpress.com/2015/01/16/openmp-tutorial-with-r-interface/)