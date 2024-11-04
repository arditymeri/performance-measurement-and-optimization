# JVM Architecture

<br/>
<br/>

![Java Microbenchmark Harness](./../media/PerformanceTracking-JVM.drawio.png){class="mx-auto block" style="width: 85%"}

<!-- 

The bytecode is loaded by the classloaders into memory
Then the interpreter operations from the bytecode one by one, compiles and executes them

However, there is also a JIT compiler that keeps an eye on hot spots - parts of the code that are executed more frequently and tries to optimize them automatically. 

It would compiles the hot code to avoid  interpreting it in the future
Additionally, it may perform optimizations like loop unfolding, method inlining, etc... 

 -->