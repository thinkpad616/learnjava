# Java Interview Questions — Complete Answers

This file now contains expanded, interview-friendly answers for all questions in the repository. Each section includes: a one-line definition, how it works, a short example or snippet (where helpful), and when/why to use it plus common pitfalls.

If anything still looks short, tell me the specific question(s) you'd like me to expand further.

---

## Core Java & OOP

### Explain OOP principles with real-world examples
- Encapsulation — Definition: Group related state and behavior and restrict direct access to internal state.
   - How it works: Use `private` fields and expose controlled APIs (getters, setters or business methods) to manipulate state.
   - Example: `Car` exposes `accelerate()`; internal fields like `engineRpm` are private.
   - When to mention: design, validation, and testing.

- Abstraction — Definition: Expose only essential behavior and hide complex implementation details.
   - How it works: Provide interfaces or abstract classes that hide implementation.
   - Example: ATM `withdraw()` hides DB/network/validation.

- Inheritance — Definition: Code reuse via `extends` (is-a relationship).
   - When to use: modeling clear taxonomy; avoid if it causes tight coupling.

- Polymorphism — Definition: Single interface, multiple implementations. Runtime (overriding) vs compile-time (overloading).
   - Example: `List` used as `ArrayList` or `LinkedList`; call methods on the `List` interface.

Short answer structure: definition → mechanism → example → trade-offs.

---

### Abstraction vs Encapsulation
- Encapsulation: data hiding (private fields + controlled API).
- Abstraction: simplifying use by exposing a higher-level interface.
- Example: Encapsulation hides `engine.rpm`; abstraction hides entire engine details behind `drive()`.

---

### Immutability — how and why
- One-line: An immutable object's state cannot change after construction.
- How to implement: final class, private final fields, initialize in constructor, defensive copy for mutable inputs/outputs, no setters.
- Example: `String`, `Integer`, and `ImmutableEmployee` (see earlier example).
- Use-cases: safe sharing between threads, cache keys, simpler reasoning.

---

## Collections, Maps & Streams

### How HashMap works & resizing
- Internals: keys hashed via `hashCode()`, transformed, and mapped into a bucket index in an array. Buckets store entries — linked list or tree (when bucket size grows).
- Resizing: when size > capacity * loadFactor (default 0.75), capacity doubles and entries are rehashed — O(n) cost.
- Interviewable points: hashCode contract, avoid mutable keys, and choose initial capacity to reduce resizing.

### ConcurrentHashMap vs Collections.synchronizedMap
- `synchronizedMap`: single global lock, poor concurrency for many threads.
- `ConcurrentHashMap`: fine-grained concurrency (lock striping/CAS), higher throughput, no null keys/values.

### Comparator vs Comparable
- `Comparable`: natural order (`compareTo`).
- `Comparator`: external, composable ordering, use `Comparator.comparing()` and `thenComparing()`.

### Streams essentials
- Collections store; Streams process. Intermediate ops are lazy; terminal ops trigger computation.
- Use `collect()` for building collections; `reduce()` for pure reductions.
- Parallel streams: watch for thread-safety and associative operations.

---

## Concurrency & Java Memory Model

### Thread lifecycle and start() vs run()
- `start()` creates a new thread and executes `run()` in it; calling `run()` directly runs on current thread.
- States: NEW → RUNNABLE → BLOCKED/WAITING/TIMED_WAITING → TERMINATED.

### ExecutorService vs ForkJoinPool
- `ExecutorService`: general task execution (tunable pools: fixed, cached).
- `ForkJoinPool`: work-stealing pool optimized for divide-and-conquer tasks (`RecursiveTask`).

### CompletableFuture
- Non-blocking composition of async tasks, supports chaining and combining results; prefer over manually managing threads.

### JMM & volatile
- `volatile` provides visibility and ordering guarantees for single reads/writes, but not atomicity for compound operations.
- For atomic compound ops use `synchronized` or `Atomic` types.

### Detecting memory leaks
- Tools: `jmap`, `jstack`, VisualVM, Eclipse MAT. Common causes: static caches, ThreadLocal, unclosed resources. Fixes: remove references, use weak/soft refs, close resources.

---

## Spring & Spring Boot — deeper answers

### Bean lifecycle (detailed)
- Steps: Instantiation → Populate properties (DI) → `BeanPostProcessor` pre-initialize → `@PostConstruct` / `afterPropertiesSet()` → `BeanPostProcessor` post-initialize → bean ready. On shutdown: `@PreDestroy` / `DisposableBean`.
- Note: AOP/transaction proxies mean `this` method calls may bypass proxies; explain use of self-injection or `AopContext` if needed.

