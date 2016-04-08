# Chapter 5 Parallel Computing in R with Packages

`parallel` package (TODO: fork processes instead of instantiate threads?) provides two interfaces, one like the `multicoare` package and one like the `snow` package. 

Call compiled function written with Rcpp, OpenMP. Parallelism with OpenMP using threads. But thread safety is a big concern (TODO: how?)

Example:

  [Parallelization in rcpp via OpenMP](https://www.google.co.jp/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0ahUKEwjRq4WS2P7LAhXMsYMKHWx5BqMQFggjMAE&url=https%3A%2F%2Fwbnicholson.wordpress.com%2F2014%2F07%2F10%2Fparallelization-in-rcpp-via-openmp%2F&usg=AFQjCNHX3wbwoZbtZXN7mjwSIuceiCFFwQ)


