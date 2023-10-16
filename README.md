# JavaSE-MethodReferences

In Java, method references provide a shorthand notation for lambda expressions. 

They allow you to refer to methods or constructors without actually invoking them. 

Method references are often more concise and readable than equivalent lambda expressions.

There are four main types of method references in Java:

1. Static Method Reference

2. Instance Method Reference of a Particular Object

3. Instance Method Reference of an Arbitrary Object of a Particular Type

4. Constructor Method Reference

## 1. Static Method Reference:

Syntax: ClassName::staticMethodName

```java

// Lambda expression
Function<String, Integer> parseInt = s -> Integer.parseInt(s);

// Method reference
Function<String, Integer> parseIntRef = Integer::parseInt;
```

## 2. Instance Method Reference of a Particular Object:

Syntax: instance::instanceMethodName

```java
// Lambda expression
BiPredicate<String, String> startsWith = (s1, s2) -> s1.startsWith(s2);

// Method reference
BiPredicate<String, String> startsWithRef = String::startsWith;
```

## 3. Instance Method Reference of an Arbitrary Object of a Particular Type:

Syntax: ClassName::instanceMethodName

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

// Lambda expression
names.forEach(s -> System.out.println(s));

// Method reference
names.forEach(System.out::println);
```

## 4. Constructor Method Reference:

Syntax: ClassName::new

```java
// Lambda expression
Supplier<List<String>> listSupplier = () -> new ArrayList<>();

// Method reference
Supplier<List<String>> listSupplierRef = ArrayList::new;
```

These examples demonstrate how method references can simplify code, making it more concise and readable.

They are especially useful when the lambda expression only calls an existing method or constructor.

I hope these examples help clarify method references in Java for you! If you have any specific questions or if there's anything you'd like me to elaborate on, feel free to ask.

## More samples

Let's dive into more examples to deepen your understanding of method references.

## 1. Static Method Reference:

```java
// Lambda expression
Function<String, Integer> lengthLambda = s -> s.length();

// Method reference
Function<String, Integer> lengthRef = String::length;
```

## 2. Instance Method Reference of a Particular Object:

```java
class StringHelper {
    public boolean isUpperCase(String s) {
        return s.equals(s.toUpperCase());
    }
}

StringHelper helper = new StringHelper();

// Lambda expression
Predicate<String> isUpperCaseLambda = s -> helper.isUpperCase(s);

// Method reference
Predicate<String> isUpperCaseRef = helper::isUpperCase;
```

## 3. Instance Method Reference of an Arbitrary Object of a Particular Type:

```java
// Lambda expression
List<String> words = Arrays.asList("apple", "banana", "orange");
words.forEach(s -> System.out.println(s.toUpperCase()));

// Method reference
words.forEach(String::toUpperCase);
```

## 4. Constructor Method Reference:

```java
// Lambda expression
Supplier<List<String>> listSupplierLambda = () -> new ArrayList<>();

// Method reference
Supplier<List<String>> listSupplierRef = ArrayList::new;
```

## 5. Reference to an Instance Method of a Particular Object's Type:

```java
List<String> fruits = Arrays.asList("apple", "banana", "orange");

// Lambda expression
fruits.sort((s1, s2) -> s1.compareToIgnoreCase(s2));

// Method reference
fruits.sort(String::compareToIgnoreCase);
```

## 6. Reference to an Arbitrary Type Instance Method:

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

// Lambda expression
Function<Integer, Double> sqrtLambda = n -> Math.sqrt(n);

// Method reference
Function<Integer, Double> sqrtRef = Math::sqrt;
```

These examples cover a range of scenarios where method references can be applied, from working with strings and lists to dealing with custom classes and mathematical operations.

If you have any specific questions about a particular example or if you'd like more examples in a specific context, feel free to let me know!

# More advance topics about "method references" in Java

Let's explore some more advanced aspects of method references in Java:

## 1. Method References with Generics:
You can use method references with generic methods. Here's an example:

```java
class Utils {
    public static <T> T identityFunction(T t) {
        return t;
    }
}

// Lambda expression with a generic method
Function<String, String> identityLambda = s -> Utils.identityFunction(s);

// Method reference with a generic method
Function<String, String> identityRef = Utils::<String>identityFunction;
```

## 2. Method References and Overloaded Methods:
If a class has multiple overloaded methods with the same name, you can specify which method to reference based on the functional interface's method signature. Here's an example:

```java
class OverloadedMethods {
    public static void print(String s) {
        System.out.println("String: " + s);
    }

    public static void print(int i) {
        System.out.println("Integer: " + i);
    }
}

// Lambda expression choosing the correct method
Consumer<String> printStringLambda = s -> OverloadedMethods.print(s);

// Method reference specifying the method with String parameter
Consumer<String> printStringRef = OverloadedMethods::print;
```

## 3. Constructor References with Generics:
Constructor references can also be used with generic classes. Here's an example:

```java
class Box<T> {
    private T value;

    public Box(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }
}

// Lambda expression with a generic constructor
Function<String, Box<String>> boxConstructorLambda = s -> new Box<>(s);

// Constructor reference with a generic constructor
Function<String, Box<String>> boxConstructorRef = Box::new;
```

## 4. Method References in Streams:
Method references are often used in Java streams to make code more concise. Here's an example:

```java
List<String> words = Arrays.asList("apple", "banana", "orange");

// Lambda expression with a stream
words.stream().map(s -> s.toUpperCase()).forEach(System.out::println);

// Method reference in a stream
words.stream().map(String::toUpperCase).forEach(System.out::println);
```

## 5. Bound and Unbound Method References:
A bound method reference is when you reference a method on an instance, and an unbound method reference is when you reference a static method. Here's an example:

```java
class Example {
    public static void staticMethod() {
        System.out.println("Static method");
    }

    public void instanceMethod() {
        System.out.println("Instance method");
    }
}

// Unbound method reference
Runnable staticMethodRef = Example::staticMethod;

// Bound method reference
Example instance = new Example();
Runnable instanceMethodRef = instance::instanceMethod;
```

These advanced topics showcase the flexibility and versatility of method references in various scenarios. If you have specific questions about any of these examples or if you'd like more details on a particular topic, feel free to ask!
