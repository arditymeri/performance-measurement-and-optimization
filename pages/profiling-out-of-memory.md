# Profiling example - Memory Leak

```java

void simulateMemoryLeak() throws OutOfMemoryError {
    List<Object> items = new ArrayList<>(1);
    int i = 0;
    while (true) {
        items.add(new Object());
        pause(i);
        i++;
    }
}

```