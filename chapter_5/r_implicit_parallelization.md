# Implicit Parallelization

---

Uses threads and shared memory (ideally via OpenMP) <font color='red'>TODO: similar idea to SupR?</font>
  
  + the user specifies a maximal number of threads to use
  + R decides internally when to use more than one thread, if allowed
  + available in an experimental package `pnmath`[^pnmath_archive]

  * requires no explicit user action once enabled <font color='red'>(just call the compiled function in R?)</font>

- Rcpp and inline

  + Rcpp is a C++ library facilitates the integration of R and C++
  + `inline` package provides functionality to dynamically define R functions and S4 methods with in-lined C, C++ and Fortran.

- OpenMP
  + It is a shared memory model.
  + It is a Lightweight approach. 
  + Workload is distributed between threads. 
  + Supported by many compilers: GNU, Intel, IBM, NAG and PGI. 

  R has interfaces for calling compiled C/C++, Fortran codes. 

  + Call compiled function written with Rcpp, OpenMP. Parallelism with OpenMP using threads. But thread safety is a big concern (TODO: how? [this post](https://wrathematics.github.io/RparallelGuide/#r-and-thread-safety) explains why but I couldn't understand.)

    OpenMP in R Examples:

      * [Parallelization in rcpp via OpenMP](https://wbnicholson.wordpress.com/2014/07/10/parallelization-in-rcpp-via-openmp/)
      * [OPENMP TUTORIAL, WITH R INTERFACE](https://matloff.wordpress.com/2015/01/16/openmp-tutorial-with-r-interface/)

- OpenMPI