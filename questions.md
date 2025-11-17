Core Java & OOPs (Deep-Dive Questions) 
1. Explain OOP principles with real-world examples .
2. Abstraction vs encapsulation (real-world example) .
3. What is immutability? How to create immutable classes .
4. How does HashMap work internally? What happens during resizing?
5. ConcurrentHashMap vs Collections.synchronizedMap()
6. Thread lifecycle + Thread.start() vs run()
7. ExecutorService vs ForkJoinPool
8. Custom sorting using Comparator & Comparable .
9. Java Memory Model (JMM) + volatile .
10. How to detect + fix memory leaks in Java .
Spring Framework / Spring Boot 
1. Lifecycle of a Spring Bean .
2. @Autowired vs @Inject .
3. How @Transactional works internally (Propagation + Isolation) .
4. What are Spring Boot starters? .
5. Creating custom annotations in Spring .
6. ApplicationContext vs BeanFactory .
7. How Spring performs DI using reflection .
8. CommandLineRunner vs ApplicationRunner .
9. How to externalize configuration in Spring Boot .
10. Spring Boot Actuator — most used endpoints .
Microservices Architecture 
1. What is service discovery? (Eureka/Consul) .
2. REST vs Kafka vs gRPC — which to use when? .
3. Common microservices challenges & solutions .
4. Microservices security: OAuth2/JWT .
5. What is distributed tracing? (Zipkin, Sleuth, OpenTelemetry) .
6. Circuit Breaker, Retry, Rate Limiting .
7. Inter-service transactions (Saga, 2PC) .
8. Role of an API Gateway .
9. Spring Cloud Config Server .
Coding / Problem-Solving (EPAM Favorites) 
1. Second highest number in an array .
2. Reverse Linked List (iterative & recursive) .
3. First non-repeated character in a string .
4. Implement an LRU Cache .
5. Find pair sum equal to a target .
6. Producer-Consumer using wait() & notify() .
7. REST API → Top 5 highest salaries by department .
8. Sort Employee by salary → then by name .
9. Calculate totals by user ID using Streams .
10. Implement API rate limiting in Java .
--------------------------------------------------------------------------------
• Explained a feature I developed — covering API design, database structure, and code optimization .
• Discussed approaches for improving performance and scalability in microservice environments .
Hibernate Caching 
• Types of caching supported by Hibernate (1st-level and 2nd-level) .
• Memory impact and caching configuration details .
• Discussion on which queries are cached and how caching improves efficiency .
Spring Boot & Bean Creation 
• Explained multiple ways to create beans in Spring Boot using annotations .
• Discussed dependency injection and bean lifecycle management .
Data Structures & Java 8 Streams 
• Solved a problem to search a target element in an integer array (sorted/unsorted) .
• Discussed time complexity and then reimplemented the logic using Java 8 Stream API for cleaner code .
Database Indexing & Query Optimization 
• Explored indexing in SQL and NoSQL databases .
• Discussed trade-offs of creating too many indexes and how it affects write operations .
• Covered how indexes work differently in MySQL vs NoSQL .
ORM & Hibernate Performance 
• Explained the N+1 Query Problem with real-world entity examples (Customer-Order relationship) .
• Discussed strategies to mitigate it using fetch joins and entity graphs .
Security 
• Discussed the difference between Authentication and Authorization in application design and how they are implemented in Spring Security .
--------------------------------------------------------------------------------
1. What's the main difference between Collections and Streams? (Collections store data; Streams process data through a pipeline of operations.) .
2. What's the difference between intermediate and terminal operations? (Intermediate operations (like map, filter) are lazy; terminal ones (like collect, forEach) trigger execution.) .
3. How does lazy evaluation improve performance in Streams? (Operations are executed only when needed, reducing unnecessary computation.) .
4. What's the difference between map() and flatMap()? (map() transforms elements; flatMap() flattens nested structures like lists of lists.) .
5. What's the role of Collectors.toMap() and how do you handle key collisions? (It builds a map from a stream, and requires a merge function for duplicate keys.) .
6. How do parallel streams differ from sequential ones? (Parallel streams split work across multiple threads via the Fork/Join framework.) .
7. Why should you be careful with stateful operations in parallel streams? (Shared mutable state can cause race conditions or unpredictable results.) .
8. How does reduce() differ from collect()? (reduce() combines elements into a single result; collect() is more flexible for mutable reduction (like building collections).) .
9. How does short-circuiting work in Streams? (Operations like findFirst() or anyMatch() stop processing once a condition is satisfied.) .
10. Why are streams not reusable? (Once consumed by a terminal operation, a stream pipeline closes and cannot be reused.) .Closing Question: What's your favorite Stream trick or collector? Share it below .
--------------------------------------------------------------------------------
Microservices Resilience Patterns (Resilience4j) 
1. What is a Circuit Breaker? Why do we need it? .
2. Explain states of Circuit Breaker (Closed, Open & Half-Open) .
3. What triggers a Circuit Breaker to move to Open state? .
4. What happens in Half-Open state? How does it decide to go back to Closed? .
5. What is failure-rate-threshold, sliding-window-size, and minimum-number-of-calls? .
6. What is Rate Limiter? Where do we use it? .
7. What happens when we exceed configured rate limit? Blocked or Queued? .
8. What is Time Limiter? What if external service takes too long? .
9. What is Retry pattern? How is retry different from circuit breaker? .
Caching 
1. What is caching? Why do we use it? .
2. Difference between @Cacheable, @CachePut, and @CacheEvict .
3. What is key in caching annotations? .
4. What is the value (cache container name)? .
5. EhCache vs Redis — differences & use cases .
6. Is EhCache a separate server? .
7. Why Redis is best for distributed microservices? .
8. Where do we configure Ehcache vs Redis? .
9. What is T.T.L in caching? .
10. Can cache survive application restart? .
Config Server & API Gateway 
1. Why do we use Config Server in Microservices? .
2. If properties are inside config server — do we still need them in local application.yml? .
3. Dynamic refresh — how @RefreshScope works? .
4. Why do we use an API Gateway in Microservices Architecture? .
--------------------------------------------------------------------------------
Spring Boot Core 
1. Explain Spring Boot Auto-configuration? How does it work internally, and how do you customize it using @ConditionalOnProperty or @autoconfigureBefore? .
2. Difference between @Component, @Service, @Repository — Are they functionally different or just semantic? .
3. Explain the Bean Lifecycle — @PostConstruct, @PreDestroy, InitializingBean, DisposableBean — when to use which? .
4. How does Spring Boot Actuator help in production monitoring? Explain /health, /metrics, and custom endpoints .
5. How do you build custom Spring Boot starters? Walk through the folder structure and auto-configuration setup .
Spring Security & Authentication 
1. How does Spring Security Filter Chain work internally? Explain the flow from request to authentication .
2. What is the OAuth2 + JWT authentication flow? How do you implement stateless authentication in microservices? .
3. How do you implement role-based access control (RBAC)? @PreAuthorize vs @Secured vs manual checking .
Microservices & Distributed Systems 
1. Explain the Circuit Breaker pattern — How does Resilience4j help prevent cascading failures? .
2. What is idempotency in REST APIs? How do you ensure POST/PUT requests don't create duplicate records? .
3. How do you implement distributed tracing? Sleuth + Zipkin or OpenTelemetry — trace IDs across services .
4. What is the Saga pattern? How do you handle distributed transactions without 2PC? .
JPA / Hibernate / Database 
1. What is the N+1 problem? How do you solve it using @EntityGraph or JOIN FETCH? .
2. Difference between lazy and eager loading — When does LazyInitializationException occur? .
3. Explain optimistic vs pessimistic locking — @Version annotation and use cases .
--------------------------------------------------------------------------------
Microservices & Architecture 
1. Why do we prefer Microservices over Monolithic? .
2. What is Saga Design Pattern? Types (Choreography vs Orchestration)? Where have you used it? .
3. What is a Circuit Breaker? When do we use one? (Resilience patterns – Hystrix, Resilience4j) .
4. What is the Observer Design Pattern? (Pseudo code below) .
5. Abstract Factory Pattern — What is it? Where does Spring use it internally? .
6. What is AOP? Real-life examples (logging, transactions, security) .
7. IoC & DI — Why do we use them? .
Spring Boot 
1. What is a Spring Bean? .
2. How does Spring Boot auto-configure the database? .
3. How do you connect a DB in Spring Boot? (application.properties, DataSource config) .
4. What is a Functional Interface? .
5. Thread-safe collections in Java? .
6. Fail-Fast vs Fail-Safe Iterators .
7. Why do we use Redis? (Caching, distributed sessions, low-latency reads) .
Core Java 
1. == vs equals() .
2. OOPS: Composition vs Aggregation .
3. Interface vs Abstract Class — when to use? .
4. What is a volatile keyword? .
5. How to make a class thread-safe? (synchronized, immutable, enums, locks) .
6. What is Multithreading and why do we use it? .
7. HashMap internal working (hashing, resizing, collision handling) .
8. How to find the frequency of characters? .
Database 
1. Difference between Functions and Stored Procedures .
2. Normalization forms (1NF, 2NF, 3NF) .
3. How database schema/tables are created in Spring Boot (Hibernate DDL auto) .
4. How do we connect our spring boot application with a database in a cloud environment .
Coding Round 
1. Write infix to postfix string conversation? .
2. Write sql to find 5th maximum salary in a student table .
--------------------------------------------------------------------------------
1. What is the Spring IoC container and how does it manage dependencies? .
2. Difference between @Component, @Repository, and @Service .
3. What is Spring Boot Auto-Configuration, and how can you disable it? .
4. Explain Spring AOP with a real-world example (logging/security) .
5. Explain Spring Transaction Management (Propagation & Isolation) .
6. How does @Transactional work under the hood? .
7. What are Spring Boot Actuators and how do you monitor metrics? .
8. Difference between CommandLineRunner and ApplicationRunner .
9. How do you implement Custom Exception Handling in REST APIs? .
10. How do you secure REST APIs using JWT + Spring Security? .
Microservices & Distributed Systems (Deep Design Concepts) 
1. Difference between Monolithic, SOA, and Microservices architectures .
2. Explain Service Discovery (Eureka / Consul) and Load Balancing .
3. What is the Circuit Breaker Pattern, and when do you use it? .
4. How do you achieve Inter-Service Communication (REST, Kafka, gRPC)? .
5. Explain Distributed Tracing and tools like Sleuth, Zipkin, OpenTelemetry .
6. How do you handle Configuration Management in microservices? .
7. What is Idempotency, and how do you design idempotent APIs? .
8. Explain Saga Pattern and Event-Driven Architecture .
9. How do you ensure Data Consistency across multiple microservices? .
10. How do you implement API Versioning in microservices? .
