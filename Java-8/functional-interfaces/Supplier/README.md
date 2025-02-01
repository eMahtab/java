# Supplier

!["Supplier interface"](../images/Supplier/supplier-interface.png?raw=true)

## 1. CompletableFuture.supplyAsync(Supplier)

```java
import java.util.concurrent.CompletableFuture;

public class Main {
    public static void main(String[] args) {
        CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> "Task 1");
        CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> "Task 2");
        CompletableFuture<String> future3 = CompletableFuture.supplyAsync(() -> "Task 3");

        CompletableFuture<Void> allFutures = CompletableFuture.allOf(future1, future2, future3);

        allFutures.thenRun(() -> {
            try {
                System.out.println(future1.get());
                System.out.println(future2.get());
                System.out.println(future3.get());
            } catch (Exception e) {
                e.printStackTrace();
            }
        });
        try {
            Thread.sleep(5000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("main method finished executing");
    }
}
```
