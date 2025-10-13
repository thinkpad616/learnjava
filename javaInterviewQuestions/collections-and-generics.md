# Collections and Generics (Study Guide + Examples)

## Contents
- Collection Framework Overview
- List, Set, Queue/Deque
- Map implementations
- ArrayList vs LinkedList
- HashSet vs LinkedHashSet vs TreeSet
- HashMap vs LinkedHashMap vs TreeMap vs ConcurrentHashMap
- Iterators, Fail-fast vs Fail-safe
- Comparable vs Comparator
- Sorting patterns
- Generics: type parameters, wildcards, bounds
- PECS rule and examples
- Type erasure implications
- Streams primer for collections

---

## Collection Framework Overview
Common root: Iterable<T> → Collection<T> → subinterfaces List, Set, Queue; Map<K,V> is separate.

## List
- ArrayList: dynamic array, O(1) random access; resizing cost.
- LinkedList: doubly linked list; efficient at insert/remove in middle.

## Set
- HashSet: unordered, hash-based.
- LinkedHashSet: insertion order.
- TreeSet: sorted, requires Comparable or Comparator.

## Map
- HashMap: average O(1) get/put; tree bins since Java 8.
- LinkedHashMap: predictable iteration order; LRU with removeEldestEntry.
- TreeMap: sorted by natural or custom order.
- ConcurrentHashMap: concurrent operations; avoids locking whole map.

### Example: LRU with LinkedHashMap
```java
class LruCache<K,V> extends LinkedHashMap<K,V> {
    private final int cap;
    LruCache(int cap) { super(16, 0.75f, true); this.cap = cap; }
    @Override protected boolean removeEldestEntry(Map.Entry<K,V> e){ return size() > cap; }
}
```

## Iterators: Fail-fast vs Fail-safe
- Fail-fast (e.g., ArrayList) throws ConcurrentModificationException on structural change during iteration.
- Fail-safe (e.g., CopyOnWriteArrayList) iterates over a snapshot.

## Comparable vs Comparator
```java
class Emp implements Comparable<Emp> {
    String name; int age;
    public int compareTo(Emp o){ return this.name.compareTo(o.name); }
}
Comparator<Emp> byAge = Comparator.comparingInt(e -> e.age);
```

## Sorting
```java
list.sort(Comparator.comparing(Emp::getName).thenComparingInt(Emp::getAge));
```

## Generics
- Type parameters: class Box<T> { T value; }
- Wildcards: ?, ? extends T, ? super T
- Bounds: <T extends Number>

### PECS
- Producer Extends: List<? extends T> for reading.
- Consumer Super: List<? super T> for writing.
```java
static void copy(List<? extends Number> src, List<? super Number> dst) {
    for (Number n : src) dst.add(n);
}
```

## Type Erasure
Generic info is erased; cannot `new T[]`; limited reflection on generic params.

## Streams Primer
```java
List<String> names = Arrays.asList("Bob", "Alice", "Carl");
List<String> upper = names.stream()
    .filter(n -> n.length() > 3)
    .map(String::toUpperCase)
    .sorted()
    .toList();
```
