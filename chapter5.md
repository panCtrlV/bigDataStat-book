# Chapter 5 Parallel Computing in R with Packages

`parallel` package (TODO: fork processes instead of instantiate threads?) provides two interfaces, one like the `multicoare` package and one like the `snow` package. 

Call compiled function written with Rcpp, OpenMP. Parallelism with OpenMP using threads. But thread safety is a big concern (TODO: how? [this post](https://wrathematics.github.io/RparallelGuide/#r-and-thread-safety) explains why but I couldn't understand.)

Example:

  [Parallelization in rcpp via OpenMP](https://www.google.co.jp/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0ahUKEwjRq4WS2P7LAhXMsYMKHWx5BqMQFggjMAE&url=https%3A%2F%2Fwbnicholson.wordpress.com%2F2014%2F07%2F10%2Fparallelization-in-rcpp-via-openmp%2F&usg=AFQjCNHX3wbwoZbtZXN7mjwSIuceiCFFwQ)

GPU computing. [Rth](https://github.com/Rth-org/Rth) is a package of functions written in Thrust, callable from R. It thus provides to R programmers a set of parallel applications that run on both GPUs and multicore systems.

[Rmpi](https://bioinfomagician.wordpress.com/2013/11/25/mpi-tutorial-for-r-rmpi/) but OpenMPI is for distributed memory cluster computing?

