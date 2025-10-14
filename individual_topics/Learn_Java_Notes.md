# Learn Java

## Why is the Java platform independent? 
Because Java code is compiled into bytecode, and this bytecode is executed in the Java Virtual Machine (JVM).

## How does bytecode get generated?
Java compiler converts `.java` file to `.class` or bytecode.

## Components of JVM and Explanation
JVM consists of five main components:

### 1. Class Loader Subsystem
- **Loading:** Classloader is classified into three types:
  1. Bootstrap ClassLoader  
  2. Extension ClassLoader  
  3. Application ClassLoader
- **Linking:**
  1. Prepare  
  2. Verify  
  3. Initialize
- **Initialization**

### 2. Runtime Data Area (Memory Area)
1. Method area  
2. Heap area  
3. Stack area  
4. PC register  
5. Native method stack

### 3. Execution Engine
1. Interpreter – Executes bytecode instructions line by line  
2. JIT Compiler – Just-In-Time compiler for optimized performance  
3. Garbage Collector

### 4. Native Method Interface  
### 5. Native Method Libraries

---

## What is a Class?
A class is a blueprint or template that holds variables and methods. Class variables or methods can be accessed only using object instantiation, and memory for non-static variables is allocated when an object is created. Static variables belong to the class itself and are allocated memory when the class is loaded by the JVM.

---

## What is an Object?
An object is an instance of a class used to access its members.

---

## Parent Class in java.lang Package
The parent class of all classes in Java is the **Object** class, defined in the `java.lang` package.

### Common Methods of Object Class
- toString()
- equals(Object obj)
- hashCode()
- getClass()
- clone()
- finalize()
- wait(), notify(), notifyAll()

---

## Constructor Chaining
You can call one constructor from another using `this()`. It must be the first statement in the constructor.

---
## Inheritance in Java

Definition:
Inheritance in Java enables a class to inherit properties and actions from another class, called a superclass (parent class).
A class derived from a superclass is called a subclass (child class).

⸻

## Terms Used in Inheritance

A class is a group of objects that share common properties. It serves as a blueprint or template for creating objects.

A subclass, also known as a derived class, extended class, or child class, inherits features from another class.

The superclass, also called a base class or parent class, is the class from which the subclass inherits its features.

Reusability allows the use of the fields and methods of an existing class in a new class. This practice helps avoid code duplication and promotes cleaner, modular design.
---
## Polymorphism
- The word ‘polymorphism’ means ‘having many forms’. Polymorphism are Two Types:
    1.Method OverLoading
    2.Method Overriding  
## Overriding vs Overloading

### Overriding
- Happens in inheritance when a subclass redefines a parent class method  
- Based on runtime polymorphism  
- Uses `@Override` annotation  
- Cannot reduce access modifier or throw broader checked exceptions

### Overloading
- Happens in the same class  
- Based on compile-time polymorphism  
- Same method name, different parameters  
- No restriction on access modifier or exceptions

---

## Super Keyword
Used to call a parent class constructor or method from a subclass. It must appear as the first statement in a constructor.

---

## IS-A vs HAS-A Relationship

- **IS-A:** Inheritance (Child class extends Parent class)  
- **HAS-A:** Composition (Object reference used in another class)

---

## instanceof Operator
Used to test if an object is an instance of a specific class or subclass.

Example:
```java
class Animal {}
class Dog extends Animal {}

Animal a = new Dog();
System.out.println(a instanceof Animal);  // true
System.out.println(a instanceof Dog);     // true
System.out.println(a instanceof Object);  // true
```

---

## Why Can't a Class be Protected?
A class can be either **public** or **package-private** only.

---

## Access Modifiers for Variables
- **private:** within the same class  
- **public:** accessible everywhere  
- **protected:** same package + subclasses  
- **default:** within the same package

---

## Abstract Class in Java

An abstract class contains both abstract and concrete methods. It cannot be instantiated and can have constructors and variables.

### Why Abstract Class When Interface Exists?
Abstract classes provide **partial implementation**, shared **state (variables)**, and **constructors**, whereas interfaces define contracts without implementation.

### Example:
```java
abstract class Vehicle {
    abstract void start();
    void stop() {
        System.out.println("Vehicle stopped");
    }
}

class Car extends Vehicle {
    void start() {
        System.out.println("Car starts with a key");
    }
}
```

---

## Exception in Java

### Hierarchy:
```
java.lang.Object
   ↳ java.lang.Throwable
         ↳ java.lang.Exception
         ↳ java.lang.Error
```

### Types of Exceptions

