# Multicore Computing

---

Multi-core CPUs are very common these days. This is true even for laptop's CUPs. Intel Core i5 is duel-core and Intel Core i7 is usaually quad-core. Intel has a proprietary simultaneous multithreading (SMT) technology called Hyper-threading Technology (HTT). It improves parallelization of computations performed on x86 microprocessors. With HTT, one physical core appears as two processors to the operating system, allowing concurrent scheduling of two processes per core.[^TODO1]

[^TODO1]: See https://en.wikipedia.org/wiki/Hyper-threading, need to be rephrased] 

The wide adoption of multi-core architectures makes it possible to parallelize data analysis on our personal computers. Parallel computing libraries such as OpenMP can be used to develop statistical packages for parallel computing on personal computers.

## Computer Architecture

- Multiple processors which share one global memory(RAM) 
- Bus interconnect 
- Threaded programs 
- Communication via shared variables
- [Symmetric multiprocessing (SMPs)](https://en.wikipedia.org/wiki/Symmetric_multiprocessing) are Commonplace because of multicore CPUs. 

![SMP Diagram](./figures/smp_diagram.png)

## OpenMP

[The most popular way to program on multicore machines is to use OpenMP, a C/C++ (and FORTRAN) callable system that runs on Linux, Mac and Windows.  (For Macs, you need the OpenMP-enabled version of Mac’s clang compiler.)](https://matloff.wordpress.com/2015/01/16/openmp-tutorial-with-r-interface/)