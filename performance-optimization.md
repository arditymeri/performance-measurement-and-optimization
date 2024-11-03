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
---



---
transition: fade-out
level: 2
---

# Java Microbenchmark Harness JMH 
A tool for accurate performance measurement in Java

<div grid="~ cols-2 gap-40">

<div>


Purpose: 
* Measure performance for (small) code snippets

Why using JMH
* consider JVM optimizations when benchmarking 
* warmup effects
* reliable, reproducible performance results
</div>

<div>

![Java Microbenchmark Harness](./media/PerformanceTracking-JMH.drawio.png){class="mx-auto block" style="width: 45%"}


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

# Loops vs Streams Performance (ms/op)

<!-- Chart Container -->
<div class="chart-container">
  <div v-for="(size, index) in collectionSizes" :key="index" class="bar-group">
    <div class="bars">
      <!-- Loop Bar -->
      <div class="bar bar-loop" :style="{ height: `${loopTimes[index] * 0.5}px` }"> <!-- Scaled down by 0.5 -->
        <span class="bar-label">{{ loopTimes[index] }} </span>
      </div>
      <!-- Stream Bar -->
      <div class="bar bar-stream" :style="{ height: `${streamTimes[index] * 0.5}px` }"> <!-- Scaled down by 0.5 -->
        <span class="bar-label">{{ streamTimes[index] }} </span>
      </div>
    </div>
    <!-- Collection Size Label -->
    <div class="size-label">{{ size }}k</div>
  </div>
</div>

<!-- Legend -->
<div class="legend">
  <div class="legend-item">
    <div class="legend-color bar-loop"></div>
    <span>Loops</span>
  </div>
  <div class="legend-item">
    <div class="legend-color bar-stream"></div>
    <span>Streams</span>
  </div>
</div>

<script setup>
const collectionSizes = [100, 250, 350, 500, 750, 1000];
const loopTimes = [42, 108, 149, 223, 342, 478]; // Adjust these values as needed
const streamTimes = [48, 130, 169, 248, 391, 509]; // Adjust these values as needed
</script>


<style>
.legend {
  display: flex;
  gap: 15px;
  justify-content: center;
  margin-top: 15px;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 5px;
}

.legend-color {
  width: 15px;
  height: 15px;
}

.bar-loop, .legend-color.bar-loop {
  background-color: #6baed6;
}

.bar-stream, .legend-color.bar-stream {
  background-color: #fd8d3c;
}

/* Existing styles for the chart */
.chart-container {
  display: flex;
  gap: 20px;
  align-items: flex-end;
  justify-content: center;
  height: 300px;
}

.bar-group {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.bars {
  display: flex;
  gap: 5px;
  align-items: flex-end;
}

.bar {
  width: 20px;
  position: relative;
}

.bar-label {
  position: absolute;
  bottom: -15px;
  font-size: 10px;
  text-align: center;
  width: 100%;
}

.size-label {
  margin-top: 20px;
  font-size: 12px;
  font-weight: bold;
  text-align: center;
}
</style>

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
src: ./pages/profiling-out-of-memory.md
---

---
transition: fade-out
level: 2
src: ./pages/profiling-virtual-threads.md
---


---
transition: fade-out
level: 1
---

# Performance Tracking in Distributed Environments 

<br>

![Performance monitoring with Grafana](./media/PerformanceTracking-GrafanaAndPrometheusMonitoring.drawio.png){class="mx-auto block" style="width: 55%"}

---
transition: fade-out
level: 2
---

# JMeter 

---
transition: fade-out
level: 2
---

# Prometheus 

---
transition: fade-out
level: 2
---

# Graphana 


---
transition: fade-out
layout: center
level: 1
---

# Nature of the problems 

---
transition: fade-out
level: 2
---

# Algorithmic Optimization Problems 

Improve efficiency of algorithms 

Profiling 


<div class="grid grid-cols-10 place-items-center gap-4">

  <div> 

  ![YourKit](./media/logos/yourkit_logo.svg){class="mx-auto block"}

  </div>

  <div> 

  ![JProfiler](./media/logos/Codework-Inc-jprofile.png){class="mx-auto block"}

  </div>

  <div> 
  
  ![VisualVM](./media/logos/visualvm_logo_big.png){class="mx-auto block"}
  
  </div>

  <div>

  ![JDK Mission Control](./media/logos/JDK_Mission_Control_(logo).png){class="mx-auto block" style="width: 70%"}
  
  </div>


</div>



Benchmarking 


---
transition: fade-out
level: 2
---

# Data-intensive problems 

* Split the work into multiple machines 
* Combine the result 


![Hadoop](./media/PerformanceTracking-HadoopMapReduce.drawio.png){class="mx-auto block" style="width: 70%"}

---
transition: fade-out
level: 2
---

# Combinatorial/Exponential Search Problems  

Complexity Theory: NP-Hard or NP-Complete classes

* Easy to guess and check 
* Enormous search space 

Examples: 
- Routing problems 
- Graph partitioning 
- ...

Applications: 
- Logistics 
- Cryptography 
- Blockchain and cryptocurrency 
- ...


---
transition: fade-out
level: 1
---

# Blockchain

![Performance monitoring with Grafana](./media/PerformanceTracking-Blockchain-Node.drawio.png){class="mx-auto block" style="width: 100%"}


---
transition: fade-out
level: 1
---

# Blockchain Decentralized

![Performance monitoring with Grafana](./media/PerformanceTracking-Blockchain-Network-Full.drawio.png){class="mx-auto block" style="width: 90%"}


---
transition: fade-out
level: 1
---

# Quantum computing - Fundamentals 


- Superposition 
- Entanglement 
- Coherence 
- Interference 


---
transition: fade-out
level: 1
---

# Quantum computing - Applications

- Quantum simulation 
- Cryptography 
- Chemistry 
- Material and drug production 
- Machine learning
- ... 


---
transition: fade-out
level: 1
---

# Quantum computing - where are we


---
transition: fade-out
level: 1
---

# Take Away  
- Know your tools: sometimes they help optimizing performance 
- Identify the pain-points first. Then try to eliminate them 
- In distributed systems this is easier said then done 
- Complex problems - practically infinite time complexity 
- Looking forward to Quantum 



---
layout: center
class: text-center
---

# Resources

[Documentation](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/resources/showcases)

# Thank you 

<PoweredBySlidev mt-10 />
