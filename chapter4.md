# Chapter 4 R for Statistical Analysis

---

- Some features of R language

  * Dynamic typing (<font color='red'>== type inference?</font>)
  * Lexical scoping
  * Object oriented (everything is an object)
  * <font color='red'>Functional programming?</font>
    + Pattern 1: pass a function as an argument to another function, e.g. apply, lapply

- Limitations of R

  * Inability to scale (due to single threaded computing paradigm and poor memory management)
  * R is a [memory bound](https://en.wikipedia.org/wiki/Memory_bound_function) language 

    >It spends almost all of its time reading and writing vector intermediates to memory”.[^R_is_memory_bound]

---

[^R_is_memory_bound]: Quoted from [Advanced R Performance](http://adv-r.had.co.nz/Performance.html).