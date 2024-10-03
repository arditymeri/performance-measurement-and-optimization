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
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

---
transition: slide-up
---

# About me

Ardit Ymeri 




---
transition: fade-up
layout: two-cols
layoutClass: gap-16
---

# Table of contents 

You can use the `Toc` component to generate a table of contents for your slides:

```html
<Toc minDepth="1" maxDepth="1"></Toc>
```

The title will be inferred from your slide content, or you can override it with `title` and `level` in your frontmatter.

<Toc minDepth="1" maxDepth="1"></Toc>

::right::

# Contents

On this talk:

<Toc v-click minDepth="1" maxDepth="2"></Toc>

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

<arrow v-click="[4, 5]" x1="350" y1="310" x2="195" y2="334" color="#953" width="2" arrowSize="1" />

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
