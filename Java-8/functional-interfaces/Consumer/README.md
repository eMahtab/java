# Consumer

!["Consumer interface"](../images/Consumer/consumer-interface.png?raw=true)

## 1. java.lang.Iterable interface forEach() takes a Consumer

!["forEach Consumer"](../images/Consumer/forEach-consumer.png?raw=true)

```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

        // Using Consumer to print each name
        names.forEach(name -> System.out.print(name + " "));
    }
}
```

## 1a. Updating records using a Consumer

```java
import java.util.function.Consumer;
import java.util.ArrayList;
import java.util.List;

class User {
    String name;
    boolean isActive;

    User(String name, boolean isActive) {
        this.name = name;
        this.isActive = isActive;
    }
    @Override
    public String toString() {
        return name + " - " + (isActive ? "Active" : "Inactive");
    }
}

public class Main {
    public static void main(String[] args) {
        List<User> users = new ArrayList<>();
        users.add(new User("Alice", false));
        users.add(new User("Bob", true));

        // Consumer to activate a user
        Consumer<User> activateUser = user -> user.isActive = true;

        // Activate all inactive users
        users.stream().forEach(user -> {
            if (!user.isActive) {
                activateUser.accept(user);
            }
        });

        users.stream().forEach(System.out::println);
    }
}
```
