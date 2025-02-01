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

# Some more examples :

```java
// Before Java 8
Runnable r1 = new Runnable() {
    @Override
    public void run() {
        System.out.println("Hello World!");
    }
};

// With Lambda Expression
Runnable r2 = () -> System.out.println("Hello World!");
```

```java
// Before Java 8
Comparator<String> c1 = new Comparator<String>() {
    @Override
    public int compare(String s1, String s2) {
        return s1.compareTo(s2);
    }
};

// With Lambda Expression
Comparator<String> c2 = (s1, s2) -> s1.compareTo(s2);
```

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void execute();
}

// Using Lambda Expression
MyFunctionalInterface mfi = () -> System.out.println("Executing...");
mfi.execute();
```
