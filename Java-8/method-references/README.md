# Method References

Method references in Java provide a way to refer to methods without invoking them explicitly. 

They are a shorthand notation for lambda expressions and improve code readability. 

Method references use :: operator and come in different types.



## Reference to an Instance Method (of an arbitrary object of a particular type)

```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

        // Using Lambda
        // names.forEach(name -> System.out.println(name));

        // Using Method References
        names.forEach(System.out::println);
        names.stream().map(String::length).forEach(System.out::println);
    }
}
```







# References :

https://docs.oracle.com/javase/tutorial/java/javaOO/methodreferences.html
