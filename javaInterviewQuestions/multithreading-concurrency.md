# Multithreading and Concurrency (Study Guide + Examples)

## Contents
- Thread model and lifecycle
- Creating threads (Runnable, Callable, Thread)
- Synchronization and intrinsic locks
- ReentrantLock, ReadWriteLock, StampedLock
- Atomic variables
- Condition, wait/notify, high-level coordination (CountDownLatch, CyclicBarrier, Phaser, Semaphores)
- Executors and Thread Pools
- ScheduledExecutorService
- Fork/Join framework
- CompletableFuture
- Parallel streams
- Deadlocks, livelocks, starvation
- Java Memory Model, happens-before, volatile
- Best practices

---

## Creating Threads
```java
// Runnable
new Thread(() -> System.out.println("Hello")).start();

// Callable with Future
ExecutorService es = Executors.newSingleThreadExecutor();
Future<Integer> f = es.submit(() -> 42);
int ans = f.get();
es.shutdown();
```

## Synchronization
```java
class Counter {
    private int n;
    synchronized void inc(){ n++; }
    synchronized int get(){ return n; }
}
```

## ReentrantLock and Conditions
```java
Lock lock = new ReentrantLock();
Condition notEmpty = lock.newCondition();
```

## ReadWriteLock and StampedLock
ReentrantReadWriteLock for read-mostly workloads; StampedLock for optimistic reads.

## Atomic Variables
```java
AtomicInteger ai = new AtomicInteger();
ai.incrementAndGet();
```

## wait/notify vs High-level Utilities
Prefer BlockingQueue, Semaphore, CountDownLatch, CyclicBarrier, Phaser for clearer concurrency control.

## Executors
newFixedThreadPool, newCachedThreadPool, newWorkStealingPool. Always shutdown.

## ScheduledExecutorService
```java
ScheduledExecutorService ses = Executors.newScheduledThreadPool(1);
ses.scheduleAtFixedRate(() -> System.out.println("tick"), 0, 1, TimeUnit.SECONDS);
```

## Fork/Join
```java
class SumTask extends RecursiveTask<Long> {
    final int[] arr; final int lo, hi;
    SumTask(int[] a,int l,int h){ this.arr=a; this.lo=l; this.hi=h; }
    protected Long compute(){
        if (hi - lo < 1000) { long s=0; for (int i=lo;i<hi;i++) s+=arr[i]; return s; }
        int mid=(lo+hi)/2;
        SumTask left = new SumTask(arr, lo, mid);
        SumTask right = new SumTask(arr, mid, hi);
        left.fork();
        long r = right.compute();
        long l = left.join();
        return l + r;
    }
}
```

## CompletableFuture
```java
CompletableFuture<Integer> result =
    CompletableFuture.supplyAsync(() -> 21)
        .thenApply(x -> x * 2)
        .exceptionally(ex -> -1);
```

## Deadlocks
Avoid circular waits; impose lock ordering; use timeouts.

## Java Memory Model and volatile
volatile ensures visibility for a variable; synchronization adds mutual exclusion and happens‑before edges.
