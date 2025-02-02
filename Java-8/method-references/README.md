# Method References

Method references in Java provide a way to refer to methods without invoking them explicitly. 

They are a shorthand notation for lambda expressions and improve code readability. 

Method references use :: operator and come in different types.

# Kinds of Method References 

| **Kind** | **Syntax** | **Examples** |
|----------|-----------|-------------|
| **Reference to a static method** | `ContainingClass::staticMethodName` | `Person::compareByAge`<br>`MethodReferencesExamples::appendStrings` |
| **Reference to an instance method of an arbitrary object of a particular type** | `ContainingType::methodName` | `String::compareToIgnoreCase`<br>`String::concat` |
| **Reference to an instance method of a particular object** | `containingObject::instanceMethodName` | `myComparisonProvider::compareByName`<br>`myApp::appendStrings2` |
| **Reference to a constructor** | `ClassName::new` | `HashSet::new` |


## 1. Reference to a Static Method

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

## 2. Reference to an Instance Method (of an arbitrary object of a particular type)

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


# 3. Reference to an Instance Method (of a particular object)

```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public void printMessage(String message) {
        System.out.println("Message: " + message);
    }

    public static void main(String[] args) {
        Main instance = new Main();
        List<String> messages = Arrays.asList("Hello", "World", "Java 8");

        // Using method reference to call printMessage on each element
        messages.forEach(instance::printMessage);
    }
}
```

```java
import java.util.function.Predicate;

public class Main {
    public boolean isLongerThanFive(String str) {
        return str.length() > 5;
    }

    public static void main(String[] args) {
        Main obj = new Main();
        Predicate<String> predicate = obj::isLongerThanFive;

        System.out.println(predicate.test("Hello")); // false
        System.out.println(predicate.test("MethodReference")); // true
    }
}
```

# 4. Reference to a Constructor

```java
import java.util.List;
import java.util.stream.Collectors;

class Employee {
    String name;
    int age;
    Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

class EmployeeDTO {
    String name;
    EmployeeDTO(Employee emp) {
        this.name = emp.name;
    }
    public String toString() {
        return "EmployeeDTO{name='" + name + "'}";
    }
}

public class Main {
    public static void main(String[] args) {
        List<Employee> employees = List.of(
            new Employee("Alice", 30),
            new Employee("Bob", 25)
        );

        // Using constructor reference instead of emp -> new EmployeeDTO(emp)
        List<EmployeeDTO> employeeDTOs = employees.stream()
                .map(EmployeeDTO::new)
                .collect(Collectors.toList());

        System.out.println(employeeDTOs);
        // Output: [EmployeeDTO{name='Alice'}, EmployeeDTO{name='Bob'}]
    }
}
```




# References :

https://docs.oracle.com/javase/tutorial/java/javaOO/methodreferences.html