#### Checked Exceptions (Compile-time)
- Must be handled or declared with `throws`
- Examples: IOException, SQLException, ClassNotFoundException

#### Unchecked Exceptions (Runtime)
- Occur during program execution
- Examples: ArithmeticException, NullPointerException, ArrayIndexOutOfBoundsException

### try-catch-finally Example
```java
try {
    int a = 5 / 0;
} catch (Exception e) {
    System.out.println("Handled: " + e);
} finally {
    System.out.println("Finally block always executes");
}
```

### throw vs throws
- **throw:** Used to throw an exception manually.  
- **throws:** Declares exceptions that a method may throw.

---

## Interface in Java

- Reference type similar to a class  
- Defines abstract behavior (a contract)  
- Loaded by ClassLoader and stored in the Method Area

### Interface Facts
- Cannot be instantiated  
- Cannot have constructors  
- Can have variables (public, static, final by default)

Example:
```java
interface Animal {
    void sound();
}
class Dog implements Animal {
    public void sound() {
        System.out.println("Bark");
    }
}
```

---

## What is `public static void main(String[] args)`?
- **public:** accessible to JVM  
- **static:** can be invoked without creating an object  
- **void:** returns nothing  
- **main:** entry point of Java application  
- **String[] args:** command-line arguments

---
## Java Control Statements | Control Flow in Java
    Java provides three types of control flow statements.
        1.Decision Making statements
            1.Simple if statement
            2.if-else statement
            3.if-else-if ladder
            4.Nested if-statement
        2.switch statement
        3.Loop statements
            1.do while loop
            2.while loop
            3.for loop
        .Jump statements
            1.break statement
            2.continue statement
## Conditional Statements
        1.Simple if statement
        2.if-else statement
        3.if-else-if ladder
        4.Nested if-statement

---
## Array Defination
    Arrays are fundamental structures in Java that allow us to store multiple values of the same type in a single variable.
    1.In Java, all arrays are dynamically allocated.
    2.Arrays may be stored in contiguous memory.
    3.Since arrays are objects in Java, we can find their length using the object property length. This is different from C/C++, where we find length using size of.
    4.A Java array variable can also be declared like other variables with [] after the data type.
    5.It is the simplest data structure where each data element can be accessed directly by only using its index number.
    6.The variables in the array are ordered, and each has an index beginning with 0.
---
## Types of Methods
    In Java, methods can be categorized in two main ways:
    1. Predefined vs. User-defined:
        Predefined methods: These methods are already defined in the Java Class Library and can be used directly without any declaration.
            Examples include System.out.println() for printing to the console and Math.max() for finding the maximum of two numbers.
        User-defined methods: These are methods that you write yourself to perform specific tasks within your program. 
```java
Syntax:
    returnType methodName() {
    // method body
    }

    returnType - It specifies what type of value a method returns.
    methodName - It is an identifier that is used to refer to the particular method in a program.
    method body - It includes the programming statements that are used to perform some tasks.body is enclosed inside the curly braces { }.
```
---
# Advanced Java Topics

## Core Java (OOPs, Collections, Concurrency)
1. Difference between HashMap, LinkedHashMap, and ConcurrentHashMap  
2. Explain Java ClassLoader hierarchy and custom ClassLoaders  
3. Handling Deadlock Detection and Prevention in Java  
4. Fork/Join Framework and its Use Cases  
5. CompletableFuture vs Traditional Future

## Spring & Spring Boot
6. How Spring Boot Auto-Configuration Works  
7. @ComponentScan vs @EnableAutoConfiguration vs @SpringBootApplication  
8. Rate Limiting and Throttling in Spring Boot APIs  
9. Distributed Caching (Redis/Azure Cache)  
10. Securing Spring Boot Actuator Endpoints

## JPA / Hibernate
11. First-level vs Second-level Cache  
12. FetchType.LAZY vs FetchType.EAGER  
13. Multi-tenant Applications in JPA  
14. Optimistic vs Pessimistic Locking  
15. Dirty Checking and Flush Modes

## Microservices & Architecture
16. REST vs gRPC vs GraphQL APIs  
17. Service Discovery and Load Balancing  
18. Saga and Outbox Patterns  
19. Event-driven Systems (Kafka/Azure Service Bus)  
20. Backward Compatibility in APIs

## Core Java:
 