### `@Autowired` vs `@Inject`
- `@Autowired` is Spring-specific and supports `required=false`, `@Qualifier`, etc. `@Inject` is standard JSR-330; both work in Spring if JSR support enabled.

### `@Transactional` internals, propagation and isolation
- Implementation: AOP proxy wraps method calls and starts/commits/rolls back transactions via `PlatformTransactionManager`.
- Propagation: `REQUIRED` joins existing txn or starts one; `REQUIRES_NEW` suspends existing and starts a new one; others include `SUPPORTS`, `MANDATORY`, `NOT_SUPPORTED`.
- Isolation levels: control phenomena like dirty reads, non-repeatable reads, phantom reads—common levels: READ_COMMITTED, REPEATABLE_READ, SERIALIZABLE.
- Rollback rules: unchecked exceptions cause rollback by default; checked exceptions do not unless configured.

### Starters and auto-configuration
- Starters are dependency bundles. Auto-configuration uses `spring.factories`/`@Conditional` annotations to create beans based on classpath and properties. Customize via `@ConditionalOnProperty`, `@AutoConfigureBefore/After`, or disable auto-configurations.

### ApplicationContext vs BeanFactory (practical)
- `BeanFactory`: lower-level, lazy. `ApplicationContext`: feature-rich (events, resource loading, message source). Use `ApplicationContext` for typical apps.

### DI via reflection
- Spring inspects constructors and fields, chooses beans by type/name/qualifiers, creates instances via constructor/factory and injects dependencies using reflection or generated bytecode (via CGLIB or reflection proxies).

### CommandLineRunner vs ApplicationRunner
- `CommandLineRunner` gets raw args; `ApplicationRunner` gets parsed `ApplicationArguments` (options, non-option args).

### Externalized configuration and Actuator
- `application.yml`/`properties`, env vars, command-line args, or Config Server. Use `@ConfigurationProperties` for structured binding.
- Actuator endpoints: `/actuator/health`, `/actuator/metrics`, `/actuator/env`. Secure them in production.

---

## Microservices — practical details

### Service discovery
- Services register with registry (Eureka/Consul) or use Kubernetes service discovery (DNS). Clients query the registry or use client-side load balancing (Ribbon) or server-side LB.

### REST vs gRPC vs Kafka
- REST: human-friendly, simple.
- gRPC: efficient, strongly typed, good for high-throughput internal RPCs.
- Kafka: event-driven, durable messaging for streaming/decoupling.

### Distributed tracing
- Propagate trace and span IDs via headers; use OpenTelemetry to collect traces, export to Zipkin/Jaeger; analyze latencies and spans.

### Resilience patterns
- Circuit Breaker: stops calling failing downstream and transitions states (Closed → Open → Half-Open). Configurable with failure-rate-threshold, sliding-window-size, and minimum-number-of-calls.
- Retry: attempts retries with backoff for transient errors.
- Rate limiting: token/leaky bucket algorithms; implement at gateway or service.

### Saga vs 2PC
- 2PC locks resources across services and is rarely used. Saga splits into local transactions with compensating actions; implement via choreography (events) or orchestration (central coordinator).

---

## Caching — precise answers

### Hibernate caching types
- First-level cache: session-scoped, enabled by default — caches entities within a session.
- Second-level cache: shared across sessions; requires provider (Ehcache, Hazelcast, Infinispan). Cache entities or query results.

### Memory & caching config
- Second-level cache reduces DB hits but increases memory use; configure eviction, TTL, max-entries, and persistence depending on provider.

### Which queries are cached
- Entity caches store entities by id; query caches (optional) cache result id lists and require careful invalidation on writes.

### `@Cacheable` / `@CachePut` / `@CacheEvict`
- `@Cacheable`: read-through caching — method result stored for given args.
- `@CachePut`: updates cache regardless of existing value (useful after writes).
- `@CacheEvict`: removes entries on updates/deletes; supports allEntries and beforeInvocation.

### Redis vs Ehcache
- Redis: external, distributed, supports persistence and clustering—preferred for microservices.
- Ehcache: in-process (fast), can be clustered via Terracotta, simpler for single-node apps.

### TTL and restart behavior
- TTL: time-to-live configuration for cached entries.
- Cache survive restart? Redis can persist to disk (RDB/AOF); in-process caches typically lost during restart unless backed by a clustered store.

---

## Data & JPA — covered and extended

### N+1 problem
- Cause: lazy fetching causing separate queries per parent when iterating children.
- Fixes: `JOIN FETCH` in JPQL, `@EntityGraph`, DTO projection (fetch only needed columns), or batch fetching.

