# JDK 12

## switch expressions (Preview)
JDk 12 introduced **switch expressions** which introduces a more concise and expressive way to use switch statements.


```java
public class Main {
    public static void main(String[] args) {
        String day = "MONDAY";

        String typeOfDay = switch (day) {
            case "SATURDAY", "SUNDAY" -> "Weekend";
            case "MONDAY", "TUESDAY", "WEDNESDAY", "THURSDAY", "FRIDAY" -> "Weekday";
            default -> throw new IllegalArgumentException("Invalid day: " + day);
        };
         
        System.out.println("The day is a: " + typeOfDay);
    }
}
```

Comparing to the traditional if-else approach, using switch expressions results in more concise code.

```java
public class Main {
    public static void main(String[] args) {
        String day = "MONDAY";
        String typeOfDay;

        if (day.equals("SATURDAY") || day.equals("SUNDAY")) {
            typeOfDay = "Weekend";
        } else if (day.equals("MONDAY") || day.equals("TUESDAY") || 
                   day.equals("WEDNESDAY") || day.equals("THURSDAY") || day.equals("FRIDAY")) {
            typeOfDay = "Weekday";
        } else {
            throw new IllegalArgumentException("Invalid day: " + day);
        }

        System.out.println("The day is a: " + typeOfDay);
    }
}
```
