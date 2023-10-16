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

In this example, MyFunction is a functional interface with a single abstract method (apply). The lambda expression is used to provide the implementation of that method.

Lambda expressions and functional interfaces together make it easier to write concise and expressive code, especially when working with APIs that rely on functional programming concepts.



