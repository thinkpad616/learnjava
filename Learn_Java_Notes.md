# Learn Java

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
