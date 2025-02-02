# Method References

Method references in Java provide a way to refer to methods without invoking them explicitly. 

They are a shorthand notation for lambda expressions and improve code readability. 

Method references use :: operator and come in different types.

## Reference to a Static Method

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> cities = Arrays.asList("Shanghai", "Xian", "Beijing", "Shenzhen");

        // Using a static method reference for printing
        cities.forEach(Main::printCity);

        // Using a static method reference for transformation
        List<Integer> cityNameLengths = cities.stream().map(Main::getLength)
                .collect(Collectors.toList());

        // Using a built-in static method reference (Integer::parseInt)
        List<String> numbersAsStrings = Arrays.asList("10", "20", "30", "40");
        List<Integer> numbers = numbersAsStrings.stream()
                .map(Integer::parseInt) // Static method reference
                .collect(Collectors.toList());

        // Using a static method reference for sorting
        cities.stream().sorted(Main::compareCities)
                .forEach(Main::printCity);
    }

    // Static method to print a city
    public static void printCity(String city) {
        System.out.println(city);
    }

    // Static method to get the length of a string
    public static int getLength(String str) {
        return str.length();
    }

    // Static method to compare two cities
    public static int compareCities(String city1, String city2) {
        return city1.compareToIgnoreCase(city2);
    }
}
```

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
