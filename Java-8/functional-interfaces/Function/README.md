# Function 

!["Function interface"](../images/Function/function-interface.png?raw=true)

## 1. Using Function for Data Validation and Transformation

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

## 2. Using Function for Dynamic Behavior in APIs

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

## 3. Stream interface map method takes a Function

!["Map's mapper function"](../images/Function/mapper-function.png?raw=true)

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

## 4. Functional Composition

Function supports composition using andThen and compose methods, allowing you to chain multiple functions together.

```java
import java.util.function.Function;

public class Main {
    public static void main(String[] args) {
        Function<Integer, Integer> multiplyByTwo = x -> x * 2;
        Function<Integer, Integer> addThree = x -> x + 3;

        // Using andThen: multiply by 2, then add 3
        Function<Integer, Integer> multiplyAndAdd = multiplyByTwo.andThen(addThree);
        int result1 = multiplyAndAdd.apply(5);
        System.out.println("andThen result: " + result1); // Output: 13

        // Using compose: add 3, then multiply by 2
        Function<Integer, Integer> addAndMultiply = multiplyByTwo.compose(addThree);
        int result2 = addAndMultiply.apply(5);
        System.out.println("compose result: " + result2); // Output: 16
    }
}
```
