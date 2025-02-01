# Consumer

!["Consumer interface"](../images/Consumer/consumer-interface.png?raw=true)

## 1. java.lang.Iterable interface forEach() takes a Consumer

!["forEach Consumer"](../images/Consumer/forEach-consumer.png?raw=true)

```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

        // Using Consumer to print each name
        names.forEach(name -> System.out.print(name + " "));
    }
}
```