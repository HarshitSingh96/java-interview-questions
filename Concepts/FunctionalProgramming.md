# Functional programming in Java

Functional programming is a style of programming that treats computation as evaluation of mathematical functions.

FP in java:

1. First class functions
In FP, functions are First class citizens which means that we can pass functions as a argument to other functions, return a function from another functions and assign a function to a variable. Java allows this through lamba functions, functional interfaces, etc.


2. Immutability
Functional programming encourages immutability, once an object is created it cannot be modified. Immutability can be achived by making class members as final and private, setting the values through constructor and not exposing the setter methods.
If there is any class member, assign a deep copy of that object and not directly the reference.

3. Pure functions
Pure functions are functions that does not have a side effect. If we give the same input, we should get the same output.

4. Higher Order functions
functions that takes another function as argument or return other function are called HOF.
Java supports this through functional interfaces like Function, Predicate and Consumer

```java
Function<Integer, Integer> square = x -> x*x;
System.out.print(square.apply(4));
```

5. Streams
Streams allows you to do multiple operations on a collection of objects like List, Set in a declarative manner without writing loops

```java
List<String> names = Arrays.asList("Harshit", "Karan", "Arjun");
names.stream.filter(name -> name.startsWith('H'))
.map(String::toUpperCase)
.forEach(System.out::println);
```

6. lambda Expression
Lambda expression is a shorthand way to write anonymous functions.

7. Functional Interfaces
Functional interfaces are interface that has exactly one abstract method. Eg. Runnable, Callable, Function, Predicate.

8. Optional
Optional is a container that may or may not contain a value. used to avoid NPE and to handle the absence of a value gracefully. 

```java
Optional<String> name = Optional.of("Harshit");
name.ifPresent(System.out::println);
```


### Benefits of FP in java
- Immutability: Avoid unintented side effects
- Consiseness: lambda expression and streams api
- Parallel processing: with streams, we can process data in parallel
- Better abstraction : HOF allows more abstract and reusable code
- Cleaner code : With use of streams, we don't need loops