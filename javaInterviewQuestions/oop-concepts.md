# OOP Concepts (Study Guide + Examples)

## Contents
- Classes and Objects
- Constructors, Overloading, Chaining
- `this`, `super`
- Encapsulation (getters/setters, invariants)
- Inheritance (single inheritance, IS-A)
- Composition/Aggregation (HAS-A)
- Polymorphism (Overloading vs Overriding)
- Abstraction (abstract classes, interfaces)
- Access Control and Design
- Immutability patterns
- Records (Java 16+)
- Enums (stateful behavior)

---

## Classes and Objects
A class defines state (fields) and behavior (methods). Objects are instances.
```java
class Account {
    private double balance;
    public void deposit(double amt) { balance += amt; }
    public double getBalance() { return balance; }
}
```

## Constructors, Overloading, Chaining
```java
class Point {
    final int x, y;
    Point(int x, int y) { this.x = x; this.y = y; }
    Point() { this(0, 0); } // chaining
}
```

## `this`, `super`
`this` refers to current instance; disambiguates field names. `super` accesses parent members; `super(...)` calls parent constructor first.

## Encapsulation
Hide fields; expose behavior. Validate invariants via setters or constructors.
```java
class Person {
    private final String name;
    Person(String name) {
        if (name == null || name.isBlank()) throw new IllegalArgumentException();
        this.name = name;
    }
    public String name() { return name; }
}
```

## Inheritance
```java
class Animal { void speak() { } }
class Dog extends Animal { @Override void speak(){ System.out.println("bark"); } }
```

## Composition/Aggregation
```java
class Engine { void start(){ } }
class Car {
    private final Engine engine = new Engine();
    void start(){ engine.start(); }
}
```

## Polymorphism
- Overloading: same name, different params (compile-time).
- Overriding: subclass changes behavior (runtime).
Rules: same signature; covariant return allowed; cannot reduce visibility; cannot throw broader checked exceptions.

## Abstraction
### Abstract class
```java
abstract class Vehicle {
    abstract void start();
    void stop(){ System.out.println("stopped"); }
}
```
### Interface (Java 8+)
```java
interface Flyable {
    void fly();
    default void land(){ System.out.println("landing"); }
    static void info(){ System.out.println("Flyable"); }
}
```

## Immutability
Final class, private final fields, no setters, defensive copies.
```java
final class ImmutableRange {
    private final int start, end;
    ImmutableRange(int s, int e){
        if (s > e) throw new IllegalArgumentException();
        this.start = s; this.end = e;
    }
    int start(){ return start; }
    int end(){ return end; }
}
```

## Records (Java 16+)
```java
public record Point(int x, int y) { }
```

## Enums with State/Behavior
```java
enum Op {
    ADD { int apply(int a,int b){ return a+b; } },
    MUL { int apply(int a,int b){ return a*b; } };
    abstract int apply(int a,int b);
}
```
