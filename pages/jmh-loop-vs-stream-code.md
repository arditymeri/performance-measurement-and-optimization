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
