# BiFunction

!["BiFunction interface"](../images/BiFunction/bifunction-interface.png?raw=true)

## 1. Mathematical Operations

We can use BiFunction to perform mathematical operations like addition, subtraction, multiplication, or division.

```java
import java.util.function.BiFunction;

public class Main {
    public static void main(String[] args) {
        // Define a BiFunction for addition
        BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;

        int result = add.apply(5, 3); // Result: 8
        System.out.println("Addition: " + result);

        // Define a BiFunction for multiplication
        BiFunction<Integer, Integer, Integer> multiply = (a, b) -> a * b;

        result = multiply.apply(4, 6); // Result: 24
        System.out.println("Multiplication: " + result);
    }
}
```

