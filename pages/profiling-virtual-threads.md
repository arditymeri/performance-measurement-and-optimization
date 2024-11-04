# Profiling - Platform vs Virtual Threads 

Platform threads:

```java
public void runPlatformThreads(int taskCount) {
    ExecutorService executor = Executors.newFixedThreadPool(100);
    for (int i = 0; i < taskCount; i++) {
        executor.submit(this::doWork);
    }
    executor.shutdown();
    while (!executor.isTerminated()) {} // wait
}

```

Virtual threads:

```java

public void runVirtualThreads(int taskCount) {
    ExecutorService executor = Executors.newVirtualThreadPerTaskExecutor();
    for (int i = 0; i < taskCount; i++) {
        executor.submit(this::doWork);
    }
    executor.shutdown();
    while (!executor.isTerminated()) {} // wait
}

```

<!--  -->