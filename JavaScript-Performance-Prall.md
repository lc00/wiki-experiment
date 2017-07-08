## Reasons For JS Performance Issues

* Performance issues are non-linear. Big-O notation determines whether something scales:
    * Constant
    * Linear
    * Loglinear
    * Quadratic
    * Factorial
* CPU profiler = which functions are called, how often
* Don’t pre-optimize, you won’t know where your issues will be
* Don’t pass two types to one variable in a signature
    * No “type polymorphism”
    * Can’t be cached or optimized
* Don’t change existing objects, it ruins optimization
* Interpreted code runs on a VM, but can be cached
* Garbage collection
    * All context is retained from closures!
    * Profile memory to look for issues
