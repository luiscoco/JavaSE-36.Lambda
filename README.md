# JavaSE-Lambda and Functional Interfaces

In Java, lambda expressions and functional interfaces are part of the functional programming features introduced in Java 8.

## 1. Lambda Expressions
Lambda expressions provide a concise way to express instances of single-method interfaces (functional interfaces). They allow you to treat functionality as a method argument or create a concise way to represent instances of single-method interfaces.

Here's the basic syntax of a lambda expression:

```java
(parameters) -> expression
```
or

```java
(parameters) -> { statements; }
```

Let's look at an example:

```java
// Traditional approach with an anonymous class
Runnable traditionalRunnable = new Runnable() {
    @Override
    public void run() {
        System.out.println("Hello, World!");
    }
};

// Lambda expression
Runnable lambdaRunnable = () -> System.out.println("Hello, World!");
```

In this example, Runnable is a functional interface with a single method (run()). The lambda expression provides a more concise way to represent the implementation of that method.

## 2. Functional Interfaces
Functional interfaces are interfaces that have exactly one abstract method. They can have multiple default or static methods, but only one abstract method. Java provides a variety of built-in functional interfaces in the java.util.function package, such as Predicate, Function, Consumer, etc.

Here's an example using a functional interface:

```java
// Functional interface with a single abstract method
@FunctionalInterface
interface MyFunction {
    int apply(int x, int y);
}

public class LambdaExample {
    public static void main(String[] args) {
        // Using a lambda expression to implement the abstract method
        MyFunction addFunction = (a, b) -> a + b;
        
        // Using the functional interface
        System.out.println(addFunction.apply(2, 3));  // Output: 5
    }
}
```

## 3. More advance concepts about lambda expressions

Let's delve into some more advanced concepts related to lambda expressions and functional interfaces in Java.

### 3.1. Method References:

Method references provide a shorthand notation to refer to methods by their names. 

They are a syntactic sugar for lambda expressions. There are several types of method references:

#### Static Method Reference:

```java
// Lambda expression
Function<String, Integer> parseIntLambda = s -> Integer.parseInt(s);

// Static method reference
Function<String, Integer> parseIntReference = Integer::parseInt;
```

#### Instance Method Reference on a Particular Instance:

```java
// Lambda expression
BiFunction<String, String, Boolean> startsWithLambda = (s1, s2) -> s1.startsWith(s2);

// Instance method reference
BiFunction<String, String, Boolean> startsWithReference = String::startsWith;
```

#### Instance Method Reference on an Arbitrary Instance:

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

// Lambda expression
names.forEach(name -> System.out.println(name));

// Instance method reference on an arbitrary instance
names.forEach(System.out::println);
```

### 3.2. Default Methods in Functional Interfaces:

Java 8 introduced the concept of default methods in interfaces, allowing the addition of new methods to interfaces without breaking existing implementations. 

Functional interfaces can have default methods.

```java
@FunctionalInterface
interface MyFunction {
    int apply(int x, int y);

    default void printResult(int result) {
        System.out.println("Result: " + result);
    }
}

public class LambdaExample {
    public static void main(String[] args) {
        MyFunction addFunction = (a, b) -> a + b;
        int result = addFunction.apply(2, 3);
        addFunction.printResult(result);
    }
}
```

### 3.3. Predicate, Function, and Consumer Interfaces:

Java provides several functional interfaces in the java.util.function package. Here are three commonly used ones:

#### Predicate: Represents a predicate (boolean-valued function) of one argument.

```java
Predicate<String> isLong = s -> s.length() > 5;
```

#### Function: Represents a function that accepts one argument and produces a result.

```java
Function<Integer, String> intToString = Object::toString;
```

#### Consumer: Represents an operation that accepts a single input argument and returns no result.

```java
Consumer<String> printUpperCase = s -> System.out.println(s.toUpperCase());
```

### 3.4. Streams and Collectors:

Lambda expressions are commonly used in conjunction with the Streams API for processing sequences of elements. 

The map, filter, and reduce operations are often used with lambda expressions.

```java
List<String> words = Arrays.asList("Java", "is", "fun");

// Using streams and lambda expressions
List<String> uppercasedWords = words.stream()
                                   .map(String::toUpperCase)
                                   .collect(Collectors.toList());
```

### 3.5. Functional Programming Patterns:

Lambda expressions enable the use of functional programming patterns, such as map-reduce and filter-map-reduce, in Java. 

These patterns can lead to more concise and expressive code.

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

// Using functional programming patterns
int sum = numbers.stream()
                 .filter(n -> n % 2 == 0)
                 .mapToInt(Integer::intValue)
                 .sum();
```

These advanced features make Java's functional programming capabilities more powerful and expressive, allowing developers to write clean and concise code.

In this example, MyFunction is a functional interface with a single abstract method (apply). 

The lambda expression is used to provide the implementation of that method.

Lambda expressions and functional interfaces together make it easier to write concise and expressive code, especially when working with APIs that rely on functional programming concepts.
