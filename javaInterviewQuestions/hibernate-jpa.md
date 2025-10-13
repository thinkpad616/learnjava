# Hibernate / JPA (Study Guide + Examples)

## Contents
- Entities, primary keys, generation strategies
- Mappings: one-to-one, one-to-many, many-to-many
- Cascading and orphan removal
- Fetch types (LAZY/EAGER)
- JPQL and Criteria API
- Transactions and the persistence context
- Dirty checking and flush modes
- Optimistic vs Pessimistic locking
- 1st and 2nd level caches
- N+1 problem and solutions
- DTO projections

---

## Entity Basics
```java
@Entity
class User {
  @Id @GeneratedValue(strategy=GenerationType.IDENTITY)
  Long id;
  String email;
}
```

## Relationships
```java
@Entity
class Order {
  @ManyToOne(fetch = FetchType.LAZY) Customer customer;
  @OneToMany(mappedBy="order", cascade=CascadeType.ALL, orphanRemoval=true)
  List<OrderLine> lines = new ArrayList<>();
}
```
