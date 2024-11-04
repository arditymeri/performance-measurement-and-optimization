# Measuring execution time

<br/>

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

What are the problems:
- one time measurement - inaccurate. Not reliable 
- doesnt take into account JVM optimizations and warm ups

-->