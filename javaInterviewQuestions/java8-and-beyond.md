# Java 8 and Beyond (Study Guide + Examples)

## Contents
- Lambdas and Method References
- Functional Interfaces
- Streams (intermediate and terminal ops)
- Collectors (grouping, partitioning, mapping, reducing)
- Optional
- Default/Static methods in interfaces
- Date/Time (java.time)
- var (Java 10), Records (16), Sealed Classes (17), Pattern Matching
- Text Blocks (15), Switch Expressions (14)

---

## Lambdas
```java
Function<Integer,Integer> f = x -> x * x;
```

## Method References
```java
List<String> names = List.of("a","b","c");
names.forEach(System.out::println);
```

## Functional Interfaces
Function, Predicate, Supplier, Consumer, UnaryOperator, BinaryOperator, Comparator, Runnable, Callable.

## Streams
```java
Map<Integer, Long> freq = List.of(1,2,2,3,3,3)
    .stream()
    .collect(Collectors.groupingBy(x -> x, Collectors.counting()));
```

## Optional
```java
Optional<String> os = Optional.of("x");
String v = os.map(String::toUpperCase).orElse("NA");
```

## Date/Time
```java
LocalDateTime now = LocalDateTime.now();
ZonedDateTime z = now.atZone(ZoneId.of("UTC"));
Duration d = Duration.between(now, now.plusHours(5));
```