### Lazy vs Eager trade-offs
- Lazy avoids fetching unnecessary data but requires session/transaction; Eager may fetch more data than needed.

### Optimistic vs Pessimistic locking
- Optimistic: use `@Version`; detect conflicts on commit.
- Pessimistic: use database locking queries (`SELECT ... FOR UPDATE`).

---

## Spring Security & Auth (concise)

### Filter chain
- Spring Security uses a chain of filters (once per request) to authenticate and authorize; ordering matters (authentication filters → authorization filters → security context establishment).

### OAuth2 + JWT
- Flow: user logs in → auth server issues JWT → client sends JWT in Authorization header → services validate signature and claims (stateless).

### RBAC: `@PreAuthorize` vs `@Secured`
- `@Secured` is simpler (role-based only). `@PreAuthorize` uses SpEL for richer expressions (roles, permissions, method args).

---

## Streams & Collections — Q&A recap
- Covered earlier; remember to mention short-circuiting ops (`anyMatch`, `findFirst`) and that streams are single-use.

---

## Coding Round — answers / hints

1) Infix to postfix (shunting-yard): implement stack for operators and output queue; handle precedence and parentheses. Interviewers expect explanation of algorithm and O(n) complexity.

2) SQL find 5th max salary: several ways — window function or distinct subquery.
    - Window function (recommended):
       ```sql
       SELECT * FROM (
          SELECT salary, ROW_NUMBER() OVER (ORDER BY salary DESC) rn
          FROM students
       ) t WHERE rn = 5;
       ```
    - Distinct approach:
       ```sql
       SELECT DISTINCT salary FROM students ORDER BY salary DESC LIMIT 1 OFFSET 4;
       ```

---

## Quick interview answer template
1. One-line definition.
2. How it works (internals or mechanism).
3. Short example.
4. When to use + pitfalls.

---

If you'd like, I will now:
- Split this file into per-topic files under `individual_topics/` (recommended for study sessions). 
- Add runnable implementations for selected practice problems under `exercises/` (I can create Java classes and unit tests).
- Produce a printable one-page cheat sheet summarizing key commands/commands and definitions.

Tell me which one you'd like next and I will proceed.

---

## Remaining detailed answers and runnable examples

Below are expanded answers and short runnable examples for many of the practical questions you listed earlier. Read each block, try the code locally (copy into a small Java class), and talk through the explanation while you code — that's a great interview prep method.

### `==` vs `equals()`
- `==` compares object references (identity). `equals()` compares logical equality and can be overridden.
- Example:
```java
String a = new String("x");
String b = new String("x");
System.out.println(a == b);       // false (different objects)
System.out.println(a.equals(b)); // true (same contents)
```

Interview tips: mention `equals` + `hashCode` contract for use in hash-based collections.

### Composition vs Aggregation
- Composition: strong ownership — lifetime of part is bound to whole (e.g., `Car` has an `Engine` created inside and destroyed with the car).
- Aggregation: weaker association — part can exist independently (e.g., `Team` has `Player`s which may exist outside the team).

### Interface vs Abstract Class
- Interface: contract of behavior; from Java 8 can have default and static methods; multiple interfaces supported.
- Abstract class: partial implementation and shared state; single inheritance. Use abstract class when you need shared code and state.

### `volatile` in-depth with example
- `volatile` ensures visibility and ordering for single reads/writes. It prevents the JVM from caching the variable in a thread-local CPU register.
- Example (visibility):
```java
class Flag { private volatile boolean stop = false; void stop(){ stop = true; } boolean isStopped(){ return stop; } }
// One thread sets stop(), another thread polling isStopped() will see the change.
```
- Caveat: `volatile` does not provide atomicity for compound operations (e.g., `count++`). Use `AtomicInteger` or synchronization for that.

### How to make a class thread-safe (patterns)
- Immutability (final fields, no setters)
- Synchronization: `synchronized` methods/blocks
- Locking: `ReentrantLock`, read/write locks
- Atomic variables: `AtomicInteger`, `AtomicReference`
- Thread-safe collections: `ConcurrentHashMap`, `CopyOnWriteArrayList`

### HashMap resizing example and implications
- Resizing happens when size > capacity * loadFactor. Rehashing re-distributes entries which costs O(n).
- Practical note: if you expect ~1,000,000 entries, set initial capacity to avoid repeated resizing: `new HashMap<>(1_333_333)` (approx 1M/0.75).

### ExecutorService example
```java
ExecutorService ex = Executors.newFixedThreadPool(4);
List<Callable<String>> tasks = List.of(() -> "A", () -> "B");
List<Future<String>> futures = ex.invokeAll(tasks);
for(Future<String> f : futures) System.out.println(f.get());
ex.shutdown();
```

