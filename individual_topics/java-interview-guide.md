# Java Interview Questions and Answers (Core + Advanced)

A consolidated, plain-English study sheet covering Core Java and Advanced Java topics. No emojis, no fluff. Organized for quick scanning and last‑minute revision.

---

## Table of Contents

1. Core Java Basics
2. JVM, JRE, JDK and Bytecode
3. OOP: Classes, Objects, Inheritance, Polymorphism, Abstraction, Encapsulation
4. Access Control, Packages, Modifiers
5. `Object` Class and Common Methods
6. Constructors, Initialization Order, `this` and `super`
7. `instanceof`, IS‑A vs HAS‑A
8. Strings and Immutability
9. Wrapper Types, Autoboxing, Unboxing
10. `equals`, `hashCode`, `toString`
11. Collections and Maps
12. Generics
13. Iteration, Enumeration, Iterator, Streams
14. Comparable vs Comparator, Sorting
15. Arrays and Varargs
16. Exceptions and Error Handling
17. I/O and NIO/NIO.2
18. Concurrency and Multithreading
19. Locks, Executors, Fork/Join, CompletableFuture
20. Memory Model, GC, Escape Analysis
21. Reflection, Annotations
22. Serialization vs Externalization
23. Functional Programming, Lambdas, Method References
24. Streams API (intermediate/terminal ops)
25. Optional
26. Date/Time API (java.time)
27. Module System (Java 9+)
28. Java Language Features by Version (5–21 overview)
29. JUnit/Testing basics
30. Build Tools (Maven/Gradle) quick notes
31. RESTful Web Services overview
32. JDBC/JPA/Hibernate quick notes
33. Spring/Spring Boot quick notes
34. Microservices quick notes
35. Security basics (hashing, enc/dec) quick notes

---

## 1) Core Java Basics

### Q1. What is Java?
Java is a general‑purpose, object‑oriented, strongly‑typed language. It compiles to bytecode executed by the JVM, enabling portability across platforms.

### Q2. Difference between JDK, JRE, and JVM.
- JDK: Tools for developing Java (compiler, javadoc, etc.) + JRE.
- JRE: Runtime libraries and JVM to run Java apps.
- JVM: Abstract machine that loads, verifies, JIT‑compiles, and executes bytecode.

### Q3. How is bytecode generated?
The Java compiler (`javac`) converts `.java` source files into `.class` bytecode files.

### Q4. What is platform independence?
The same bytecode runs on different platforms with compatible JVMs; no recompilation is required.

---

## 2) JVM, JRE, JDK and Bytecode

### Q5. JVM components.
- Class Loader Subsystem (Bootstrap, Extension/Platform, Application)
- Linking (Verify, Prepare, Resolve), Initialization
- Runtime Data Areas: Method Area, Heap, Java Stacks, PC Registers, Native Method Stacks
- Execution Engine: Interpreter, JIT, Garbage Collector
- Native Interface (JNI) and Native Libraries

### Q6. Class loading phases.
Loading → Linking (Verify, Prepare, Resolve) → Initialization (static initializers run).

### Q7. JIT vs Interpreter.
Interpreter executes bytecode line‑by‑line. JIT compiles hot code paths to native code for speed; modern JVMs use mixed mode.

---

## 3) OOP: Classes, Objects, Inheritance, Polymorphism, Abstraction, Encapsulation

### Q8. What is a class? What is an object?
Class: blueprint defining state and behavior. Object: runtime instance of a class.

### Q9. Encapsulation.
Bundling data and methods; controlling access using access modifiers and getters/setters.

### Q10. Inheritance.
Mechanism to derive a subclass from a superclass to reuse/extend behavior. Supports single inheritance of classes.

### Q11. Polymorphism types.
- Compile‑time: method overloading.
- Runtime: method overriding via dynamic dispatch.

### Q12. Abstraction.
Expose essential behavior, hide details via abstract classes and interfaces.

---

## 4) Access Control, Packages, Modifiers

