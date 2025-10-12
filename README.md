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
3. Why can a class not be defined as protected?
 - class can be either public or package private only
 - https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html


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
