# JDK 10 (Feature Release)

In JDK 10, you can declare local variables **(only local variables)** with non-null initializers with the var identifier, which can help you write code that’s easier to read.

## Local Variable Type Inference

var is a reserved type name, not a keyword

```java
var list = new ArrayList<String>();    // infers ArrayList<String>
var stream = list.stream();            // infers Stream<String>
var path = Paths.get(fileName);        // infers Path
var bytes = Files.readAllBytes(path);  // infers bytes[]
```




# References :

https://docs.oracle.com/en/java/javase/17/language/local-variable-type-inference.html

https://openjdk.org/projects/amber/guides/lvti-style-guide
