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