### Q13. Access modifiers.
- `public`: everywhere
- `protected`: same package + subclasses
- default (package‑private): same package
- `private`: within class

### Q14. Class level access.
Top‑level classes can be `public` or package‑private. Not `protected` or `private`.

### Q15. Other modifiers.
`final`, `static`, `abstract`, `synchronized`, `native`, `strictfp`, `transient`, `volatile`, `sealed` (Java 17).

---

## 5) `Object` Class and Common Methods

### Q16. Name common methods of `Object`.
`equals`, `hashCode`, `toString`, `getClass`, `clone`, `finalize` (deprecated), `wait`, `notify`, `notifyAll`.

### Q17. When override `equals` and `hashCode`?
When logical equality differs from reference equality, and when objects are used as map keys or in hash‑based collections.

---

## 6) Constructors, Initialization Order, `this` and `super`

### Q18. Constructor chaining.
Use `this(...)` for same‑class constructor, `super(...)` for parent; must be first statement.

### Q19. Initialization order.
Static fields/blocks (parent → child), then instance fields/blocks (parent → child), then constructors (parent → child).

### Q20. Use of `super`.
Access parent methods/fields or call parent constructor.

---

## 7) `instanceof`, IS‑A vs HAS‑A

### Q21. `instanceof` usage.
Checks runtime type compatibility, considering inheritance and interfaces.

### Q22. IS‑A vs HAS‑A.
IS‑A is inheritance; HAS‑A is composition/aggregation.

---

## 8) Strings and Immutability

### Q23. Why are Strings immutable?
Security, caching (string pool), thread‑safety, and reliable hashing for use as keys.

### Q24. `String` vs `StringBuilder` vs `StringBuffer`.
- `String`: immutable; concatenation creates new objects.
- `StringBuilder`: mutable, not synchronized; faster in single‑threaded contexts.
- `StringBuffer`: mutable, synchronized; legacy thread‑safe alternative.

---

## 9) Wrapper Types, Autoboxing, Unboxing

### Q25. What are wrapper classes?
Object representations of primitives: `Integer`, `Long`, `Double`, etc.

### Q26. Autoboxing and unboxing.
Automatic conversion between primitives and wrappers. Beware of null unboxing (NPE) and performance costs in hot code.

---

## 10) `equals`, `hashCode`, `toString`

### Q27. Equality contracts.
If `equals` is overridden, `hashCode` must be consistent with it. Equal objects must have equal hash codes.

### Q28. Best practices.
Use IDE or `Objects.equals`, `Objects.hash`, and include significant fields only.

---

## 11) Collections and Maps

### Q29. Main interfaces.
`Collection`, `List`, `Set`, `Queue`, `Deque`, and `Map` (separate hierarchy).

### Q30. ArrayList vs LinkedList.
ArrayList: random access, contiguous array, efficient append; LinkedList: efficient insert/remove in middle, higher overhead.

### Q31. HashMap vs Hashtable.
HashMap: not synchronized, allows one null key; Hashtable: synchronized, no nulls, legacy.

### Q32. HashSet vs TreeSet.
HashSet: hash‑based, no order; TreeSet: sorted (Red‑Black tree), requires Comparable/Comparator.

### Q33. LinkedHashMap.
Maintains insertion access order; supports LRU with accessOrder=true and `removeEldestEntry`.

### Q34. ConcurrentHashMap.
Partitioned (buckets/segments in older versions) concurrency, no locking of entire map; supports safe concurrent access.

### Q35. Fail‑fast vs fail‑safe iterators.
Fail‑fast (e.g., ArrayList) throw `ConcurrentModificationException`; fail‑safe (e.g., CopyOnWriteArrayList) iterate over snapshot.

---

## 12) Generics

### Q36. Purpose of generics.
Type safety and elimination of casts at compile time; implemented via type erasure.

### Q37. Wildcards.
`?`, `? extends T` (read‑only), `? super T` (write‑only). PECS rule: Producer Extends, Consumer Super.

