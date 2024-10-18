# Measuring execution time

```java
public long sumUsingForLoop(List<Integer>numbers) {
    long sum = 0;

    long startTime = System.nanoTime();
    for (int number : numbers) {
        sum += number;
    }
    long endTime = System.nanoTime();

    double duration = (endTime - startTime)/1000000d;
    System.out.println("Execution time: " + duration + " milliseconds");
    return sum;
}
```

<!-- 
1. Find a code example 
2. Measure with milliseconds  
  2.1. Measure with nanoseconds instead 
3. What is the problem? 
4. Use JMH 
-->