# Method References

Method references in Java provide a way to refer to methods without invoking them explicitly. 

They are a shorthand notation for lambda expressions and improve code readability. 

Method references use :: operator and come in different types.



## Reference to an Instance Method (of an arbitrary object of a particular type)

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> cities = Arrays.asList("Shanghai", "Xian", "Beijing", "Shenzhen");

        // Using Lambda
        // cities.forEach(city -> System.out.println(city));

        // Using Method References
        cities.forEach(System.out::println);
        cities.stream().map(String::length).forEach(System.out::println);
        cities.stream().sorted(String::compareToIgnoreCase).forEach(System.out::println);
        List<String> lowerCased = cities.stream().map(String::toLowerCase).collect(Collectors.toList());
    }
}
```







# References :

https://docs.oracle.com/javase/tutorial/java/javaOO/methodreferences.html
