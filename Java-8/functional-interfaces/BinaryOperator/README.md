# BinaryOperator

**This is a specialization of BiFunction** for the case where the operands and the result are all of the same type.

!["BinaryOperator interface"](../images/BinaryOperator/binaryoperator-interface.png?raw=true)


### 1. Reduction Operations in Streams e.g. 
```
Optional<T> reduce(BinaryOperator<T> accumulator)

T reduce(T identity,
         BinaryOperator<T> accumulator)
```
BinaryOperator is often used in reduction operations with streams, such as summing a list of integers:

```java
import java.util.Arrays;
import java.util.List;
import java.util.function.BinaryOperator;

public class Main {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        BinaryOperator<Integer> sum = (a, b) -> a + b;
        int total = numbers.stream().reduce(0, sum); // Result: 15
        System.out.println("Total Sum: " + total);
    }
}
```

