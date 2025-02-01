# BiConsumer

!["BiConsumer interface"](../images/BiConsumer/biconsumer-interface.png?raw=true)

## 1. Iterating Over a Map

!["Map forEach BiConsumer"](../images/BiConsumer/map-forEach-biconsumer.png?raw=true)

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

## 1a. BiConsumer
```java
import java.util.Arrays;
import java.util.List;
import java.util.function.BiConsumer;

public class Main {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
        List<Integer> ages = Arrays.asList(25, 30, 35);

        BiConsumer<String, Integer> printNameAndAge = (name, age) -> {
            System.out.println(name + " is " + age + " years old.");
        };

        for (int i = 0; i < names.size(); i++) {
            printNameAndAge.accept(names.get(i), ages.get(i));
        }
    }
}
```
