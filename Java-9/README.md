# JDK 9 (Feature Release)

Along with many other changes Java 9 introduced, methods in Collection to create Immutable List, Set and Map.


## Creating Immutable List, Set, Map

```java
import java.util.List;
import java.util.Set;
import java.util.Map;

public class Main {
        public static void main(String[] args) {
                List<String> immutableList = List.of("banana", "apple", "cherry");
                // java.lang.UnsupportedOperationException
                // Collections.sort(immutableList);

                // java.lang.UnsupportedOperationException
                // immutableList.add("orange");

                Set<String> immutableSet = Set.of("Xian", "Beijing", "Shenzhen", "Shanghai");
                // java.lang.UnsupportedOperationException
                // immutableSet.remove("Xian");
                Map<String, Integer> immutableMap = Map.of("Xian", 1, "Beijing", 2, "Shenzhen", 3, "Shanghai", 4);
                // java.lang.UnsupportedOperationException
                // immutableMap.remove("Shanghai");
        }
}
```








# References 

https://docs.oracle.com/javase/9/whatsnew/toc.htm#JSNEW-GUID-BA9D8AF6-E706-4327-8909-F6747B8F35C5

