# interface default and static methods 

## Default methods helps add new functionality without breaking existing code

Default methods allow library designers to add new functionality to interfaces without forcing existing users to update their code.

## Key Points to Remember:

- Default methods are not abstract; they have a body.

- They are public by default and cannot be private or protected.

- They are inherited by sub-interfaces and implementing classes.

e.g. Iterable interface (which is extended by Collection interface) has been enhanced with default forEach() method. Collection interface has been enhanced with default stream() and parallelStream()methods.

```java
public interface Iterable<T>{
    default void forEach(Consumer<? super T> action) {
        Objects.requireNonNull(action);
        for (T t : this) {
            action.accept(t);
        }
    }

   ...
}
```

```java
public interface Collection<E> extends Iterable<E> {
    default Stream<E> stream() {
        return StreamSupport.stream(spliterator(), false);
    }

    default Stream<E> parallelStream() {
        return StreamSupport.stream(spliterator(), true);
    }

    ...
}    
```

## static methods

Before Java 8, utility methods related to an interface were often placed in separate utility classes (e.g., Collections for the Collection interface).

Static methods in interfaces allow you to define utility methods directly within the interface, making the code more organized and intuitive.


```java
Optional.empty()
Optional.of()
Optional.ofNullable()

```

Below are some of the static methods introduced in JDK 9 in collection interfaces

```java
List.of()
Set.of()
Map.of()
```