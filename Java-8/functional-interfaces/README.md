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

[Function](https://github.com/eMahtab/java/tree/main/Java-8/functional-interfaces/Function)  

[Consumer](https://github.com/eMahtab/java/tree/main/Java-8/functional-interfaces/Consumer)

[BiFunction](https://github.com/eMahtab/java/tree/main/Java-8/functional-interfaces/BiFunction)

[Predicate](https://github.com/eMahtab/java/tree/main/Java-8/functional-interfaces/Predicate)