### ForkJoin example (RecursiveTask)
```java
class SumTask extends RecursiveTask<Long> {
   private final long[] arr; int lo, hi; int THRESHOLD = 1000;
   SumTask(long[] arr,int lo,int hi){this.arr=arr;this.lo=lo;this.hi=hi;}
   protected Long compute(){
      if(hi-lo<=THRESHOLD){ long s=0; for(int i=lo;i<hi;i++) s+=arr[i]; return s; }
      int mid=(lo+hi)/2; SumTask a=new SumTask(arr,lo,mid); SumTask b=new SumTask(arr,mid,hi);
      a.fork(); long sb=b.compute(); long sa=a.join(); return sa+sb;
   }
}
ForkJoinPool.commonPool().invoke(new SumTask(arr,0,arr.length));
```

### Producer-Consumer — BlockingQueue example (recommended)
```java
class PC {
   public static void main(String[] args){
      BlockingQueue<Integer> q=new ArrayBlockingQueue<>(10);
      Runnable prod=()->{ for(int i=0;i<100;i++){ q.put(i); } };
      Runnable cons=()->{ while(true){ Integer v=q.take(); System.out.println(v); } };
      new Thread(prod).start(); new Thread(cons).start();
   }
}
```

### LRU Cache — LinkedHashMap implementation
```java
class LRUCache<K,V> extends LinkedHashMap<K,V>{
   private final int capacity;
   LRUCache(int capacity){ super(capacity,0.75f,true); this.capacity=capacity; }
   protected boolean removeEldestEntry(Map.Entry<K,V> eldest){ return size()>capacity; }
}
```

### Reverse Linked List — iterative & recursive code
Iterative:
```java
ListNode prev=null, curr=head;
while(curr!=null){ ListNode next=curr.next; curr.next=prev; prev=curr; curr=next; }
return prev;
```
Recursive (brief): reverse rest and append current.

### First non-repeated character — sample code
```java
int firstNonRepeated(String s){ Map<Character,Integer> cnt=new LinkedHashMap<>(); for(char c:s.toCharArray()) cnt.merge(c,1,Integer::sum);
 for(var e:cnt.entrySet()) if(e.getValue()==1) return e.getKey(); return -1; }
```

### Implementing LRU cache by hand (HashMap + DoublyLinkedList) — brief approach
- Maintain head/tail of doubly-linked list for recency and a HashMap from key to node for O(1) access. On access move node to head; on insert remove tail when capacity exceeded.

### Infix to Postfix (shunting-yard) — algorithm summary
- Use an operator stack and an output list. For each token: numbers -> output; operator -> pop higher/equal precedence operators to output, then push operator; parentheses handled specially. Complexity O(n).

### SQL: 5th maximum salary — alternatives
- Window function (ROW_NUMBER / DENSE_RANK) — handles duplicates.
- DISTINCT + ORDER BY + LIMIT/OFFSET for simpler DBs.

### Circuit Breaker config (Resilience4j) — example snippet
```yaml
resilience4j.circuitbreaker.instances.backendA.registerHealthIndicator=true
resilience4j.circuitbreaker.instances.backendA.slidingWindowSize=50
resilience4j.circuitbreaker.instances.backendA.failureRateThreshold=50
resilience4j.circuitbreaker.instances.backendA.waitDurationInOpenState=5000
```

Explain: `slidingWindowSize` controls sample size; `failureRateThreshold` % of failures to open circuit; `waitDurationInOpenState` how long before trying half-open.

### `@Transactional` example with propagation explanation
```java
@Service
class AService{
   @Transactional
   public void outer(){ repo.save(...); inner(); }
   @Transactional(propagation = Propagation.REQUIRES_NEW)
   public void inner(){ repo.save(...); }
}
```
If `inner()` is `REQUIRES_NEW`, it runs in its own transaction (commit/rollback independent of `outer`).

### Detecting memory leaks — example commands
- `jmap -heap <pid>` to inspect heap config; `jmap -dump:format=b,file=heap.hprof <pid>` then open in Eclipse MAT to find biggest GC roots.

### HashMap vs ConcurrentHashMap code differences (null behavior)
- `HashMap` allows one null key and many null values; `ConcurrentHashMap` forbids null keys/values since null return value could be ambiguous in concurrent context.

---

If you want all topics split into individual files or runnable code for the problems above, I can create an `exercises/` folder and add Java classes and simple JUnit tests for each implementation (LRU, reverse linked list, producer/consumer, infix->postfix). Tell me which of the practice problems you want implemented first and I'll add the code and tests.
