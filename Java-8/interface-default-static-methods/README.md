# interface default and static methods 

## Default methods helps add new functionality without breaking existing code

Default methods allow library designers to add new functionality to interfaces without forcing existing users to update their code.

## Key Points to Remember:

- Default methods are not abstract; they have a body.

- They are public by default and cannot be private or protected.

- They are inherited by sub-interfaces and implementing classes.

e.g. Comparator interface has been enhanced with default methods, Iterable interface (which is extended by Collection interface) has been enhanced with default forEach method.

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
