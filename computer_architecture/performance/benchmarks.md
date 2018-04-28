# Benchmarks

#####Performance best determined by running a real application
* Use programs typical of expected workload
* Or, typical of expected class of applications. e.g., compilers/editors,
scientific applications, graphics, etc.
#####Small benchmarks
* Nice for architects and designers
* Easy to standardize
* Can be abused

* CPI is not always the best way to compare the performance,
especially when processors use different instruction sets.
* In such cases synthetic benchmarks are preferred (CoreMark,
Dhrystone).
* It should be noted that different benchmarks consider different
levels of performance. Thus, some benchmarks measure only CPU performance without
cache performance, and some do system evaluation.

All these details need to be taken into account for fair comparison.

Also, the reported performance of some benchmarks can be
sensitive to processor frequency (e.g. performance per MHz)