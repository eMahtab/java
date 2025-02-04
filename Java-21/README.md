# JDK 21

## Virtual Threads

Virtual threads, first introduced in Java 19 as a preview are made standard feature starting from Java 21.


### Why Use Virtual Threads?

Use virtual threads in high-throughput concurrent applications, especially those that consist of a great number of concurrent tasks that spend much of their time waiting. Server applications are examples of high-throughput applications because they typically handle many client requests that perform blocking I/O operations such as fetching resources.

**Virtual threads are not faster threads; they do not run code any faster than platform threads. They exist to provide scale (higher throughput), not speed (lower latency).**

```java
import java.time.Duration;
import java.time.Instant;
import java.util.concurrent.*;

public class Main {
    private static final int TASK_COUNT = 10_000; // Number of tasks to execute
    private static final int PLATFORM_THREAD_POOL_SIZE = 100; // Fixed thread pool size

    public static void main(String[] args) {
        System.out.println("Starting performance comparison...\n");

        // Measure Virtual Threads Execution Time
        measureExecutionTime("Virtual Threads", () -> {
            try (ExecutorService virtualExecutor = Executors.newVirtualThreadPerTaskExecutor()) {
                submitTasks(virtualExecutor);
            }
        });

        // Measure Platform Threads Execution Time
        measureExecutionTime("Platform Threads (Fixed Pool)", () -> {
            try (ExecutorService platformExecutor = Executors.newFixedThreadPool(PLATFORM_THREAD_POOL_SIZE)) {
                submitTasks(platformExecutor);
            }
        });
    }

    /**
     * Submits TASK_COUNT tasks to the given executor.
     */
    private static void submitTasks(ExecutorService executor) {
        CountDownLatch latch = new CountDownLatch(TASK_COUNT);
        for (int i = 0; i < TASK_COUNT; i++) {
            executor.submit(() -> {
                performTask();
                latch.countDown();
            });
        }
        try {
            latch.await(); // Ensure all tasks complete before proceeding
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }

    /**
     * Simulates a lightweight task.
     */
    private static void performTask() {
        try {
            Thread.sleep(10); // Simulating some work
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }

    /**
     * Measures and prints the execution time of a given task.
     */
    private static void measureExecutionTime(String testName, Runnable task) {
        Instant start = Instant.now();
        task.run();
        Instant end = Instant.now();
        System.out.printf("%s execution time: %d ms%n", testName, Duration.between(start, end).toMillis());
    }
}
```


# References 

https://docs.oracle.com/en/java/javase/21/core/virtual-threads.html#GUID-DC4306FC-D6C1-4BCC-AECE-48C32C1A8DAA



