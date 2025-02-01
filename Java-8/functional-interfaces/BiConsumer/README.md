# BiConsumer

!["BiConsumer interface"](../images/BiConsumer/biconsumer-interface.png?raw=true)

## 1. Iterating Over a Map

A common use case for BiConsumer is iterating over the entries of a Map. The forEach method of Map takes a BiConsumer as an argument, where the two inputs are the key and value of each entry.

```java
import java.util.HashMap;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        Map<String, Integer> map = new HashMap<>();
        map.put("Apple", 10);
        map.put("Banana", 5);
        map.put("Orange", 8);

        // Using BiConsumer to print key-value pairs
        map.forEach((key, value) -> System.out.println(key + " -> " + value));
    }
}
```
