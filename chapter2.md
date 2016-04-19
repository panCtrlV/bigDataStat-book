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
- Reconfigurable computing with FPGA
- Vector processors 
- 

## Multicore Computing

## Cluster Computing

## GPU Computing

## Grid Computing