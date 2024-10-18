---
theme: seriph
background: https://cover.sli.dev
title: Performance tracking and optimization
info: |
class: text-center
drawings: 
    persist: false 
transition: slide-left
mdc: true
overviewSnapshots: true
---

# Performance tracking and optimization

From JVM to distributed systems 

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    <carbon:arrow-right class="inline"/>
  </span>
</div>

---
transition: slide-up
layout: center
---

# About me

Ardit Ymeri 

<!-- Find some pictures of me: 

  - summer pictures 
  - cycling pictures 
  - swimming pictures 
  - guitar picture 


 -->

<!-- 

- I work as consultant on insurance companies on behalf of Open Value. 

- I moved from albania to austria in 2013 because I wanted to study Logic and Computer Science 
at Vienna University of Technology. That's the reason I'm here now. 

- It's funny how you put enormous efforts on studying Logic and all theorems about computability theory 
only to end up working as a software developer in a financial institution .... because that's where the money is. 

I hope my boss doesn't hear that :D 

The reason why i'm saying this is I will mention a few tools today. I'm not working for any of them nor trying to promote any of them. 

In the past tho, I did spend some years working on Java refactoring tools.
And because of that, i had to dig deeper in the Java features and understand the language and its tools closely. 

-->

---
transition: fade-out
layout: two-cols
layoutClass: gap-16
---

# Table of contents 

You can use the `Toc` component to generate a table of contents for your slides:

```html
<Toc minDepth="1" maxDepth="1"></Toc>
```

The title will be inferred from your slide content, or you can override it with `title` and `level` in your frontmatter.

<Toc minDepth="1" maxDepth="2"></Toc>

::right::

# Contents

On this talk:

<Toc minDepth="1" maxDepth="2"></Toc>


---
transition: fade-out
layout: image-right
image: https://cover.sli.dev
---

# On this talk

JVM: 
- Optimizations from `javac` compiler 
- Optimizations from the JIT Compiler 
- GraalVM vs OpenJDK
- JMH 
- Profilers 
- Data leak example 
- Project loom
- Virtual threads example 

- Other JVM languages? 

Distributed platforms
- How to track performance in distributed platforms
- JMetric 
- Working with big data: Splitting the work to multiple machines

Blockchain 
- 

Big data 
- Map reduce 


Problem classifications 
- Some problems are hard: Exponential time, polynomial space
- Quantum computing to the rescue?


---
transition: slide-left
layout: center
level: 1
---

# Java Optimization

---
transition: fade-out
src: ./pages/string-literals.md
level: 2
---


---
transition: fade-out
layout: two-cols
layoutClass: gap-16
src: ./pages/string-concatenation-invokedynamic.md
level: 2
---


---
transition: fade-out
src: ./pages/measure-execution-time.md
level: 2

---


---
transition: fade-out
src: ./pages/jvm-architecture.md
level: 2
layout: center
class: text-center
---



---
transition: fade-out
level: 2
---

# Java Microbenchmark Harness JMH 
A Tool for Accurate Performance Measurement in Java

<div grid="~ cols-2 gap-60">

<div>


Purpose: 
* Measure performance for (small) code snippets

Why Use JMH
* consider JVM optimizations when benchmarking 
* warmup effects
* reliable, reproducible performance results
</div>

<div>

```mermaid {scale: 0.5}
flowchart TD
  A([Start Benchmarking]) --> B[Fork New JVM Instance]
  B --> C[Warm-Up Phase]
  C ---|"JIT Optimizations"| D[JIT Optimized Code]
  D --> E[Measurement Phase]
  E --> F[Result Aggregation]
  F --> G([End Benchmarking])
```

</div>
</div>

---
transition: fade-out
level: 2
---

# JMH Examples - Loops vs Streams

```java
import org.openjdk.jmh.annotations.*;

@State(Scope.Thread)
public class SumBenchmark {

    private List<Integer> numbers;

    @Setup(Level.Trial)
    public void setup() {
        numbers = IntStream.range(1, 1_000_000).boxed().toList();
    }

    @Benchmark
    @BenchmarkMode(Mode.AverageTime)
    @OutputTimeUnit(TimeUnit.MILLISECONDS)
    public int sumUsingForLoop() {
        int sum = 0;
        for (int num : numbers) 
          sum += num;
        return sum;
    }
}

```

---
transition: fade-out
level: 2
---

# JMH Examples - Lambda vs Method Reference

```java
@Benchmark
@BenchmarkMode(Mode.AverageTime)
@OutputTimeUnit(TimeUnit.MILLISECONDS)
public List<String> convertToUppercaseUsingLambda() {
    return strings.stream()
            .map(s -> s.toUpperCase())
            .collect(Collectors.toList());
}

@Benchmark
@BenchmarkMode(Mode.AverageTime)
@OutputTimeUnit(TimeUnit.MILLISECONDS)
public List<String> convertToUppercaseUsingMethodReference() {
    return strings.stream()
            .map(String::toUpperCase)
            .collect(Collectors.toList());
}

```

---
transition: fade-out
level: 2
---

# JMH Diagrams 

Put some diagrams after running benchmarks

Diagram here

---
transition: fade-out
level: 2
---

# Profiling 
Analyze runtime behavior of an application

Why use profilers
* identify bottlenecks in the code 
* understand memory allocation and GC patterns
* gain insights into thread synchronization issues 

Popular profilers
* VisualVM
* YourKit
* JProfiler 
* Perf



---
transition: fade-out
level: 2
---

# Example - Profiling


---
transition: fade-out
level: 2
---

# Example - Project loom

---
transition: fade-out
level: 2
src: ./pages/graalvm.md
hide: false
---


---
transition: fade-out
level: 2
---

# Other JVM Languages


---
layout: center
class: text-center
---

# Resources

[Documentation](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/resources/showcases)


---
layout: center
class: text-center
---

# Thank you 

<PoweredBySlidev mt-10 />
