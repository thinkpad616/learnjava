# learnjava

how does bytecode gets generated?
java compiler converts .java file to .class or bytecode

what are components of jvm and explain?
jvm consists of five main components 
1. class loader sub system.
 1. Loading: Classloader is classified into three types
  1. Bootstrap classloader.
  2. Extension classloader.
  3. Application classloader.
 2. Linking.
  1. Prepare.
  2. Verify.
  3. Initialize.
 3. Initialization.
2. Run time data area or memory area.
1. Method area.
2. heap area
3. Stack area.
4. PC register.
5. Native method.
3. Execution engine.
1. Interpreter.
Executes bytecode instructions line by line
2. Just in time compiler.(jit)

3. Garbage collector.
4. Native method area.
5. Native method interface.
1. what is a class?
- A class is a blueprint or template which holds variables and methods. A class variable or method can be accessed only using object instantiation, and memory for non-static (instance) variables is allocated only when an object is created during execution. Static variables belong to the class itself and are allocated memory when the class is loaded by the JVM. A class can also have constructors to initialize object state, and access modifiers like private, protected, and public control visibility. Methods of a class are stored in the method area and frequently used methods are compiled into native code by the JIT compiler for faster execution. Garbage collector removes memory of objects when they are no longer referenced, while static members remain until JVM shuts down.
2. what is an object?
 - Object is a instance of a class, to access any member of a class.

what is parent class in java.lang package?
The parent class of all classes in Java is the Object class, which is defined in the java.lang package.
	•	Object is declared as a public class, so it’s accessible to all other classes.
	•	Every class in Java implicitly extends Object, even if you don’t write extends Object in your code.
	•	This means every class automatically inherits methods from the Object class — such as:
	•	toString()
	•	equals(Object obj)
	•	hashCode()
	•	getClass()
	•	clone()
	•	finalize()
	•	wait(), notify(), notifyAll()

How to call one constructor from the other constructor ?
- using this() we can call other constructor in same class and it should be the first line of constructor. we can pass values as per other constructor initialization.

overriding vs overloading ?
overriding:
- overriding happens in inheritance where method from parent class is overriden in subclass
- overriding is based on runtime polymorphism (dynamic binding)
- we use @override keyword when impimenting
- we cannot reduce accessmodifer from parent class
- child class cannot throw broader checked exception from parent class. 
overloading:
- overloading is compile time polymorphism
- overloading happens in same class we can use same methodname with differt return types and input values.
- ovverloading doesnt have any barriers with exceptions or access modifier. 

what is super keyword in java?
- super key word can be used while a subclass extends parent class to reference variables in constructor which should be first line in constructor. and we can also use super key word to call method from parent class in child class.

is a relationship vs has a relationship in java?
is a relation ship is inheritance where child class extends parent class. 
has a relationship is like using object in another class. like car object (instance of class) is created in engine class and engine uses its methods. 

Explain about instanceof operator in java?
- instanceof is used to check weather an obeject is an instance of class.class Animal { }
class Dog extends Animal { }

Animal a = new Dog();
System.out.println(a instanceof Animal);  // true
System.out.println(a instanceof Dog);     // true
System.out.println(a instanceof Object);  // true
System.out.println(a instanceof String);  // false
Animal b = null;
System.out.println(b instanceof Animal);  // false


3. Why can a class not be defined as protected?
 - class can be either public or package private only
 - https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html

Explain what access modifiers can be used for variables?
private is accessable witin the class 
public is accessable anywhere
protected is accessable witin the same package. 
default is accessable within the package

explain abstract class in java?
- abstract class in java contains abstract methods along with implimentation methods with concrete logic.
- it can be used with extends keyword as a abstract class cannot be instantiated.

abstract class Vehicle {
    abstract void start();  // abstract method
    void stop() {           // concrete method
        System.out.println("Vehicle stopped");
    }
}

class Car extends Vehicle {
    void start() {
        System.out.println("Car starts with a key");
    }
}

public class Test {
    public static void main(String[] args) {
        Vehicle v = new Car();  // reference of abstract class
        v.start();
        v.stop();
    }
}

what are abstract methods in java?
- abstract methods does not have any implementation. 

what is an exception in java?

➤ Core Java (OOPs, Collections, Concurrency)
1.	Difference between HashMap, LinkedHashMap, and ConcurrentHashMap.
2.	Explain Java ClassLoader hierarchy and how custom ClassLoaders work.
    - 
3.	How to handle deadlock detection and prevention in Java?
4.	Explain Fork/Join Framework and its use cases.
5.	What are the advantages of using CompletableFuture over traditional Futures?

➤ Spring & Spring Boot

6.	How does Spring Boot auto-configuration choose which beans to create?
7.	Explain the difference between @ComponentScan, @EnableAutoConfiguration, and @SpringBootApplication.
8.	How do you implement rate limiting and throttling in Spring Boot APIs?
9.	How do you implement distributed caching with Spring Boot (Redis/Azure Cache)?
10.	Explain Spring Boot Actuator endpoints and how to secure them.

➤ JPA / Hibernate

11.	Explain first-level vs second-level cache in Hibernate.
12.	Difference between FetchType.LAZY and FetchType.EAGER and how to optimize queries.
13.	How do you handle multi-tenant applications in JPA?
14.	Explain optimistic vs pessimistic locking with real examples.
15.	How does dirty checking and flush mode work in Hibernate?

➤ Microservices & Architecture

16.	Explain the difference between REST, gRPC, and GraphQL APIs.
17.	How do you achieve service discovery and load balancing in microservices?
18.	Explain Saga and Outbox patterns for distributed transactions.
19.	How do you design an event-driven system (Azure Service Bus/Kafka)?
20.	How do you ensure backward compatibility for APIs in microservices?
