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
level: 2
---

# 


---
transition: fade-out
layout: image-right
image: https://cover.sli.dev
---

# What is Slidev? 

Content here 

- Slidev is cool 
- Let's give it  a try 
- Let's see how code looks like in here



<!-- This allow you to embed external code blocks -->
<<< @/snippets/external.ts#snippet

<!-- Footer -->

[Learn more](https://sli.dev/features/line-highlighting)

<!-- Inline style -->
<style>
.footnotes-sep {
  @apply mt-5 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

<!--
Notes can also sync with clicks

[click] This will be highlighted after the first click

[click] Highlighted with `count = ref(0)`

[click:3] Last click (skip two clicks)
-->

---
transition: fade-out
layout: center
level: 2
---

# JVM


Let's bring in some code

Java is beautiful 

Other languages too 

---
transition: slide-up
level: 2
---

# JMH 

Java Microbenchmark Harness 

Profiling is used to find performance hot spots and bottlenecks 

- JProfiler 
- Eclipse MAT

You only got one shot


---
transition: slide-up
level: 2
---

# Profiling 

Java Microbenchmark Harness 

Profiling is used to find performance hot spots and bottlenecks 

- JProfiler 
- Eclipse MAT


---
src: ./pages/graalvm.md
hide: false
---


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