### Q38. Type erasure implications.
No reified types, no `new T[]`, limited reflection on generic parameters at runtime.

---

## 13) Iteration, Enumeration, Iterator, Streams

### Q39. Enumeration vs Iterator.
Enumeration is legacy (Vector/Hashtable). Iterator supports removal and is preferred.

### Q40. ListIterator.
Bi‑directional traversal for lists; can add, set, remove during iteration.

---

## 14) Comparable vs Comparator, Sorting

### Q41. Difference.
Comparable defines natural order via `compareTo`. Comparator defines custom order via `compare`.

### Q42. Sorting examples.
Use `Collections.sort(list)` or `list.sort(comparator)`; for streams, `sorted()`.

---

## 15) Arrays and Varargs

### Q43. Array properties.
Fixed size, indexed from 0, `length` field, store primitives or references.

### Q44. Varargs.
`void m(String... s)` compiles to an array parameter; only one varargs parameter and it must be last.

---

## 16) Exceptions and Error Handling

### Q45. Hierarchy.
`Throwable` → `Error` (JVM issues) and `Exception` (checked/unchecked).

### Q46. Checked vs unchecked.
Checked must be declared/handled (IOException); unchecked are runtime (NPE, AIOOBE).

### Q47. `throw` vs `throws`.
`throw` creates/propagates a specific exception; `throws` declares possible exceptions.

### Q48. try‑with‑resources.
Auto‑closes resources implementing `AutoCloseable`.

### Q49. Custom exception.
Extend `Exception` (checked) or `RuntimeException` (unchecked).

---

## 17) I/O and NIO/NIO.2

### Q50. java.io vs java.nio.
`io` is stream‑based, blocking. `nio` is buffer‑based, channels/selectors, non‑blocking IO; NIO.2 adds Paths, Files, async channels, WatchService.

### Q51. File operations.
Use `java.nio.file.Files` and `Path` for modern file work.

---

## 18) Concurrency and Multithreading

### Q52. Creating threads.
Extend `Thread` or implement `Runnable`/`Callable` and submit to `ExecutorService`.

### Q53. Synchronization mechanisms.
` synchronized` blocks/methods, `ReentrantLock`, `ReadWriteLock`, `StampedLock`.

### Q54. Thread communication.
`wait/notify/notifyAll` or higher‑level constructs (BlockingQueue, Phaser, CountDownLatch, CyclicBarrier).

### Q55. Thread states.
NEW → RUNNABLE → BLOCKED/WAITING/TIMED_WAITING → TERMINATED.

### Q56. Thread safety strategies.
Immutability, confinement, atomic classes, synchronization, concurrent collections.

---

## 19) Locks, Executors, Fork/Join, CompletableFuture

### Q57. Executor framework.
`ExecutorService`, pools (`newFixedThreadPool`, `newCachedThreadPool`, `newWorkStealingPool`).

### Q58. Fork/Join.
Work‑stealing for divide‑and‑conquer tasks via `RecursiveTask`/`RecursiveAction`.

### Q59. CompletableFuture.
Asynchronous pipelines with composition (`thenApply`, `thenCompose`), combination (`allOf`, `anyOf`), exception handling (`exceptionally`).

---

## 20) Memory Model, GC, Escape Analysis

### Q60. Java Memory Model (JMM).
Defines visibility, ordering, and atomicity guarantees. `volatile` establishes happens‑before; locks also create happens‑before edges.

### Q61. GC basics.
Generational GC (young/old), collectors like Serial, Parallel, CMS (removed), G1, ZGC, Shenandoah (low‑pause). Tuning involves heap sizing and GC flags.

### Q62. `finalize` status.
Deprecated; use cleaners/try‑with‑resources instead.

---

## 21) Reflection, Annotations

### Q63. Reflection.
Inspect/modify classes, methods, fields at runtime via `java.lang.reflect`. Used for frameworks, DI, ORMs.

### Q64. Annotations.
Metadata processed at compile/runtime. Built‑in targets: type, method, field, parameter, module, etc. Retention: SOURCE, CLASS, RUNTIME.

