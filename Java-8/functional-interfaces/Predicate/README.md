# Predicate

!["Predicate interface"](../images/Predicate/predicate-interface.png?raw=true)

## 1. Stream interface filter method takes a Predicate

!["Stream.filter takes a Predicate"](../images/Predicate/stream-filter-predicate.png?raw=true)

```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Predicate;
import java.util.stream.Collectors;

class Employee {
    String name;
    double salary;
    String department;

    Employee(String name, double salary, String department) {
        this.name = name;
        this.salary = salary;
        this.department = department;
    }

    public String toString() {
        return name + " (" + department + ") - $" + salary;
    }
}

public class Main {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee("John", 50000, "IT"),
            new Employee("Jane", 60000, "HR"),
            new Employee("Doe", 75000, "IT"),
            new Employee("Alice", 45000, "Finance")
        );

        // Predicate to filter IT department employees
        Predicate<Employee> itDepartment = e -> e.department.equals("IT");

        // Filter and print IT employees
        List<Employee> itEmployees = employees.stream()
                                              .filter(itDepartment)
                                              .collect(Collectors.toList());
        itEmployees.forEach(System.out::println);
    }
}
```

## 2. Combining Predicates

```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Predicate;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        // Predicate to check if a number is even
        Predicate<Integer> isEven = n -> n % 2 == 0;

        // Predicate to check if a number is greater than 5
        Predicate<Integer> isGreaterThan5 = n -> n > 5;

        // Combine predicates: even numbers greater than 5
        Predicate<Integer> combined = isEven.and(isGreaterThan5);

        // Filter and print numbers
        List<Integer> result = numbers.stream()
                                      .filter(combined)
                                      .collect(Collectors.toList());
        System.out.println(result); // Output: [6, 8, 10]
    }
}
```
