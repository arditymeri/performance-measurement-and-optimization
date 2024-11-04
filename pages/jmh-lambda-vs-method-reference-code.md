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


<!--  

Open IntelliJ to view the code. Mention: 

- State and setup annotation 
- The benchmark annotation 
- Benchmark mode 
- Output Unit 


 -->