1. OOPs Concepts (Abstraction,Encapsulation,Polymorphism, Inheritance, IS-A relationship and HAS-A relationship)
2. Java 8 new features
3. Java Streams
4. Java NIO,Lamda, and Streams
5. What is JVM,JRE and JDK
6. What is the difference between overloading and Overridding in Java , Can you explain with examples? Is main method can overloaded?
7. What is immutable in Java, can you write java class with immutability?
8. How do you modify the run time behavior of java application? ( i.e explain about the reflection api with examples)
9. How to sort collection of objects java , can you explain with example?
10. What is serialization in java, can you give one example?
11. Can explain what are the new features added in java 8 with examples?
12. What is hashcode,equals() in java
13. Can  explain String Buffer and String Builder in java.
14. Can you explain thread pool executor in java?
15. Multithreading using Java 8
16. What is the difference between final, finally and finalize in java ?
17. Can you write custom exception class in java?
18. Difference between Overloading and Overriding
19. Explain rules to override a method
20. How do you prevent a method from being overridden?
21. Difference between Interface and Abstract class? When to go for Interfaces and When to choose Abstract classes?
22. Why do we have marker interfaces? Advantages of them
23. Importance of static in java
24. Difference between final and finally
25. What is hashcode() and equals() method? When will you override these methods? And explain with example…write code too.
26. What will happen if my I override hashcode() method which returns always same value.
27. What is difference between comparator and comparable? Explain with example.
28. Explain Java 5 new features
29. Explain Importance of finalize() method
30. What is the difference between Enumeration and Iterator?
31. ArrayList and Vector differences
32. HashMap and HashTable differences
33. Explain LinkedList,LinkedHashSet, and LinkedHashMap. And also differences, when to use each.
34. How do you decide when to use ArrayList and When to use   LinkedList?
35. What is the difference between Serializalble and Externalizable interface?
36. How will you sort collection of user defined objects? For example, Employee class having First Name, Last Name, and Age member variables. Assume that you have a 50 instances of Employee class stored in a List collection. How will you sort all employees by First Name.
37. What's the difference between the == operator and the equals() method?
38. What is Serialization?
39. Explain Synchronization and different ways of achieving this
40. Difference between String and StringBuffer?
41. Compare StringBuilder and StringBuffer
42. What is HashSet and TreeSet
43. Explain about Exception handling
44. What is stream in Java? Write a code to read from a file.
45. How will you read a image from database?
46. Explain different java io classes
47. Difference between Checked and Unchecked exceptions?
48. Difference between Throw and Throws?
Answer: Checked exception cannot be propagated using throw only.
49. How will you invoke garbage collector?
Answer: You as Java programmer can not force garbage collection in Java; it will only trigger if JVM thinks it needs a garbage collection based on Java heap size.
There are methods like System.gc() and Runtime.gc() which is used to send request of Garbage collection to JVM but it’s not guaranteed that garbage collection will happen.

 
Restful WebServices:
 
1. How does the request come to your Controller when you hit the URL in the browser? Understand end-end flow
2. What is restful ? is restful is stateless or Stateful, explain adv and disadvantages of restful web service?
3. What are the tools used for restful web service api testing?
4. Can you explain headers and content type supported by restful web services?
5. What are the different types of annotations which you used for restful webservice?
6. What is the difference between PathParam and RequestParam in restful web service?
7. How to validate incoming request for Restful web service and how do you identify either incoming request is get or post?
8. Can you explain what is JAX-RS?
9. Secrutiy
10. Explain different encryption and decryption alogorithims
 
 
 
J2EE:
 
1. Explain different types of JDBC drivers?
2. Difference between Statement and Prepared statements in JDBC?
3. How will you call stored procedure from java?
4. What is connection pooling?
5. Explain steps to establish a connection to DB?
6. How to implement a connection pooling?
7. What is SAX and DOM? Explain differences between them.
8. What is JAXB? Explain advantages of JAXB
9. What is Singleton design Patten? Write a code to achive this?
10. Advantages of Singleton pattern ?
11. Explain Factory and Abstract Factor design pattern
12. Explain Service Locator design pattern
13. What is the difference between doPost and doGet methods?
14. What is the life cycle of a servlet?
 
 
Spring:
1. What is IOC(Inversion Of Control) in Spring framework and Explain advantages
2. What are the different types of IOC in Spring framework?
3. Explain different modules in Spring Framework?
4. What is the difference between Bean Factory and Application Context ? 
5. Explain XMl over http concept?
6. Explain Spring Annotations
7.  
8. Explain Spring Security
9. Explain Spring streo types
10. Spring REST controller
11.  
Microservices:
1. What is microservice and advantages
2. What is config server
3. Spring cloud
4. spring eureka
 
Spring Boot:
 
1. Can you explain what is the Spring Boot and its features?
2. What are different types of starters in Spring Boot?
3. What is properties file in SpringBoot and how do you configure default properties in spring boot.
