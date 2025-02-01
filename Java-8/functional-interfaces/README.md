# Functional Interfaces

**Functional interfaces provide target types for lambda expressions and method references.** 

Each functional interface has a single abstract method, called the functional method for that functional interface, to which the lambda expression's parameter and return types are matched or adapted.

Functional interfaces are introduced in Java 8.

# Java 8 Functional Interfaces

Java 8 introduced several functional interfaces in the `java.util.function` package. Below is a table summarizing these interfaces along with their descriptions and common use cases.

| Functional Interface | Description | Use Case |
|---------------------|-------------|----------|
| **Function<T, R>** | Represents a function that accepts one argument and produces a result (`apply(T t)`). | Used for transformation (e.g., converting a `String` to `Integer`). |
| **BiFunction<T, U, R>** | Represents a function that accepts two arguments and produces a result (`apply(T, U)`). | Used for operations requiring two inputs, like combining data. |
| **Predicate<T>** | Represents a boolean-valued function of one argument. It contains a `test(T t)` method. | Used for filtering data (e.g., in Streams and Collections). |
| **BiPredicate<T, U>** | Represents a boolean-valued function that takes two arguments (`test(T, U)`). | Used for filtering and comparisons involving two parameters. |
| **Consumer<T>** | Represents an operation that accepts a single argument and returns no result (`accept(T t)`). | Used for performing actions like logging or printing data. |
| **BiConsumer<T, U>** | Represents an operation that takes two arguments and returns no result (`accept(T, U)`). | Used for actions like updating two values or logging two inputs. |
| **Supplier<T>** | Represents a function that provides a result of type `T` (`get()`). | Used for lazy initialization and object supply. |
| **UnaryOperator<T>** | A specialized `Function<T, T>` that operates on a single operand of type `T`. | Used for transformations where input and output types are the same. |
| **BinaryOperator<T>** | A specialized `BiFunction<T, T, T>` that operates on two operands of type `T`. | Used for operations like addition, multiplication, and string concatenation. |



## Examples:

### Using Function for Data Validation and Transformation

We can use Function to validate and transform input data, such as converting user input into a specific format.

```java
import java.util.function.Function;

public class Main {
    public static void main(String[] args) {
        // Function to validate and format a phone number
        Function<String, String> formatPhoneNumber = phone -> {
            if (phone == null || !phone.matches("\\d{10}")) {
                throw new IllegalArgumentException("Invalid phone number");
            }
            return "+1" + phone; // Add country code
        };

        String userInput = "1234567890";
        String formattedNumber = formatPhoneNumber.apply(userInput);
        System.out.println(formattedNumber); // Output: +11234567890
    }
}
```

### Using Function for Dynamic Behavior in APIs

APIs can use Function to allow users to pass custom logic for processing data.

```java
import java.util.function.Function;

public class Main {
    public static void main(String[] args) {
        // API method that accepts a Function for custom processing
        String result = processInput("hello", input -> input.toUpperCase() + "!");
        System.out.println(result); // Output: HELLO!
    }

    public static String processInput(String input, Function<String, String> processor) {
        return processor.apply(input);
    }
}
```

## Stream interface map method takes a Function

!["Map's mapper function"](images/mapper-function.png?raw=true)

```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Function;

public class Main {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        // Function to square a number
        Function<Integer, Integer> square = x -> x * x;

        numbers.stream()
                .map(square)
                .forEach(num -> System.out.print(num   + " ")); // Output: 1 4 9 16 25 
    }
}
```
