# Chapter 5 Parallel Computing in R

---

**Note** The classification of explicit and implicit parallelization is given in [this slides](http://www.labs.hpe.com/research/systems-research/R-workshop/luke-talk1.pdf). The difference between these two types of parallelization is similar to that between multi-processing and multi-threading. They can be combined.

- Explicit paralellization

- Implicit paralellization

- Combined approach

- Limitations

  * The "load data at master -> send to workers -> collect at master -> send to worker->repeat" workflow is not suitable for interactive data analysis and iterative algorithms.

  ![](./figures/cost_of_data_movement.jpg) 

**Note** [Figure source](http://www.labs.hpe.com/research/systems-research/R-workshop/Indrajit-talk5.pdf) with adaptation.

---

[^R_hpc_packages]: The CRAN page of [High-Performance and Parallel Computing with R](https://cran.r-project.org/web/views/HighPerformanceComputing.html) contains such a list of packages.
[^pnmath_archive]: Download the package from [here](http://homepage.stat.uiowa.edu/~luke/R/experimental/). This is the [demo](https://www.olcf.ornl.gov/wp-content/uploads/2011/07/Lecture3.pdf).

---

- pbdR

- GPU computing. [Rth](https://github.com/Rth-org/Rth) is a package of functions written in Thrust, callable from R. It thus provides to R programmers a set of parallel applications that run on both GPUs and multicore systems.