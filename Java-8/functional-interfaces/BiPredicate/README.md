# BiPredicate

!["BiPredicate interface"](../images/BiPredicate/bipredicate-interface.png?raw=true)

## 1. Filtering Entries in a Map
You can use BiPredicate to filter entries in a Map based on both the key and value.

```java
import java.util.HashMap;
import java.util.Map;
import java.util.function.BiPredicate;

public class Main {
    public static void main(String[] args) {
        Map<String, Integer> map = new HashMap<>();
        map.put("apple", 10);
        map.put("banana", 20);
        map.put("cherry", 30);

        BiPredicate<String, Integer> biPredicate = (key, value) -> key.startsWith("a") && value > 5;

        map.entrySet().stream()
           .filter(entry -> biPredicate.test(entry.getKey(), entry.getValue()))
           .forEach(entry -> System.out.println(entry.getKey() + " => " + entry.getValue()));
    }
}
```
