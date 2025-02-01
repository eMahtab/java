# UnaryOperator

**UnaryOperator is a specialization of Function interface**, for the case where the operand and result are of the same type.

!["UnaryOperator interface"](../images/UnaryOperator/unary-operator.png?raw=true)

## 1. List.replaceAll(UnaryOperator<E> operator) method applies a UnaryOperator to all elements in the list.

!["UnaryOperator interface"](../images/UnaryOperator/list-replaceAll.png?raw=true)

```java
import java.util.List;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
        names.replaceAll(name -> name.toUpperCase());
        System.out.println(names);
    }
}
```



