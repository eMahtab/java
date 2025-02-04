# JDK 14

## Made switch expressions a standard feature

The switch expression was a preview feature in Java 12 and Java 13; with JDK 14 it is officially JDK standard feature.

It means from Java 14 and onward, we can return value via switch expressions without specifying the --enable-preview option.


## Introduced record (aka Data classes) in Preview

A new class called record (aka data class), it is a final class, not abstract, and all of its fields are final as well. 

The record will automatically generate the tedious constructors, public get, equals(), hashCode(), toString() **during compile time.**

**No setter methods, all fields are final.**

```java
record Data(int i, String s, double score) {
}

public class Main {
   public static void main(String[] args) {
      Data d1 = new Data(1, "One", 1.34d);
      Data d2 = new Data(2, "Two", 2.54d);
      Data d3 = new Data(1, "One", 1.34d);
      System.out.println(d1.hashCode() + ":" + d3.hashCode());
      System.out.println(d1.equals(d3));
      System.out.println(d2.i() + d2.s() + d2.score()); //2Two2.54
   }
}
```