---

## 22) Serialization vs Externalization

### Q65. Difference.
Serializable is marker with default mechanism. Externalizable gives full control via `writeExternal/readExternal`.

### Q66. `transient` and `serialVersionUID`.
`transient` fields are skipped; `serialVersionUID` ensures version compatibility.

---

## 23) Functional Programming, Lambdas, Method References

### Q67. Functional interfaces.
Single abstract method interfaces like `Runnable`, `Callable`, `Comparator`, `Function`, `Predicate`, `Supplier`, `Consumer`.

### Q68. Method references.
`Class::staticMethod`, `Class::instanceMethod`, `instance::method`, `Class::new` for constructors.

---

## 24) Streams API

### Q69. Stream types.
Sequential and parallel streams; base interfaces: `Stream<T>`, `IntStream`, `LongStream`, `DoubleStream`.

### Q70. Intermediate vs terminal ops.
Intermediate: `map`, `filter`, `flatMap`, `distinct`, `sorted`, `peek`, `limit/skip`.
Terminal: `forEach`, `collect`, `reduce`, `count`, `anyMatch/allMatch/noneMatch`, `findFirst/findAny`.

### Q71. Collectors.
`toList`, `toSet`, `toMap`, `groupingBy`, `partitioningBy`, `mapping`, `joining`, `summarizingInt`.

---

## 25) Optional

### Q72. Why `Optional`?
Model presence/absence explicitly to avoid `null` checks; not intended for fields or serialization.

### Q73. Useful methods.
`of`, `ofNullable`, `empty`, `map`, `flatMap`, `filter`, `orElse`, `orElseGet`, `orElseThrow`, `ifPresent`, `ifPresentOrElse`.

---

## 26) Date/Time API (java.time)

### Q74. Key classes.
`LocalDate`, `LocalTime`, `LocalDateTime`, `ZonedDateTime`, `Instant`, `Duration`, `Period`, `ZoneId`, `DateTimeFormatter`.

### Q75. Thread safety.
java.time types are immutable and thread‑safe.

---

## 27) Module System (Java 9+)

### Q76. What is JPMS?
Java Platform Module System organizes code into modules with explicit dependencies and exports, improving encapsulation and start‑up.

### Q77. `module-info.java` basics.
`module name { requires x; exports pkg; }`

---

## 28) Java Language Features by Version (brief)

- Java 5: Generics, annotations, enums, varargs, concurrency utilities.
- Java 7: try‑with‑resources, multi‑catch, diamond operator for anonymous classes? (diamond added in 7 for generics instantiation).
- Java 8: lambdas, streams, default/static interface methods, Optional, new Date/Time API.
- Java 9: modules, JShell, reactive streams `Flow`.
- Java 10: `var` (local type inference).
- Java 11: HTTP Client, string/file additions, `var` in lambda params.
- Java 14: switch expressions (standardized in 14), records (14 preview, 16 GA).
- Java 15+: text blocks (15), sealed classes (17), pattern matching for `instanceof` (16), virtual threads (19/21), record patterns (19/21).

---

## 29) JUnit/Testing (brief)

### Q78. Basics.
Arrange‑Act‑Assert, test isolation, deterministic outcomes.

### Q79. JUnit annotations.
`@Test`, `@BeforeEach`, `@AfterEach`, `@BeforeAll`, `@AfterAll`, `@Disabled`.

---

## 30) Build Tools (brief)

### Q80. Maven vs Gradle.
Maven: convention‑over‑configuration, XML POM. Gradle: Groovy/Kotlin DSL, incremental builds, faster caching.

---

## 31) RESTful Web Services (brief)

### Q81. Core ideas.
Resource‑oriented, statelessness, standard methods (GET/POST/PUT/PATCH/DELETE), content negotiation via `Accept`/`Content-Type`.

### Q82. Validation and versioning.
Bean Validation (`javax.validation`/`jakarta.validation`), API versioning (URI/header).

---

## 32) JDBC/JPA/Hibernate (brief)

