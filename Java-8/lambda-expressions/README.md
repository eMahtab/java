# Lambda Expressions

Java 8 introduced lambda expressions, which are a significant feature enabling functional programming in Java. 

Lambda expressions **provide a clear and concise way to represent instances of functional interfaces** (interfaces with a single abstract method) using an expression. They help in writing more readable and maintainable code

## Step 1 : Old way without Lambda Expression

```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Consumer;

class PrintElement implements Consumer<String> {
    @Override
    public void accept(String element) {
        System.out.print(element + " ");
    }
}

public class Main {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("a", "b", "c");
        list.forEach(new PrintElement());
    }
}
```

## Step 1a : Using Anonymous Class but without Lambda Expression

```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Consumer;

public class Main {

    public static void main(String[] args) {
        Consumer<String> consumer = new Consumer<String>() {
            @Override
            public void accept(String element) {
                System.out.print(element + " ");
            }
        };
        List<String> list = Arrays.asList("a", "b", "c");
        list.forEach(consumer);
    }
}
```

## Step 2 : Using Lambda Expression
```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("a", "b", "c");
        list.forEach((element) -> System.out.print(element + " "));
    }
}
```
