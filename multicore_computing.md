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
- SMPs are Commonplace because of multicore CPUs. 