### Q83. JDBC essentials.
Drivers, connections, statements (Statement/PreparedStatement/CallableStatement), result sets, connection pooling.

### Q84. JPA/Hibernate basics.
Entities, repositories, persistence context, dirty checking, cascading, fetching (`LAZY`/`EAGER`), first/second‑level cache.

---

## 33) Spring / Spring Boot (brief)

### Q85. IoC/DI.
Container manages object creation and wiring; `@Component`, `@Service`, `@Repository`, `@Controller`, `@Configuration`.

### Q86. Auto‑configuration.
`@SpringBootApplication` combines `@Configuration`, `@EnableAutoConfiguration`, `@ComponentScan`.

### Q87. Profiles and configuration.
`application.yml/properties`, profiles, actuator endpoints security.

---

## 34) Microservices (brief)

### Q88. Service discovery and config.
Eureka/Consul, Spring Cloud Config, API gateways, circuit breakers (Resilience4j).

### Q89. Messaging.
Kafka, RabbitMQ; idempotency, outbox pattern, saga orchestration vs choreography.

---

## 35) Security basics (brief)

### Q90. Hashing vs encryption.
Hashing is one‑way for integrity (e.g., passwords with salt). Encryption is two‑way for confidentiality (symmetric/asymmetric).

---

# Appendix: Focused Q&A Expansions

## Overloading vs Overriding

### Q91. Can `main` be overloaded?
Yes. Only the exact signature `public static void main(String[] args)` is the entry point.

### Q92. Prevent overriding.
Declare method `final`, or class `final`, or use private methods (not visible to subclass).

---

## Collections Deep Dive

### Q93. Collision handling in HashMap.
Buckets store nodes; collisions are resolved via linked lists or balanced trees (since Java 8) when bins exceed a threshold.

### Q94. Ordering in LinkedHashMap.
Maintains insertion or access order. Useful for simple LRU caches by overriding `removeEldestEntry`.

---

## Concurrency Deep Dive

### Q95. `volatile` vs `synchronized`.
`volatile` ensures visibility and prevents reordering for a single variable; `synchronized` provides mutual exclusion and visibility for critical sections.

### Q96. Deadlock detection and prevention.
Avoid circular wait via lock ordering; use timeouts; prefer higher‑level concurrency utilities; analyze with thread dumps and tools.

### Q97. Thread‑pool sizing.
CPU‑bound: ~cores; IO‑bound: higher, depends on blocking ratio.

---

## Streams Patterns

### Q98. `map` vs `flatMap`.
`map` transforms elements; `flatMap` flattens nested streams or optionals.

### Q99. Parallel streams caveats.
Use when operations are stateless, non‑blocking, and data is large; beware of synchronization and ordering costs.

---

## Serialization Notes

### Q100. When to use Externalizable.
When you need custom, compact, or version‑tolerant binary formats and full control over fields written/read.

---

# Cleaned Items Merged From Your Draft

- Bytecode generation: `javac` → `.class`.
- JVM components: class loader, runtime data areas, execution engine, JNI.
- Class, object, constructor chaining, `this`/`super` rules.
- Inheritance, IS‑A vs HAS‑A, `instanceof`.
- Overloading vs overriding, rules, access/exception constraints.
- `Object` class methods.
- Access modifiers and why classes cannot be `protected`.
- Abstract classes vs interfaces with concise example.
- Exceptions: hierarchy, checked vs unchecked, `throw`/`throws`, try‑catch‑finally.
- Interfaces: facts and example.
- `public static void main(String[] args)` explained.
- Control flow, arrays, method types and syntax.
- Advanced index: Spring Boot auto‑config, caches, Actuator security, JPA fetching and caching, microservice patterns.

---

Notes:
- This document is intentionally concise. It focuses on high‑yield interview topics in Core Java and provides short advanced overviews.
- For a 1,500‑question compendium, consider splitting into multiple files by category (Core, Concurrency, Collections, Streams, JVM, Spring, JPA, Microservices).

