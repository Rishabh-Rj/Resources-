# 🚀 MEGA Java Backend Interview Guide (Company-Wise → Topic-Wise)

> Consolidated from **all 60 files** in `Interview_Questions/Company_Wise_Interview_Questions/`
> (Accenture, Airtel, Amazon, Amex, Capgemini, Cognizant, Deloitte, EPAM, EY, Flipkart, Google, Infosys, JPMorgan, Mastercard, Optum/Synchron, PayPal, TCS, Tech Mahindra, Wells Fargo, Wissen, and 40+ more).

## How to read this file

| Symbol | Meaning |
|---|---|
| 🟢 Basic | Definition / fundamentals – must answer in 1–2 min |
| 🟡 Intermediate | Internals, comparison, small coding, "why" |
| 🔴 Advanced | Production scenarios, design trade-offs, concurrency/distributed correctness |
| 🔥 | Asked by **3+ companies** (high frequency) |
| ➡️ **Follow-ups** | Questions interviewers commonly ask *after* the main answer |

- Duplicates are merged: **one row per unique question**, with every company that asked it.
- Abbreviations: *Acc* = Accenture, *CTS* = Cognizant, *TechM* = Tech Mahindra, *JPM* = JPMorgan, *MC* = Mastercard, *Amex* = American Express, *WF* = Wells Fargo, *Cap* = Capgemini, *Alti* = Altimetrik, *Misc* = "z Other Miscellanous / UnClassified" files.
- "Key points" are answer skeletons, not full essays – expand them with your own project examples (interviewers repeatedly said: *"don't memorize definitions, explain internals + real project usage"*).

## Table of Contents

1. [Core Java & OOP](#1-core-java--oop)
2. [Collections & HashMap Internals](#2-collections--hashmap-internals)
3. [Multithreading & Concurrency](#3-multithreading--concurrency)
4. [Java 8+ Streams, Lambdas & Optional](#4-java-8-streams-lambdas--optional)
5. [JVM, Memory Management & Garbage Collection](#5-jvm-memory-management--garbage-collection)
6. [Spring & Spring Boot Internals](#6-spring--spring-boot-internals)
7. [Spring Security, JWT & OAuth](#7-spring-security-jwt--oauth)
8. [Hibernate, JPA & SQL](#8-hibernate-jpa--sql)
9. [Microservices & System Design](#9-microservices--system-design)
10. [Kafka & Event-Driven Architecture](#10-kafka--event-driven-architecture)
11. [Redis, Caching & Performance](#11-redis-caching--performance)
12. [AWS, Docker, Kubernetes & CI/CD](#12-aws-docker-kubernetes--cicd)
13. [DSA & Java Coding Problems (with solutions)](#13-dsa--java-coding-problems-with-solutions)
14. [Real-World Production Troubleshooting Scenarios](#14-real-world-production-troubleshooting-scenarios)
15. [Extras: Frontend, Behavioral, HR, AI-Screening Rounds](#15-extras-frontend-behavioral-hr--ai-screening-rounds)
16. [🎯 Preparation Priority Checklist](#16--preparation-priority-checklist)
17. [Company Cheat-Sheet](#17-company-cheat-sheet)

---

## 1. Core Java & OOP

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | OOP pillars with real-time/project examples; encapsulation vs abstraction | 🔥 Acc, Deloitte, Infosys, Tata Nexarc, Delhivery, Logixal, Nagaro | 🟢 |
| 2 | Abstract class vs Interface (incl. default/static/private methods after Java 8); when to choose which | 🔥 Acc, CTS, TCS, Deloitte, Charter Global, MC, Nagaro, Infosys, Tata Nexarc | 🟢🟡 |
| 3 | Diamond problem; two interfaces with same default method – what happens, how to fix (`A.super.m()`); "class wins" rule | 🔥 Deloitte, Citi, MC, Optum, Virtuasa, Misc | 🟡 |
| 4 | Overloading vs overriding; rules child must follow when overriding; are overloaded/overridden methods inherited; method hiding | 🔥 Deloitte, TechM, Tata Nexarc, Alti, CTS, Misc | 🟢🟡 |
| 5 | `Parent p = new Child()` – which method runs? Why `Child c = new Parent()` is invalid | CTS | 🟢 |
| 6 | `==` vs `.equals()`, String pool, `new String("hello")` vs literal, `intern()`, where the pool lives | 🔥 Bajaj, Deloitte, EY, Optum, Tata Nexarc, i-exceed | 🟡 |
| 7 | Why String is immutable? `String` vs `StringBuilder` vs `StringBuffer` | 🔥 Acc, Amex, Optum, TechM, NTT, Virtuasa, EPAM, HCL, Charter Global, Deloitte | 🟢🟡 |
| 8 | Create an **immutable class** (final class, private final fields, no setters, defensive copy of `List`); how many ways; can it have getters; example other than String | 🔥 Acc, CTS, Charter Global, HCL, Synchron, Tata Nexarc, Wissen, MC, Infosys | 🟡 |
| 9 | Exceptions: checked vs unchecked, `throw` vs `throws`, `final/finally/finalize`, try-catch-finally order, can `finally` be skipped, exception inside finally, multi-catch, try-with-resources, custom exceptions, exception chaining | 🔥 Acc, Datatex, Deloitte, Tata Nexarc, Nagaro, Citi, JPM, Airtel, Optum | 🟢🟡 |
| 10 | `static` keyword, static block vs instance block, can `main` be overloaded, `this` in static context | Acc, ACL, Deloitte, CTS | 🟢 |
| 11 | JDK vs JRE vs JVM; platform independence; classloader hierarchy; `ClassLoader` vs `Class.forName()` | Acc, Infosys, PayPal, Misc | 🟢🟡 |
| 12 | Wrapper classes: Integer cache (-128..127), `==` on boxed values; autoboxing/unboxing performance pitfalls | NavajNa, Optum | 🟡 |
| 13 | `Comparable` vs `Comparator`; why `TreeSet` throws `ClassCastException` | 🔥 Acc, CTS, Cap, HCL, JPM, Virtuasa | 🟢🟡 |
| 14 | Marker interfaces, Serialization (`serialVersionUID`, `transient`, class evolution), Filter streams | MC, PayPal, TechM, Infosys | 🟡 |
| 15 | Records (auto equals/hashCode/toString, immutable, can implement interface, **cannot extend**), sealed classes, pattern matching, `var` (compile-time inference; not for fields/generic args) | 🔥 Alti, Bravura, IntraEdge, EY, Cap, Optum, TCS, Citi | 🟡 |
| 16 | Java 8 / 11 / 17 / 21 features; why migrate 8 → 17 (GC, perf, security); libraries that broke during migration | 🔥 Cap, Citi, Bravura, JPM, Virtuasa, Logixal, Acc, Infosys | 🟡 |
| 17 | Inner classes, effectively final, functional programming, generics (`? extends` vs `? super`) | Bajaj, Citi, Logixal, Deloitte | 🟡 |
| 18 | `ThreadLocal`, Reflection API cost, `ServiceLoader`, MethodHandles, custom `Spliterator` | Optum, PayPal | 🔴 |
| 19 | Timezone handling in Java (`java.time`, store UTC) | Datatex | 🟡 |
| 20 | `BigDecimal` vs `double` for money | PwC | 🟢 |
| 21 | Design patterns: Singleton (thread-safe), Factory / Abstract Factory, Builder, Strategy, State, Observer, Proxy, Saga, Outbox | 🔥 ACL, Acc, Cap, Deloitte, Barclays, Wissen, i-exceed, Kotak, MC, NTT | 🟡 |
| 22 | SOLID with real examples; LSP violated in production; inheritance-vs-composition failure; "if subclass replaces parent, why inheritance?" | 🔥 ACL, Barclays, Cap, Citi, Infosys, Optum, Alti, Virtuasa, Nagaro | 🟡 |
| 23 | Replace if-else heavy code (Strategy + Factory); add a UPI payment without modifying existing logic (Open/Closed) | ACL, MC, Kotak | 🟡 |
| 24 | Aggregation vs composition vs association; IS-A vs HAS-A | CTS, Deloitte, Optum, Virtuasa, Acc | 🟡 |

### Key points / follow-ups

**Immutable class template**
```java
public final class Order {
    private final long id;
    private final List<String> items;           // mutable type => defensive copy

    public Order(long id, List<String> items) {
        this.id = id;
        this.items = List.copyOf(items);        // copy in
    }
    public long getId() { return id; }
    public List<String> getItems() { return items; } // already unmodifiable
}
```
➡️ *Why `final` class? Why defensive copy? Can reflection break it? Is `record` deeply immutable (no – shallow)?*

**Thread-safe Singleton (Acc, JPM, NTT, i-exceed)**
```java
public final class Config {
    private Config() {}
    private static class Holder { static final Config INSTANCE = new Config(); } // lazy + thread-safe
    public static Config getInstance() { return Holder.INSTANCE; }
}
// Alternatives: enum singleton (safe vs serialization + reflection);
// double-checked locking requires `private static volatile Config instance;`
```
➡️ *How to break a singleton (reflection, serialization, clone)? Why `volatile` in DCL?*

**Method hiding vs overriding** – static methods are *hidden* (resolved by reference type at compile time); instance methods are *overridden* (runtime dispatch).

**try/catch/finally** – `finally` runs even after `return`; skipped only by `System.exit`, JVM crash, infinite loop; `return` in `finally` swallows the exception.

**Records** – compact constructor for validation; implicitly `final`; static members allowed; no extra instance fields.

**More follow-ups**
- Why must a `HashMap` key be immutable? (mutating a field used in `hashCode` after insert → entry becomes unreachable) 🔥 (Cap, Citi, EY)
- `final` vs `finally` vs `finalize` (finalize deprecated).
- Why can't a functional interface have 2 abstract methods? (lambda needs a single target method).
- Can a class have the `static` keyword? (only nested classes).
- Optimising `result += word` in a loop → `StringBuilder` (NTT).

---

## 2. Collections & HashMap Internals

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | 🔥 **How HashMap works internally** – hash(), index = `(n-1) & hash`, buckets, collision (linked list → red-black tree at ≥8 nodes & table ≥64; back to list at ≤6), load factor 0.75, default capacity 16, resize ×2 & rehash | Acc, ACL, Alti, Amazon, Birlasoft, Cap, Charter Global, CTS, Deloitte, EPAM, Google, HCL, i-exceed, JPM, Optum, TCS, TechM, Virtuasa, WF, Misc (20+) | 🟡 |
| 2 | What changed in HashMap in Java 8 (treeification, tail insertion, no more infinite-loop on resize) | Alti, Deloitte, EPAM, Optum | 🟡 |
| 3 | `equals()` vs `hashCode()` contract; override one but not the other; same hashCode but equals false | 🔥 Acc, Amazon, Deloitte, JPM, WF, CTS | 🟡 |
| 4 | Why HashMap key should be immutable; what if the field used in hashCode changes after insertion | 🔥 Cap, Citi, EY | 🟡 |
| 5 | HashMap vs ConcurrentHashMap vs Hashtable vs `Collections.synchronizedMap` – when to use each | 🔥 Acc, Airtel, Alti, Amazon, CTS, EY, JPM, Comviva, PwC, TCS, Tata Nexarc, TechM, WF, UnClassified | 🟡 |
| 6 | **ConcurrentHashMap internals** – Java 7 segments vs Java 8 CAS + `synchronized` on bin head, no locking for reads, size via `CounterCell`, null keys/values disallowed | 🔥 Airtel, Deloitte, Mphasis, Optum, TechM, JPM, Misc | 🔴 |
| 7 | HashMap vs LinkedHashMap vs TreeMap (ordering, complexity, null handling) | 🔥 HCL, Deloitte, Synchron, Tata Nexarc, Wissen | 🟢🟡 |
| 8 | Why HashMap allows one null key; HashMap vs Hashtable | Acc, Infosys | 🟢 |
| 9 | Two threads modify the same HashMap – what happens? (lost updates, corrupted structure, infinite loop in Java ≤7) | Alti, Google, PwC | 🟡 |
| 10 | Performance impact of resize/rehash and how to avoid (pre-size: `new HashMap<>(expected/0.75+1)`) | Optum, i-exceed | 🟡 |
| 11 | HashSet internals (backed by HashMap), treeification | EPAM, Misc | 🟡 |
| 12 | ArrayList vs LinkedList (get/insert complexity, memory, cache locality); max size of ArrayList (~`Integer.MAX_VALUE-8`) | 🔥 Acc, Alti, Birlasoft, Charter Global, Datatex, Tata Nexarc, Cap, Misc | 🟢 |
| 13 | List vs Set vs Map – choosing for a use case; HashSet vs LinkedHashSet vs TreeSet; Vector vs ArrayList | Acc | 🟢 |
| 14 | **Fail-fast vs fail-safe** iterators, `ConcurrentModificationException`, `Iterator` vs `ListIterator` | 🔥 Acc, Airtel, Amex, CTS, Deloitte, UnClassified, Virtuasa | 🟡 |
| 15 | `CopyOnWriteArrayList` internals, use case & memory overhead | Optum, TechM | 🟡 |
| 16 | `WeakHashMap`, `IdentityHashMap` use cases | Optum, Misc | 🔴 |
| 17 | How to make `LinkedList` / collections synchronized | EPAM, Synchron | 🟢 |
| 18 | Implement your own `Iterator`/`Iterable` (hasNext/next/remove) | Wissen | 🟡 |
| 19 | Sort a Map by value / by key | Acc, JPM | 🟡 |
| 20 | Which data structure for very large datasets / top-K when data doesn't fit in memory | Bravura, EY | 🔴 |
| 21 | Implement **LRU cache** (HashMap + doubly linked list; or `LinkedHashMap` with `accessOrder=true`) | Flipkart, JPM | 🟡🔴 |
| 22 | Thread-safe cache with expiration | Synchron | 🔴 |

### Key points

- **index** = `(n - 1) & (h ^ (h >>> 16))`; capacity always power of 2.
- Treeify when bucket ≥ **8** *and* table ≥ **64** (else just resize). Untreeify at ≤ **6**.
- Resize at `size > capacity × 0.75`; Java 8 preserves order in split lists (lo/hi lists) — no reversal → no infinite loop.
- `ConcurrentHashMap.put`: empty bin → CAS insert; otherwise `synchronized(binHead)`. `get` is lock-free (volatile reads). `computeIfAbsent`/`merge` are atomic per key. `size()` is an estimate under contention.
- Compound ops (`check-then-put`) on CHM still need `putIfAbsent`/`compute`.

**LRU cache with LinkedHashMap (quick answer)**
```java
class LRUCache<K, V> extends LinkedHashMap<K, V> {
    private final int capacity;
    LRUCache(int capacity) { super(capacity, 0.75f, true); this.capacity = capacity; }
    @Override protected boolean removeEldestEntry(Map.Entry<K, V> e) { return size() > capacity; }
}
```
(Full O(1) HashMap + DLL version is in §13.)

➡️ **Follow-ups**: What if two keys collide and `equals` is true? Why power-of-2 capacity? Why 0.75? Why 8 for treeify (Poisson distribution)? Can ConcurrentHashMap hold null? Is `Collections.synchronizedMap` iteration thread-safe (no – lock manually)? Make LRU thread-safe (synchronize / `ReentrantReadWriteLock` / Caffeine).

---

## 3. Multithreading & Concurrency

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | Thread lifecycle (NEW vs RUNNABLE etc.); ways to create threads & which is preferred; Thread vs Runnable | 🔥 Acc, Airtel, CTS, Deloitte, EPAM, HCL, Synchron, Misc | 🟢 |
| 2 | `start()` vs `run()`; `wait()` vs `sleep()` vs `yield()` vs `join()`; `notify()` vs `notifyAll()` | 🔥 Acc, CTS, Deloitte, EPAM, Virtuasa | 🟢🟡 |
| 3 | `synchronized` (method vs block, instance vs static lock) | 🔥 Acc, CTS, Bravura, Tata Nexarc, Wissen, Misc | 🟢🟡 |
| 4 | **`synchronized` vs `ReentrantLock`** (tryLock, fairness, interruptible, multiple Conditions; always `unlock` in `finally`) | 🔥 Alti, Amex, Bravura, Deloitte, EPAM, HCL, JPM, PwC, TCS, TechM, Virtuasa, Misc, Deloitte | 🟡 |
| 5 | `ReentrantLock` vs `ReentrantReadWriteLock` (internals), `StampedLock` | Deloitte, TechM, Amex | 🔴 |
| 6 | `volatile` (visibility + ordering, **not atomicity**); is a volatile counter thread-safe? (No); `volatile` vs Atomic classes | 🔥 Acc, Bravura, HCL, Infosys, Amex | 🟡 |
| 7 | Java Memory Model, **happens-before**, memory visibility | 🔥 Airtel, Cognizant, EPAM, Flipkart, JPM, Optum, TechM, Misc | 🔴 |
| 8 | Deadlock – cause, prevention (lock ordering, tryLock w/ timeout), detection via thread dump; livelock, starvation, race condition | 🔥 Acc, CTS, HCL, Infosys, Google, PwC, EY, Misc | 🟡 |
| 9 | **ExecutorService** – types of pools, `execute` vs `submit`, `Runnable` vs `Callable`, `Future`, shutdown vs shutdownNow, `RejectedExecutionException`, queue full behaviour, choosing pool size (CPU-bound = cores, IO-bound = cores × (1 + wait/compute)) | 🔥 Bravura, Bitwise, CTS, Deloitte, EY, Google, Synchron, Wells Fargo, Misc | 🟡 |
| 10 | **CompletableFuture** – vs Future, vs ExecutorService, default pool (`ForkJoinPool.commonPool()`), `thenApply/thenCompose/thenCombine`, `allOf`, `exceptionally/handle`, run two independent API calls in parallel | 🔥 Amazon, Acc, Barclays, Birlasoft, Bravura, Deloitte, EY, Flipkart, Google, NTT, Optum, WF, Misc | 🟡 |
| 11 | ForkJoinPool & work stealing; parallel streams – when they help/hurt | Amex, Optum, Oracle, Virtuasa, Citi, Misc | 🔴 |
| 12 | **Virtual threads (Project Loom)** – how they raise throughput (blocking IO unmounts carrier), vs platform threads, when NOT to use (CPU-bound, pinned `synchronized`) | 🔥 Airtel, Amazon, EY, Optum, TCS, TechM, Misc | 🔴 |
| 13 | Producer–Consumer (BlockingQueue / wait-notify) | Acc, Synchron | 🟡 |
| 14 | Print odd/even with two threads | CTS | 🟡 |
| 15 | Design a custom thread pool | EPAM | 🔴 |
| 16 | Thread pool: 1000 tasks, 10 concurrent, retry + graceful shutdown | Deloitte | 🔴 |
| 17 | `ThreadLocal` memory leak (thread pools) & fix (`remove()`) | Optum | 🔴 |
| 18 | `Semaphore`, `CountDownLatch`, `CyclicBarrier` use cases | Optum, Wissen | 🟡 |
| 19 | False sharing in low-latency systems (`@Contended`, padding) | Virtuasa | 🔴 |
| 20 | Daemon thread | Misc | 🟢 |
| 21 | `synchronized` instance vs static method locks – output of Wissen puzzle (below) | Wissen | 🔴 |
| 22 | How to guarantee an account never goes negative under 100 concurrent withdrawals; two threads update same balance; deadlock-free transfer between two accounts | PwC, Flipkart (overselling) | 🔴 |
| 23 | Make a class thread-safe (real scenario) | Misc | 🟡 |
| 24 | Reduce latency when API calls multiple independent downstream services (parallel via CompletableFuture) | Oracle | 🟡 |
| 25 | Threads vs Processes; parallel processing in Java | MC | 🟢 |
| 26 | 1000 users hit same API – how use multiple threads; DB connection pool with 100 users | Bravura | 🟡 |

### Key points

- **Pool size**: CPU-bound ≈ N cores (+1); IO-bound ≈ N × (1 + W/C). Prefer bounded `ThreadPoolExecutor` (custom `ArrayBlockingQueue` + `CallerRunsPolicy`) over `Executors.newFixedThreadPool` (unbounded queue → OOM).
- **Queue full** in `ThreadPoolExecutor`: tasks go queue → grow to `maxPoolSize` → rejection policy (`Abort` default → `RejectedExecutionException`).
- **CompletableFuture default pool** = common ForkJoinPool (size cores-1) → pass your own executor for blocking IO.
- **Happens-before**: unlock→lock of same monitor, volatile write→read, `Thread.start()`→thread actions, thread end→`join()`.
- **Virtual threads**: `Thread.ofVirtual().start(r)` / `Executors.newVirtualThreadPerTaskExecutor()`. Don't pool them; avoid `synchronized` pinning (use `ReentrantLock`).
- **Deadlock detection**: `jstack <pid>` / `jcmd <pid> Thread.print` → "Found one Java-level deadlock"; or `ThreadMXBean.findDeadlockedThreads()`.

**Wissen puzzle** – `Task1: resource.test1()` (locks `resource` instance, sleeps forever) then `Task2: Resource.test2()` (locks `Resource.class`, sleeps forever) → both threads block on unbounded `sleep`; *not* a classic deadlock because the monitors (instance vs class) are independent. Both print "Inside Test1/Test2" and hang.

**Parallel two API calls**
```java
CompletableFuture<User>  u = CompletableFuture.supplyAsync(() -> userClient.get(id), ioPool);
CompletableFuture<Order> o = CompletableFuture.supplyAsync(() -> orderClient.get(id), ioPool);
Result r = u.thenCombine(o, Result::new)
            .exceptionally(ex -> Result.fallback())   // or handle((v, ex) -> ...)
            .orTimeout(2, TimeUnit.SECONDS)
            .join();
```

**Producer–consumer with BlockingQueue**
```java
BlockingQueue<Integer> q = new ArrayBlockingQueue<>(10);
Thread producer = new Thread(() -> { try { for (int i = 0; i < 100; i++) q.put(i); q.put(-1); } catch (InterruptedException e) { Thread.currentThread().interrupt(); } });
Thread consumer = new Thread(() -> { try { for (int v; (v = q.take()) != -1; ) System.out.println(v); } catch (InterruptedException e) { Thread.currentThread().interrupt(); } });
producer.start(); consumer.start();
```

**Odd/even printing (two threads, one lock)**
```java
class OddEven {
    private int n = 1; private final int max = 20;
    synchronized void print(boolean odd) throws InterruptedException {
        while (n <= max) {
            if ((n % 2 == 1) != odd) { wait(); continue; }
            System.out.println(Thread.currentThread().getName() + ": " + n++);
            notifyAll();
        }
    }
}
// new Thread(() -> oe.print(true)) , new Thread(() -> oe.print(false))
```

**Thread-safe withdraw (no negative balance)**
```java
class Account {
    private final AtomicLong balance = new AtomicLong(1000);
    boolean withdraw(long amt) {
        long cur;
        do { cur = balance.get(); if (cur < amt) return false; }
        while (!balance.compareAndSet(cur, cur - amt));   // lock-free; DB version: UPDATE ... WHERE balance >= ?
        return true;
    }
}
// transfer(a,b): lock accounts in a global order (by id) to avoid deadlock.
```

➡️ **Follow-ups**: Why does `i++` on a volatile fail? What does `synchronized` guarantee besides mutual exclusion? Fair vs non-fair lock? What happens to uncaught exception in pool thread? `submit` vs `execute` exception handling? How does `ConcurrentHashMap` avoid locking reads? How to gracefully shut down (`shutdown` + `awaitTermination` + `shutdownNow`)? Difference between `Executor`, `ExecutorService`, `Executors`?

---

## 4. Java 8+ Streams, Lambdas & Optional

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | Java 8 features overview (lambda, functional interfaces, streams, Optional, default/static interface methods, method refs, `java.time`) | 🔥 Acc, Cap, CTS, Deloitte, EPAM, Infosys, Charter Global, Logixal, Optum | 🟢 |
| 2 | `map()` vs `flatMap()` vs `filter()` | 🔥 ACL, Acc, Barclays, Cap, CTS, Deloitte, Wells Fargo | 🟢🟡 |
| 3 | Functional interfaces: `Predicate`, `Consumer`, `Supplier`, `Function`, `BiFunction`; is `@FunctionalInterface` mandatory; write predicate + consumer; random 1–100 via `Supplier`; Consumer vs Supplier | 🔥 Acc, Alti, Bravura, CTS, IntraEdge, Infosys, Deloitte | 🟢 |
| 4 | Intermediate vs terminal operations; lazy evaluation; `peek()`; how Streams work internally; a stream can be consumed **once** (`IllegalStateException`) | 🔥 Bitwise, Deloitte, NavajNa, TCS, EPAM | 🟡 |
| 5 | `Stream` vs `Collection`; `reduce()` vs `collect()`; `stream()` vs `parallelStream()`; when Streams add overhead | EPAM, WF, Citi, Virtuasa | 🟡 |
| 6 | Method references; default & static interface methods and why introduced; private interface methods | Cap, CTS, Bravura | 🟢 |
| 7 | `Optional` – purpose, methods, `isPresent()` vs `ifPresent()`, **`orElse` vs `orElseGet`**, misuse (fields/params), create Optional of an employee | 🔥 ACL, Acc, Barclays, Cap, Charter Global, Deloitte, Logixal, Nagaro, Optum, Virtuasa | 🟢🟡 |
| 8 | Using non-thread-safe collection with Stream; Stream pitfalls with parallel (shared state) | Bitwise, Virtuasa | 🔴 |
| 9 | Java 17/21 features (records, sealed, text blocks, switch expr., pattern matching, virtual threads) | see §1 | 🟡 |

### 🧑‍💻 Stream coding problems asked (with solutions)

Common model:
```java
record Employee(int id, String name, String dept, double salary, int age) {}
```

| # | Problem | Companies |
|---|---|---|
| S1 | Group employees by department | 🔥 Acc, Airtel, Alti |
| S2 | Count employees per department | 🔥 Alti, Bravura |
| S3 | Average & total salary; filter by salary/department | 🔥 ACL, Airtel |
| S4 | Highest-paid employee per department | Acc |
| S5 | **Second-highest salary** (distinct, handle duplicates) overall | 🔥 Cap, Alti |
| S6 | **2nd highest salary per department** | 🔥 Cap, EY, TechM |
| S7 | Top 3 highest-paid per department | Oracle |
| S8 | Youngest employee (name, age) per department | Alti |
| S9 | Character frequency / word frequency (case-insensitive) / fruit counts | 🔥 Cap, Honey Bee, Infosys, TCS |
| S10 | Second character of each String; square elements; reverse list; concatenate strings | Bajaj, Bravura, Infosys |
| S11 | Distinct skills of certified trainers → "Java, Spring Boot, Kafka" | EPAM |
| S12 | "I love Java" → `#ILoveJava` | EPAM |
| S13 | Anagrams using streams | EPAM |
| S14 | Total transaction amount per customer, sorted desc; top 3 clients | NavajNa, Wissen |
| S15 | Sort odds first then evens, each sorted; remove ≤0 using `partitioningBy`; reverse order distinct odd first then even | CTS, Deloitte |
| S16 | Sort `Person` by age asc; salary hike 10 % for joined after 2024 | Cap, Misc |
| S17 | Remove odds → multiply → sum | JPM |
| S18 | Missing numbers in sequence; second duplicate element | CTS, Birlasoft |
| S19 | 3rd highest salary with streams | Misc |
| S20 | Reverse a string using streams (no StringBuilder) | TCS |
| S21 | Final balance per account from `A:+100, B:+200, A:-50 …` using `Map.merge` | EY |

```java
// S1 / S2
Map<String, List<Employee>> byDept = emps.stream().collect(Collectors.groupingBy(Employee::dept));
Map<String, Long> countByDept = emps.stream().collect(Collectors.groupingBy(Employee::dept, Collectors.counting()));

// S3
double avg   = emps.stream().mapToDouble(Employee::salary).average().orElse(0);
double total = emps.stream().mapToDouble(Employee::salary).sum();

// S4 highest paid per dept
Map<String, Optional<Employee>> top = emps.stream().collect(
    Collectors.groupingBy(Employee::dept, Collectors.maxBy(Comparator.comparingDouble(Employee::salary))));

// S5 2nd highest distinct salary overall
Optional<Double> second = emps.stream().map(Employee::salary).distinct()
    .sorted(Comparator.reverseOrder()).skip(1).findFirst();

// S6 2nd highest per department
Map<String, Optional<Employee>> secondByDept = emps.stream().collect(
    Collectors.groupingBy(Employee::dept, Collectors.collectingAndThen(Collectors.toList(),
        l -> l.stream().sorted(Comparator.comparingDouble(Employee::salary).reversed()).skip(1).findFirst())));

// S7 top 3 per dept
Map<String, List<Employee>> top3 = emps.stream().collect(
    Collectors.groupingBy(Employee::dept, Collectors.collectingAndThen(Collectors.toList(),
        l -> l.stream().sorted(Comparator.comparingDouble(Employee::salary).reversed()).limit(3).toList())));

// S8 youngest per dept
Map<String, Optional<Employee>> youngest = emps.stream().collect(
    Collectors.groupingBy(Employee::dept, Collectors.minBy(Comparator.comparingInt(Employee::age))));

// S9 char frequency / word frequency (case-insensitive)
Map<Character, Long> cf = "hello".chars().mapToObj(c -> (char) c)
    .collect(Collectors.groupingBy(Function.identity(), LinkedHashMap::new, Collectors.counting()));
Map<String, Long> wf = Arrays.stream("The new the NEW".toLowerCase().split("\\s+"))
    .collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));

// S10
List<Character> second = Stream.of("bob", "AI", "Happy").map(s -> s.charAt(1)).toList();

// S11 / S12
String skills = trainers.stream().filter(Trainer::isCertified).map(Trainer::getSkill).distinct().collect(Collectors.joining(", "));
String tag = "#" + Arrays.stream("I love Java".split(" ")).collect(Collectors.joining());   // #ILoveJava

// S13 group anagrams
Map<String, List<String>> anagrams = words.stream().collect(Collectors.groupingBy(w -> {
    char[] c = w.toCharArray(); Arrays.sort(c); return new String(c); }));

// S14 total per customer, desc; top-3
Map<String, Double> totals = txns.stream().collect(Collectors.groupingBy(Txn::customer, Collectors.summingDouble(Txn::amount)));
List<Map.Entry<String, Double>> top3c = totals.entrySet().stream()
    .sorted(Map.Entry.<String, Double>comparingByValue().reversed()).limit(3).toList();

// S15 odd first (sorted) then even (sorted)
List<Integer> r = nums.stream().sorted(Comparator.comparing((Integer n) -> n % 2 == 0).thenComparing(Comparator.naturalOrder())).toList();
// remove <= 0 using partitioningBy
List<Integer> positives = nums.stream().collect(Collectors.partitioningBy(n -> n > 0)).get(true);

// S20 reverse a string with streams
String rev = IntStream.range(0, s.length()).mapToObj(i -> String.valueOf(s.charAt(s.length() - 1 - i))).collect(Collectors.joining());

// S21 balances
Map<String, Integer> bal = new HashMap<>();
for (String t : txns) { String[] p = t.split(":"); bal.merge(p[0], Integer.parseInt(p[1]), Integer::sum); }
```

**Wissen "top-3 clients" model solution** (records + Optional parsing + ignore malformed/FAILED):
```java
record Txn(String client, long amount) {}
static Optional<Txn> parse(String line) {
    try {
        String[] p = line.split("\\|");
        if (p.length != 4 || !"SUCCESS".equals(p[3])) return Optional.empty();
        return Optional.of(new Txn(p[0], Long.parseLong(p[2])));
    } catch (NumberFormatException e) { return Optional.empty(); }   // "INVALID" amount ignored
}
Map<String, Long> totals = lines.stream().map(Main::parse).flatMap(Optional::stream)
    .collect(Collectors.groupingBy(Txn::client, Collectors.summingLong(Txn::amount)));
List<String> top3 = totals.entrySet().stream()
    .sorted(Map.Entry.<String, Long>comparingByValue().reversed()).limit(3).map(Map.Entry::getKey).toList();
```

### Key points / follow-ups
- `orElse(x)` always evaluates `x`; `orElseGet(supplier)` evaluates lazily → use `orElseGet` for expensive/side-effect defaults.
- `isPresent()` returns boolean; `ifPresent(consumer)` runs an action. Prefer `map/flatMap/orElseThrow` over `isPresent()+get()`.
- Why is `distinct()` needed? How are `null`/duplicate values handled? (`Collectors.toMap` throws on duplicate keys – supply merge function.)
- `parallelStream` degrades with small data, shared mutable state, blocking ops, boxing, common-pool contention (Virtuasa, Oracle).
- `flatMap` for `List<List<T>>` → `Stream<T>`; `Optional::stream` to drop empties.

---

## 5. JVM, Memory Management & Garbage Collection

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | JVM architecture / complete lifecycle: ClassLoader → runtime data areas → execution engine (interpreter, **JIT**) → GC; what if Java had no GC | 🔥 Acc, Comviva, Deloitte, Birlasoft, Misc | 🟡 |
| 2 | Memory areas: Heap (Young: Eden/S0/S1, Old), Stack, Metaspace, Method Area, PC Register, native stack; heap vs stack | 🔥 Alti, Birlasoft, Deloitte, EY, Flipkart, TechM, Misc | 🟡 |
| 3 | What happens in JVM for `int x=10; Employee e = new Employee();` – where do primitives/objects live, what happens after method returns (frame popped; object becomes eligible for GC) | Flipkart | 🟡 |
| 4 | How stack memory is cleared; Metaspace (replaced PermGen, native memory) | Alti | 🟡 |
| 5 | Garbage collection basics, algorithms (Mark-Sweep-Compact, Copying, generational); `finalize()` purpose | 🔥 Alti, Deloitte, Cap, EPAM, JPM, MC, Birlasoft | 🟡 |
| 6 | **G1 GC** – regions, remembered sets, mixed collections, pause-time goal; why better than CMS for large heaps | 🔥 Optum, Misc | 🔴 |
| 7 | GC improvements in Java 8 vs Java 17 (G1 default, ZGC/Shenandoah low pause) | Bitwise, Cap | 🔴 |
| 8 | Frequent GC pauses – how to optimise; how JVM GC pauses show in production | EY, Deloitte | 🔴 |
| 9 | **Memory leak**: how to detect (heap dump, MAT, VisualVM, JFR), common causes (static collections, ThreadLocal, unclosed resources, listeners, caches w/o eviction), how to confirm even when GC runs normally | 🔥 Airtel, Bajaj, EY, Misc, PwC, Optum | 🔴 |
| 10 | **OutOfMemoryError** in production – types (heap, metaspace, GC overhead, unable to create native thread), steps, tools | 🔥 Bitwise, EY, Google, PwC, Misc | 🔴 |
| 11 | Heap dump vs thread dump; `jmap`, `jstack`, `jcmd`, JFR; how incorrect cache config causes OOM | PwC, JPM | 🔴 |
| 12 | JVM tuning for a high-throughput checkout service (heap sizing, GC choice, pause targets, `-XX:MaxRAMPercentage` in containers) | Flipkart | 🔴 |
| 13 | String pool location (heap since Java 7), `intern()` | Optum, EY, i-exceed | 🟡 |
| 14 | Class loading, classloader hierarchy (Bootstrap/Platform/Application), `Class.forName` | Misc, PayPal | 🟡 |
| 15 | Memory allocation for static / final / static-final variables | Optum | 🟡 |
| 16 | High CPU with low traffic; application slows after hours; service randomly unresponsive; crash with no error | EY, Misc | 🔴 |
| 17 | Which tool for performance check when app goes down | Virtuasa | 🟡 |

### Key points

- **Young GC (minor)**: Eden → Survivor (copy); objects age → promoted to Old. **Full GC** = stop-the-world compaction of whole heap.
- **G1**: heap split in equal regions; evacuates regions with most garbage first (garbage-first); concurrent marking; tune `-XX:MaxGCPauseMillis`.
- **ZGC / Shenandoah**: concurrent compaction, sub-ms pauses.
- **Leak analysis flow**: confirm with GC logs (old-gen post-GC floor keeps rising) → `jcmd <pid> GC.heap_dump` / `-XX:+HeapDumpOnOutOfMemoryError` → open in **Eclipse MAT** → dominator tree / leak suspects → trace GC roots.
- **High CPU + low traffic** → `top -H` to find hot thread → convert TID to hex → match in `jstack` → look for busy loops, GC threads, regex backtracking, JIT.
- Container tip: use `-XX:MaxRAMPercentage=75`; OOMKilled in K8s ≠ Java OOM (check `kubectl describe pod`).

➡️ **Follow-ups**: What's in a thread dump for BLOCKED threads? Difference between `OutOfMemoryError: Metaspace` and Java heap space? Why Strings in pool were moved to heap? What is escape analysis? How do you size young vs old gen?

---

## 6. Spring & Spring Boot Internals

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | Spring vs Spring Boot (and vs JPA/Hibernate); why Spring Boot; features you use daily | 🔥 Acc, Alti, Bajaj, Mastercard, Optum, Misc, JPM, Cap, CTS, HCL | 🟢 |
| 2 | **`@SpringBootApplication`** = `@Configuration` + `@EnableAutoConfiguration` + `@ComponentScan`; startup flow (`SpringApplication.run`, context refresh, embedded Tomcat) | 🔥 Alti, Birlasoft, Cap, CTS, Acc, Bravura, Infosys, Logixal, Optum | 🟡 |
| 3 | **Auto-configuration** – `spring.factories`/`AutoConfiguration.imports`, `@Conditional*` (`@ConditionalOnClass/Property/MissingBean`), how starters work, exclude an auto-config, `SpringFactoriesLoader`; what `spring-boot-starter-web` adds | 🔥 Airtel, Acc, HCL, WF, Infosys, Misc | 🔴 |
| 4 | DI / IoC: types (constructor/setter/field), **constructor vs field injection** (immutability, testing, circular detection), `@Autowired` internals, IoC vs DI | 🔥 Acc, Amazon, Barclays, CTS, Deloitte, IntraEdge, Misc, Tata Nexarc | 🟡 |
| 5 | `@Component` vs `@Service` vs `@Repository` vs `@Controller`; `@Repository` exception translation; what if two stereotypes on one class; interchange them | 🔥 Acc, Airtel, Birlasoft, Bravura, Charter Global, Deloitte, Hughes, Infosys, Misc, Tata Nexarc | 🟢🟡 |
| 6 | `@Component` vs `@Bean` vs `@Configuration` (full vs lite mode/CGLIB) | Amex, Deloitte, Misc | 🟡 |
| 7 | `@Controller` vs `@RestController` vs `@ControllerAdvice` | 🔥 Acc, Synchron, Tata Nexarc | 🟢 |
| 8 | `@Qualifier` vs `@Primary`; multiple beans of the same type; same bean name | 🔥 ACL, Barclays, Bajaj, Bitwise, Infosys, NavajNa, Deloitte | 🟡 |
| 9 | **Bean lifecycle** (instantiate → populate → Aware → `BeanPostProcessor.before` → `@PostConstruct`/`InitializingBean` → `BPP.after` (proxies) → ready → `@PreDestroy`) | 🔥 Barclays, Bravura, Deloitte, EPAM, Infosys, Optum, MC, Misc, NavajNa | 🟡 |
| 10 | **Bean scopes** – singleton, prototype, request, session, application, websocket; singleton injecting prototype (use `ObjectProvider`/`@Lookup`/scoped proxy); singleton thread-safety | 🔥 Honey Bee, Hughes, EY, Acc, Deloitte, NavajNa | 🟡 |
| 11 | **Circular dependency** – how Spring resolves (3-level cache, setter/field only), constructor cycles fail; how to fix (`@Lazy`, redesign, event, setter) | 🔥 ACL, Bravura, Deloitte, NavajNa, Optum, Misc | 🟡🔴 |
| 12 | BeanFactory vs ApplicationContext | 🔥 Amex, Bitwise, Honey Bee | 🟡 |
| 13 | **`@Transactional`** – how it works (AOP proxy, TransactionManager), what is rolled back (only unchecked by default; `rollbackFor`), propagation (REQUIRED, REQUIRES_NEW, NESTED, …), isolation, **self-invocation** problem, private method, exception swallowed | 🔥🔥 Acc, Airtel, Amazon, Barclays, Bitwise, Charter Global, Comviva, CTS, Datatex, Delhivery, Deloitte, EPAM, Hughes, JPM, MC, Oracle, PwC, TechM, WF, Misc (20+) | 🟡🔴 |
| 15 | Global exception handling (`@ControllerAdvice` + `@ExceptionHandler`, `ResponseEntityExceptionHandler`, `ProblemDetail`) | 🔥 Acc, Alti, Bravura, Cap, EPAM, HCL, Nagaro, NTT, Synchron, Wissen | 🟢🟡 |
| 16 | **Filter vs Interceptor vs AOP** (servlet vs MVC vs proxy-level; order; use cases); AOP concepts & where you used it | 🔥 Alti, Amex, Bajaj, Deloitte, EPAM | 🟡 |
| 17 | Spring MVC request flow (DispatcherServlet → HandlerMapping → Controller → ViewResolver/HttpMessageConverter); how `@RequestBody` works internally; how Spring picks GET/POST handler; what happens when you hit a REST URL | Airtel, Alti, EY, Logixal, Infosys | 🟡 |
| 18 | `@RequestParam` vs `@PathVariable`; `@RequestBody`; POST vs PUT vs PATCH | Acc, Barclays, Flipkart, Infosys | 🟢 |
| 19 | Profiles (`@Profile`, `spring.profiles.active`), externalised config, `@Value`, `@ConfigurationProperties` (nested binding), `.properties` vs `.yml`, both present – precedence, override defaults | 🔥 Barclays, Deloitte, Hughes, NTT, TCS, Infosys, Misc | 🟡 |
| 20 | Actuator, health checks (liveness/readiness), securing `/actuator`, smoke tests | HCL, Optum, IntraEdge, Infosys | 🟡 |
| 21 | Multiple data sources in one app (two `DataSource`/`EntityManagerFactory`/`TransactionManager` beans, `@Primary`) | 🔥 Amex, Optum, Synchron, TechM | 🟡 |
| 22 | `@Async`, `@Scheduled` scheduling, Spring events, customise startup with application events | Bitwise, Infosys, PayPal, Misc | 🟡 |
| 23 | Spring Cache (`@Cacheable`, `@CacheEvict`, `@CachePut`), stale cache | Bitwise, NavajNa, Optum | 🟡 |
| 24 | Pagination, sorting & filtering (`Pageable`, `PageRequest`); how DB knows to fetch only 10 rows (`LIMIT/OFFSET`) ; cursor/keyset for 100 M rows | 🔥 Acc, HCL, EY, Infosys, TechM | 🟡🔴 |
| 25 | Calling another service – `RestTemplate` vs `WebClient` vs `HttpClient` vs Feign; headers; flow | 🔥 Cap, IntraEdge, Logixal, Misc, PhonePe, i-exceed | 🟡 |
| 26 | Request validation (`@Valid`, Bean Validation, cross-field validators); correlation IDs; masking sensitive logs | Bravura, PayPal, Nagaro | 🟡 |
| 27 | Testing: `@SpringBootTest` vs `@WebMvcTest`, Mockito `@Mock` vs `@Spy` vs `@MockBean`, Testcontainers, BDD/TDD, JUnit version, code coverage, SonarQube | 🔥 Bitwise, IntraEdge, Nagaro, Cap, ACL, Citi, Deloitte | 🟡 |
| 28 | REST API design: versioning, HATEOAS, HTTP status codes (200/201/400/401/403/404/500/503), REST vs SOAP, idempotency, CORS, Swagger/OpenAPI | 🔥 Acc, Bajaj, Cap, CTS, Alti, Infosys, JPM | 🟡 |
| 29 | Spring Data: `CrudRepository` vs `JpaRepository`, `save` vs `saveAll` vs `saveAndFlush`, SessionFactory vs EntityManager, Spring Data JPA vs JDBC | 🔥 Acc, Infosys, MC, Tata Nexarc | 🟡 |
| 30 | Migrations: Liquibase/Flyway | Acc, Misc | 🟡 |
| 31 | How to reduce XML configuration; can Spring create a bean for an abstract class; `@Autowired` on constructor; exclude configuration | Misc, Acc, Infosys | 🟡 |
| 32 | Spring Cloud: Eureka, Config Server, Gateway, LoadBalancer | Comviva, Nagaro, Capgemini | 🟡 |
| 33 | Spring AI / RAG chatbot | WF, Misc | 🔴 |
| 34 | Maven lifecycle (`clean/validate/compile/test/package/verify/install/deploy`), `<distributionManagement>`, dependency vs artifact, BOM/dependency versions | Barclays, Bravura, Logixal, Infosys | 🟢 |
| 35 | HikariCP / connection pooling – why, tuning, behaviour when exhausted | Charter Global, Bravura, Misc | 🟡 |

### Key points

**@Transactional pitfalls (single most repeated Spring question):**
1. **Proxy-based** → calling a `@Transactional` method from another method *of the same class* bypasses the proxy (self-invocation) → no transaction. Fix: move to another bean, inject self, or use AspectJ mode.
2. Only **public** methods (proxy) are advised.
3. Default rollback: **RuntimeException & Error**. Checked exceptions (e.g. `IOException`) **don't** roll back unless `rollbackFor = Exception.class`.
4. Swallowing exceptions in `try/catch` → no rollback.
5. `REQUIRES_NEW` suspends the outer tx; `NESTED` uses savepoints; `REQUIRED` (default) joins existing.
6. Within the same transaction, a `save()` then `find` returns the updated value (first-level cache / flush before query) – Misc question.
7. Different thread (`@Async`) = different transaction.

**Bean lifecycle one-liner**: Instantiate → inject → `BeanNameAware/BeanFactoryAware/ApplicationContextAware` → `BPP.postProcessBeforeInitialization` → `@PostConstruct` → `afterPropertiesSet` → `init-method` → `BPP.postProcessAfterInitialization` (AOP proxy created here) → use → `@PreDestroy` → `destroy()`.

**Circular dependency** – singleton setter/field injection works via early references (3-level cache: `singletonObjects`, `earlySingletonObjects`, `singletonFactories`); constructor injection fails with `BeanCurrentlyInCreationException`; Spring Boot 2.6+ prohibits by default (`spring.main.allow-circular-references`).

**Filter vs Interceptor vs AOP**: Filter = servlet container, before DispatcherServlet (auth, CORS, logging raw request); Interceptor = Spring MVC (`preHandle/postHandle/afterCompletion`, knows handler); AOP = method-level, any bean (transactions, auditing, metrics).

**Multiple beans of same type** → `NoUniqueBeanDefinitionException` → use `@Primary`, `@Qualifier("name")`, inject `List<Interface>`/`Map<String,Interface>` (Strategy pattern).

**Singleton thread-safety** – singletons are shared; storing request-specific data in a field of a service is a bug (race). Keep beans stateless.

**Multiple datasources sketch**
```java
@Configuration
@EnableJpaRepositories(basePackages = "com.app.orders", entityManagerFactoryRef = "ordersEmf", transactionManagerRef = "ordersTm")
class OrdersDbConfig {
    @Primary @Bean @ConfigurationProperties("spring.datasource.orders")
    DataSource ordersDs() { return DataSourceBuilder.create().build(); }
    @Primary @Bean LocalContainerEntityManagerFactoryBean ordersEmf(EntityManagerFactoryBuilder b, @Qualifier("ordersDs") DataSource ds) {
        return b.dataSource(ds).packages("com.app.orders.entity").persistenceUnit("orders").build();
    }
    @Primary @Bean PlatformTransactionManager ordersTm(@Qualifier("ordersEmf") EntityManagerFactory emf) { return new JpaTransactionManager(emf); }
}
```

**Global exception handler**
```java
@RestControllerAdvice
class GlobalExceptionHandler {
    @ExceptionHandler(ResourceNotFoundException.class)
    ResponseEntity<ApiError> notFound(ResourceNotFoundException ex) { return ResponseEntity.status(404).body(new ApiError("NOT_FOUND", ex.getMessage())); }
    @ExceptionHandler(MethodArgumentNotValidException.class)
    ResponseEntity<ApiError> invalid(MethodArgumentNotValidException ex) { return ResponseEntity.badRequest().body(ApiError.from(ex)); }
    @ExceptionHandler(Exception.class)
    ResponseEntity<ApiError> generic(Exception ex) { return ResponseEntity.status(500).body(new ApiError("INTERNAL_ERROR", "Something went wrong")); }
}
```

**MVC flow task (Airtel)** – `POST /plans/deactivate {mobileNumber, planId}` → Controller (validates, delegates) → Service interface + `ServiceImpl` (`@Transactional`: find `CustomerPlan` by mobile+planId, else throw `NotFound`; set `Customer.active=false`) → Repository (`JpaRepository`) ; return 200/404.

**Password-save task (IntraEdge)** – `POST /users` (creation → POST, not PUT: PUT is idempotent full-replace); `BCryptPasswordEncoder.encode(raw)` (adaptive, salted one-way hash; never plain text / never reversible encryption).

➡️ **Follow-ups**: Why constructor injection? How does `@Autowired` resolve (by type → qualifier → name)? Where is the proxy created (JDK vs CGLIB)? What if `@Service` + `@Repository` both on a class (works; both are `@Component`, but exception-translation post-processor applies)? How to debug `@Transactional` not working in prod (check proxy, `TransactionSynchronizationManager.isActualTransactionActive()`, debug `org.springframework.transaction` logs)? Where does Spring Boot decide embedded Tomcat (`ServletWebServerFactoryAutoConfiguration`, classpath detection)?

---

## 7. Spring Security, JWT & OAuth

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | Authentication vs Authorization (+ 401 vs 403; which comes first); IDOR | 🔥 Acc, Akamai, Bajaj, CTS, Deloitte, Infosys, MC, Tech M, Misc | 🟢 |
| 2 | **JWT** – structure (header.payload.signature), claims, validation flow, where stored, why needed, how used in project | 🔥 Acc, Barclays, CTS, Deloitte, EPAM, EY, i-exceed, Infosys, TechM, Misc | 🟡 |
| 3 | Access token vs **refresh token**; refresh once & retry concurrent failed requests; token expiry design | 🔥 Acc, Deloitte, i-exceed, EY | 🟡🔴 |
| 4 | **Spring Security filter chain** – `SecurityFilterChain`, `UsernamePasswordAuthenticationFilter`, `AuthenticationManager`, `AuthenticationProvider`, `UserDetailsService`, `SecurityContextHolder`, `OncePerRequestFilter` for JWT | 🔥 Acc, Barclays, Optum, TechM, MC, Altimetrik | 🟡 |
| 5 | OAuth 2.0 vs JWT vs OpenID Connect; OAuth vs OAuth 2.0; grant types; scopes | 🔥 Alti, EY, Misc, TechM | 🟡 |
| 6 | Securing microservices: gateway auth, propagating tokens, service-to-service (client-credentials, mTLS), securing 100+ services, payload integrity, TLS vs mTLS, TLS handshake & certificates | 🔥 Akamai, Bravura, EPAM, EY, MC, TechM, Misc | 🔴 |
| 7 | Password storage: hashing vs encryption, BCrypt, why not plain text, RSA use | IntraEdge, TechM | 🟡 |
| 8 | CSRF – what & how protected (stateless JWT APIs usually disable); CORS purpose; OWASP top risks | Deloitte, TechM, Bajaj | 🟡 |
| 9 | `@PreAuthorize` / `@PostAuthorize`, RBAC | TechM, CTS | 🟡 |
| 10 | JWT valid but user's role changed in DB – avoid stale permissions (short TTL, token versioning, revocation list / introspection) | TechM | 🔴 |
| 11 | Frontend sends role in browser – prevent tampering (never trust client; enforce server-side from token/DB) ; attach token via interceptor only to own API | Acc | 🟡 |
| 12 | Secrets mgmt: no passwords in `application.properties` (Vault, AWS Secrets Manager/SSM, env, K8s secrets, Jasypt) ; store user creds in AWS | TechM, Infosys, Synchron, HiperBrain | 🟡 |
| 13 | Secure the actuator/health endpoint; debug 401 vs 404 | Infosys, EY | 🟡 |
| 14 | MongoDB security measures before insert (validation/NoSQL injection) ; REST API validity when service-to-service data tampered | Bravura | 🟡 |

### Key points

**JWT flow (Spring Security):** client `POST /login` → `AuthenticationManager.authenticate()` → `UserDetailsService` + `PasswordEncoder` → on success sign JWT (`HS256` secret or `RS256` private key) with `sub`, `roles`, `iat`, `exp` → client sends `Authorization: Bearer <jwt>` → `JwtAuthFilter extends OncePerRequestFilter` verifies signature + expiry → builds `Authentication` → sets `SecurityContextHolder` → `@PreAuthorize`/`authorizeHttpRequests` enforce roles.

```java
@Bean
SecurityFilterChain chain(HttpSecurity http, JwtAuthFilter jwt) throws Exception {
    return http.csrf(c -> c.disable())
        .sessionManagement(s -> s.sessionCreationPolicy(SessionCreationPolicy.STATELESS))
        .authorizeHttpRequests(a -> a.requestMatchers("/auth/**").permitAll()
                                     .requestMatchers("/admin/**").hasRole("ADMIN")
                                     .anyRequest().authenticated())
        .addFilterBefore(jwt, UsernamePasswordAuthenticationFilter.class)
        .build();
}
```

- **401** = unauthenticated (no/invalid token); **403** = authenticated but not permitted. Authentication happens first → 401 before 403.
- **Refresh**: short-lived access token (5–15 min) + long-lived refresh token (stored httpOnly cookie / DB, rotated). Angular: single "refresh in progress" subject so parallel 401s wait and retry once.
- **JWT is signed, not encrypted** – don't put secrets in payload. Revocation needs a blacklist or short TTL.
- **OAuth2 vs JWT**: OAuth2 = authorization framework (roles: resource owner/client/auth server/resource server); JWT = token format. OIDC = identity layer on OAuth2 (ID token).
- **Inter-service**: client-credentials grant or mTLS; gateway validates the user token, downstream services re-validate (zero trust).
- **Encryption vs hashing**: encryption reversible with key; hashing one-way (use BCrypt/Argon2 with salt + work factor).

➡️ **Follow-ups**: Where do you store the JWT on the client (httpOnly cookie vs localStorage/XSS)? How to log out a JWT? How does `AuthenticationProvider` differ from `AuthenticationManager`? What is `SecurityContext` per-thread (ThreadLocal) implications with `@Async`? How to unit-test secured endpoints (`@WithMockUser`)?

---

## 8. Hibernate, JPA & SQL

### 8A. Hibernate / JPA

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | 🔥 **N+1 query problem** – detect (SQL logs, Hibernate statistics, p6spy), fix (`JOIN FETCH`, `@EntityGraph`, `@BatchSize`, DTO projection, `default_batch_fetch_size`) | Acc, Amazon, Birlasoft, Datatex, Deloitte, EPAM, EY, HCL, Infosys, NavajNa, Optum, TechM, UnClassified, Misc (15+) | 🟡 |
| 2 | Lazy vs eager fetch; **`LazyInitializationException`** – cause & fixes (fetch join, `@Transactional`, DTO, `Open-Session-In-View` trade-off) | 🔥 Acc, Barclays, Bajaj, CTS, HCL, NavajNa, Synchron, TechM | 🟡 |
| 3 | **Optimistic (`@Version`) vs pessimistic locking** (`SELECT … FOR UPDATE`), lost-update prevention (two users edit same record) | 🔥 Acc, Amex, Deloitte, EPAM, EY, NavajNa, Misc | 🟡🔴 |
| 4 | `save()` vs `saveAll()` vs `saveAndFlush()` vs `flush()`; `persist()` vs `merge()`; DB calls triggered | 🔥 Acc, HCL, Synchron, Tata Nexarc | 🟡 |
| 5 | Entity states (transient, persistent, detached, removed) & dirty checking | HCL, Synchron | 🟡 |
| 6 | First-level vs second-level cache (Ehcache), query cache; when it hurts | Deloitte, Misc | 🔴 |
| 7 | Mappings: `@OneToMany/@ManyToOne/@ManyToMany`, `mappedBy`, cascade, orphanRemoval, composite key (`@EmbeddedId`/`@IdClass`) | 🔥 HCL, Synchron, ACL, Misc | 🟡 |
| 8 | JPA vs Hibernate; SessionFactory vs EntityManager (Spring Data uses `EntityManager`) | Infosys, Bravura, Misc | 🟡 |
| 9 | Entity → table flow (JPA → Hibernate → SQL, `ddl-auto`); skip a field from persistence (`@Transient`) | Airtel, EPAM | 🟡 |
| 10 | Batch insert/update for large datasets (`hibernate.jdbc.batch_size`, `order_inserts`, avoid IDENTITY) | Synchron | 🔴 |
| 11 | Update 10 M rows safely in prod; archive millions of rows without disrupting prod; 5 lakh records efficiently | Deloitte, PayPal, Infosys | 🔴 |
| 12 | Custom JPA query by age & salary; max-age employee; JPA vs JDBC (Spring Data JDBC) | Logixal, Misc, MC | 🟡 |

### 8B. SQL & Database

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | 🔥 **Second / Nth highest salary** (`DENSE_RANK`, subquery, `LIMIT OFFSET`); 5th highest | Alti, Barclays, Bravura, CTS, EPAM, HCL, NavajNa, WF, Deloitte, Synchron | 🟢🟡 |
| 2 | Highest salary per department; avg salary per dept; count per dept; top-N per dept | Alti, Comviva, Deloitte, TechM, Bravura | 🟡 |
| 3 | Employees earning more than **manager** (self join); more than **average** | Deloitte, Bravura, Misc | 🟡 |
| 4 | Joins (INNER/LEFT/RIGHT/FULL), self join & use cases | 🔥 CTS, Airtel, EPAM, HCL, Infosys, Mphasis, WF, Misc | 🟢 |
| 5 | Indexing: how it works (B-tree), clustered vs non-clustered, composite index (column order), covering index, when not to index; design index for customer+date+sort | 🔥 Alti, ACL, Amex, Flipkart, Infosys, Mphasis, PayPal, EY, WF | 🟡🔴 |
| 6 | Primary vs unique vs composite key; when to use composite key | ACL, Bajaj, Infosys | 🟢 |
| 7 | `DELETE` vs `TRUNCATE` vs `DROP`; `UNION` vs `UNION ALL`; `RANK` vs `DENSE_RANK` vs `ROW_NUMBER`; SQL order of execution | CTS, Datatex, Deloitte | 🟢🟡 |
| 8 | ACID; isolation levels (dirty/non-repeatable/phantom reads); **MVCC**; PostgreSQL concurrency | 🔥 Bitwise, Delhivery, Flipkart, JPM, PwC, PayPal, Misc | 🟡🔴 |
| 9 | SQL vs NoSQL – when to use which; DB for fund transfer/banking | Delhivery, JPM, EY, Walmart | 🟡 |
| 10 | Stored procedures (when/why), views vs procedures, triggers, normalization | Infosys, Deloitte | 🟡 |
| 11 | Optimise slow query (EXPLAIN plan, indexes, avoid `SELECT *`, pagination), DB bottleneck, slow after DB growth | 🔥 HCL, Infosys, JPM, NavajNa, EY, Deloitte, WF | 🟡🔴 |
| 12 | Find duplicate rows/transactions; list tables & columns of a DB | JPM, PayPal, NavajNa | 🟡 |
| 13 | Orders in last 12 months for customers with ≥ 3 orders | Datatex | 🟡 |
| 14 | Department-wise count & total salary for ACTIVE employees sorted by total desc | Tata Nexarc | 🟡 |
| 15 | Top 5 customers by revenue per region; rank employees by experience | Deloitte | 🟡 |
| 16 | Sharding/partitioning of large tables; cursor-based pagination | Synchron, EY | 🔴 |
| 17 | Schema design: e-commerce ER, order management, ride-sharing, Cricbuzz | Infosys, Flipkart, JPM, Delhivery | 🟡 |
| 18 | Salary increment query; employee with NULL address → 'NA' (`COALESCE`) | i-exceed, Bravura | 🟢 |

### SQL solutions
```sql
-- 2nd / Nth highest salary (handles duplicates)
SELECT salary FROM (SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) rnk FROM employee) t WHERE rnk = 2;
SELECT MAX(salary) FROM employee WHERE salary < (SELECT MAX(salary) FROM employee);
SELECT DISTINCT salary FROM employee ORDER BY salary DESC LIMIT 1 OFFSET 4;   -- 5th highest

-- Highest paid per department
SELECT * FROM (SELECT e.*, RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC) r FROM employee e) t WHERE r = 1 ORDER BY dept_id;
-- 2nd highest per department
SELECT * FROM (SELECT e.*, DENSE_RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC) r FROM employee e) t WHERE r = 2;

-- Salary > average ; salary > manager's salary
SELECT * FROM employee WHERE salary > (SELECT AVG(salary) FROM employee);
SELECT e.* FROM employee e JOIN employee m ON e.manager_id = m.id WHERE e.salary > m.salary;

-- Dept-wise count and total salary for ACTIVE employees
SELECT d.dept_name, COUNT(*) emp_cnt, SUM(e.salary) total
FROM employee e JOIN department d ON d.id = e.dept_id
WHERE e.status = 'ACTIVE' GROUP BY d.dept_name ORDER BY total DESC;

-- Orders in last 12 months for customers having >= 3 orders (Datatex)
SELECT o.* FROM orders o
WHERE o.order_date >= CURRENT_DATE - INTERVAL '12 months'
  AND o.customer_id IN (SELECT customer_id FROM orders WHERE order_date >= CURRENT_DATE - INTERVAL '12 months'
                        GROUP BY customer_id HAVING COUNT(*) >= 3)
ORDER BY o.order_date DESC;

-- Duplicate rows
SELECT col1, col2, COUNT(*) FROM txn GROUP BY col1, col2 HAVING COUNT(*) > 1;

-- NULL address -> 'NA'
SELECT id, name, COALESCE(address, 'NA') AS address FROM employee;
```

### JPA snippets
```java
// N+1 fix
@Query("select d from Department d join fetch d.employees")
List<Department> findAllWithEmployees();
// or: @EntityGraph(attributePaths = "employees")  /  @BatchSize(size = 50)

// Optimistic locking
@Entity class Account { @Id Long id; @Version Long version; BigDecimal balance; }  // OptimisticLockException on conflict

// Pessimistic
@Lock(LockModeType.PESSIMISTIC_WRITE) @Query("select a from Account a where a.id = :id") Account lockById(Long id);

// Max age employee
Optional<Employee> findFirstByOrderByAgeDesc();
```

### Key points
- **Isolation levels**: READ_UNCOMMITTED → READ_COMMITTED (PG default) → REPEATABLE_READ (MySQL default) → SERIALIZABLE. **MVCC**: readers don't block writers via row versions/snapshots.
- **Composite index rule**: leftmost-prefix; for "filter by customer + date range, sorted by date" index `(customer_id, txn_date DESC)`; covering index includes all selected columns so table lookup is avoided.
- **Cursor/keyset pagination**: `WHERE (created_at, id) < (:lastCreated, :lastId) ORDER BY created_at DESC, id DESC LIMIT 50` – O(1) vs OFFSET O(n).
- **Safely update 10 M rows**: batches of N (1–10 k) in short transactions, indexed predicate, off-peak, throttle, monitor replication lag, idempotent resumable job, backups.
- **Archive without disruption**: partition by date + detach partition, or chunked `INSERT…SELECT` + `DELETE` with sleep.

➡️ **Follow-ups**: Why does `JOIN FETCH` + pagination warn (in-memory pagination, HHH000104)? Clustered index physical ordering? When does an index NOT get used (functions on column, leading wildcard, low selectivity)? Difference between `READ_COMMITTED` and `REPEATABLE_READ` anomalies? How does `@Version` generate SQL (`UPDATE … WHERE id=? AND version=?`)?

---

## 9. Microservices & System Design

### 9A. Microservices concepts & patterns

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | Monolith vs microservices – when each, drawbacks of both, why/when migrate, "distributed monolith" | 🔥 Alti, Bajaj, Cap, CTS, Delhivery, Flipkart, Infosys, Logixal, Walmart, EY, Mphasis | 🟢🟡 |
| 2 | **How microservices communicate** – REST/gRPC (sync) vs messaging (async), RestTemplate/WebClient/Feign/RabbitMQ/Kafka; sync vs async trade-offs; when REST vs Kafka | 🔥 Airtel, Bitwise, Deloitte, EY, Flipkart, HCL, Honey Bee, JPM, Mphasis, Phonepe, WF, Misc | 🟡 |
| 3 | **API Gateway** – role (routing, auth, rate limit, aggregation, SSL), design pattern associated, fault-tolerant gateway | 🔥 Airtel, EPAM, HCL, Infosys, Mastercard, Synchron, TCS, WF, Misc | 🟡 |
| 4 | **Service discovery** (Eureka), registration flow, client-side load-balancing, service A→B flow | 🔥 Cap, Comviva, HCL, JPM, TCS | 🟡 |
| 5 | **Circuit Breaker** (Resilience4j: states CLOSED/OPEN/HALF_OPEN, failure-rate threshold, sliding window, wait-duration, permitted calls in half-open); Retry (max attempts, backoff + jitter), Bulkhead, TimeLimiter, fallback; retry vs circuit breaker; troubleshooting breaker flapping | 🔥🔥 Airtel, Alti, Cap, Comviva, CTS, Deloitte, EPAM, EY, Google, HCL, Infosys, Mphasis, TCS, Misc, WF | 🟡🔴 |
| 6 | **Cascading failures** – timeouts, bulkhead, fallback, rate limiting, load shedding; microservice C unavailable – what happens to A,B | 🔥 Alti, CTS, EY, Flipkart, Google, Deloitte | 🔴 |
| 7 | **Saga pattern** (orchestration vs choreography, compensating transactions) – order/payment/inventory; fund-transfer saga; Saga vs 2PC | 🔥🔥 Comviva, CTS, Deloitte, EPAM, EY, Google, Infosys, JPM, TCS, WF, Wissen, Citi, Misc | 🔴 |
| 8 | **Transactional Outbox**, CDC (Debezium), Event Sourcing, CQRS, 2-phase commit | 🔥 EPAM, Wissen, Citi, Bravura, Barclays | 🔴 |
| 9 | Distributed transactions & data consistency across services without 2PC; DB-per-service; eventual consistency | 🔥 ACL, Amex, Bravura, JPM, TCS, Misc | 🔴 |
| 10 | **Idempotency** – idempotent POST (payment creation), idempotency keys, dedup table, unique constraints | 🔥🔥 Airtel, Amazon, Comviva, Deloitte, EPAM, EY, Google, Infosys, JPM, NavajNa, PayPal, PwC, WF, Misc | 🔴 |
| 11 | Distributed tracing / correlation IDs (Sleuth/Micrometer + Zipkin; propagate trace-id via headers/MDC); centralized logging (ELK/EFK); monitoring (Prometheus + Grafana); observability | 🔥 Airtel, Alti, Bitwise, EY, PayPal, Synchron, Walmart | 🟡 |
| 12 | Distributed locking (Redis `SET NX PX`/Redlock, DB advisory lock, ZooKeeper) | Wissen, Misc | 🔴 |
| 13 | Design patterns in microservices (API Gateway, Saga, CQRS, Strategy, DB-per-service, Strangler, Sidecar, Bulkhead…) ; orchestration pattern | Deloitte, Optum, Misc | 🟡 |
| 14 | Config management (Spring Cloud Config, ConfigMap), change `application.properties` without redeploy (`@RefreshScope`/Config server/ConfigMap) | HCL, i-exceed | 🟡 |
| 15 | Rate limiting – control how many users can access; third-party API with rate limit | 🔥 Amazon, Deloitte, Infosys, JPM, TechM, PayPal, Airtel | 🔴 |
| 16 | Handling 10 K RPS with 1 K RPS downstream (queue, buffer, backpressure, bulkhead, cache) | Deloitte | 🔴 |
| 17 | REST API versioning (URI/header/media-type), maintain multiple versions, WebSocket vs WebClient | Acc, Bajaj, Cap | 🟡 |
| 18 | Event-driven flow: send email after registration without slowing API (async via queue/`@Async`) | TechM | 🟡 |
| 19 | Large file upload between servers (streaming, chunking, multipart, presigned URL) | TechM, Misc | 🔴 |
| 20 | Microservice testing difficulty; contract testing | Flipkart | 🟡 |

### 9B. System Design (HLD) & LLD asked

| Design | Companies | Level |
|---|---|---|
| 🔥 **Payment processing/gateway system** (idempotent, retries, no duplicate charge, ledger, reconciliation, millions of txns) | Airtel, Amex, Comviva, EY, Google, JPM, Flipkart, Infosys, Misc | 🔴 |
| 🔥 **Rate limiter** (fixed window, sliding window log/counter, token bucket, leaky bucket; thread-safe; distributed with Redis + Lua) | Amazon, Airtel, Deloitte, JPM, PayPal, Misc | 🔴 |
| Fund transfer (A debited, B credit fails → Saga; order per account via Kafka partition key) | EY, Google | 🔴 |
| Notification system (WhatsApp/SMS/Email/Push; queue per channel, retry, DLQ, templates, idempotency) | Comviva, JPM, Walmart, Infosys | 🔴 |
| Real-time data pipeline / time-series (Kafka → stream processing → TSDB → Grafana) | Airtel | 🔴 |
| Global distributed rate limiter, distributed cache, distributed log aggregation system | Airtel, JPM, Wissen | 🔴 |
| Shopping cart / checkout with fraud detection; Flash-sale checkout; inventory overselling | Amex, Flipkart, i-exceed | 🔴 |
| Video streaming platform (Crunchyroll): upload, transcode, CDN, metadata, caching | Crunchyroll, UnClassified | 🔴 |
| Travel booking, Parking lot, Movie ticket booking (seat double-booking), ATM/bank, stock order book, vending machine, library, food-delivery state machine, logging framework | Airtel, JPM, Flipkart, i-exceed | 🔴 |
| Music player (Play/Next/Previous/Repeat – State pattern) ; Cricbuzz LLD + DB design | Kotak, Delhivery | 🔴 |
| Digital wallet / double-entry ledger / real-time fraud pipeline | JPM, Flipkart | 🔴 |
| Chat app / social feed / Slack-like notifications | Walmart | 🔴 |
| API handling 50 K RPS; 1 lakh msg/s Kafka; 1 M requests/day with no downtime; DR for multi-region microservices | EY, Misc | 🔴 |
| Fraud detection, data warehouse, news aggregator, ride-sharing DB | JPM | 🔴 |
| Product catalog & search, recommendation, order tracking | Flipkart | 🔴 |

### Key points / answer skeletons

**Idempotent payment API**
1. Client sends `Idempotency-Key: <uuid>` header.
2. Server: `INSERT INTO idempotency(key, request_hash, status) …` with **unique constraint** (or Redis `SET key NX EX`).
3. If key exists → return stored response (or 409 if still in progress / different payload).
4. Process payment inside one DB tx; persist response; use the key as the idempotency key to the PSP too.
5. Consumers: dedupe by `eventId` (processed-events table) – at-least-once + idempotent consumer = effectively-once.

**Saga for fund transfer / payment-inventory**: `Debit(A)` → `Credit(B)` ; on credit failure → compensating `Refund(A)`. Orchestrator keeps state machine (persisted); each step idempotent; use **Outbox** to atomically update DB + publish event.

**Outbox**: write business row + `outbox` row in one local tx → CDC (Debezium) / poller publishes to Kafka → solves "DB commit OK but Kafka publish failed" (WF, Misc).

**Circuit breaker config (Resilience4j)**
```yaml
resilience4j:
  circuitbreaker.instances.payment:
    slidingWindowType: COUNT_BASED
    slidingWindowSize: 20
    failureRateThreshold: 50
    waitDurationInOpenState: 10s
    permittedNumberOfCallsInHalfOpenState: 3
  retry.instances.payment:
    maxAttempts: 3
    waitDuration: 500ms
    enableExponentialBackoff: true
```
Order of decorators (outer→inner): Retry → CircuitBreaker → RateLimiter → TimeLimiter → Bulkhead.

**Rate limiter (token bucket, in-memory, thread-safe) – PayPal/JPM coding**
```java
class TokenBucket {
    private final long capacity, refillPerSec; private double tokens; private long last = System.nanoTime();
    TokenBucket(long capacity, long refillPerSec) { this.capacity = capacity; this.refillPerSec = refillPerSec; this.tokens = capacity; }
    synchronized boolean tryAcquire() {
        long now = System.nanoTime();
        tokens = Math.min(capacity, tokens + (now - last) / 1e9 * refillPerSec);
        last = now;
        if (tokens >= 1) { tokens -= 1; return true; }
        return false;
    }
}
// per-user: ConcurrentHashMap<String, TokenBucket> buckets; buckets.computeIfAbsent(userId, k -> new TokenBucket(100, 100/60.0 ...)).tryAcquire()
// Distributed: Redis Lua script (INCR + EXPIRE for fixed window, or ZSET for sliding window) so check+update is atomic.
```
Fixed window = cheap but burst at boundary (2× limit); sliding window log = exact but memory-heavy; sliding counter = approximation; token bucket = allows bursts.

**Scaling a service ×10 / 50 K RPS**: stateless instances behind LB + autoscaling, cache (Redis/CDN), async via Kafka, DB read replicas / sharding, connection-pool & thread tuning, backpressure, bulkheads, load tests, observability.

**Ordering at scale (Wissen/EY)**: Kafka partition key = `userId/accountId` → ordered per key; consumers use one thread per partition (or in-memory per-key worker queues); hot-key skew trade-off (80 % traffic on one key).

**Load balancer scenario (Bravura)**: instances register with Eureka/K8s Service; health checks (readiness) remove unhealthy; client-side LB (Spring Cloud LoadBalancer round-robin).

➡️ **Follow-ups** (JPM: "What happens if…"): service goes down? request retried? two transactions simultaneously? How do you recover from partial failure? How to prevent duplicates? What consistency model & why? How would DB choice change (SQL for ACID ledger vs NoSQL for feed)?

---

## 10. Kafka & Event-Driven Architecture

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | Kafka basics: topic, partition, broker, ZooKeeper/KRaft, producer, consumer, consumer group, offset, replication; Kafka vs RabbitMQ/ActiveMQ/Redis Pub-Sub; why Kafka for async | 🔥 Airtel, Citi, Cap, Delhivery, Flipkart, Mphasis, Synchrony, TechM, Mastercard, Misc, JPM | 🟢🟡 |
| 2 | Partitions & consumer groups – how assigned; more consumers than partitions (idle: 20 consumers / 8 partitions → 8 active); fewer consumers than partitions; same partition from different groups; how many partitions per topic; **how to decide number of partitions** | 🔥 Acc, Alti, Cap, Bitwise, Delhivery, Infosys, Kotak, TechM, Wissen, WF, Flipkart | 🟡 |
| 3 | How producer picks the partition (key hash / round-robin / custom partitioner) | Alti, Flipkart | 🟡 |
| 4 | **Delivery guarantees** at-most / at-least / exactly-once; idempotent producer (`enable.idempotence=true`, `acks=all`, `min.insync.replicas=2`), transactions; consumer-side idempotency | 🔥 Airtel, Bravura, Cap, CTS, Deloitte, JPM, MC, EY, TechM, Misc | 🔴 |
| 5 | **Consumer crashes after processing but before commit offset** – re-delivery, duplicates, how to design (idempotent processing, commit after processing, transactional) | 🔥 Acc, Oracle, Airtel, TechM, Misc | 🔴 |
| 6 | Offset management: auto vs manual commit, `commitSync/Async`, `enable.auto.commit`, `auto.offset.reset`, rebalancing | 🔥 Comviva, Kotak, Citi, Deloitte, CTS | 🟡 |
| 7 | **Duplicate event processing / safe reprocessing** | 🔥 CTS, Citi, Deloitte, EY, Infosys, PwC, TechM, JPM, Mphasis | 🔴 |
| 8 | **Consumer lag** diagnosis & fixes (add partitions/consumers, batch/parallelise, slow downstream, `max.poll.records`, rebalances, GC) ; consumer stuck in production | 🔥 Airtel, Bitwise, EY, Misc | 🔴 |
| 9 | **Poison messages, retry topics, DLQ/DLT**, exponential backoff, replay historical events without affecting live | 🔥 CTS, Deloitte, EPAM, EY, Infosys, PayPal, Wissen, Mastercard | 🔴 |
| 10 | Message ordering (per-key via partition), event ordering across two topics read by one consumer | 🔥 Citi, Deloitte, EY, Wissen, Misc | 🔴 |
| 11 | Broker down: leader election, ISR, replication factor; producer produces but broker dies; zero message loss config | Flipkart, TechM, WF, TCS | 🔴 |
| 12 | What happens when partition count increases (key→partition mapping changes, ordering break) | PayPal, UnClassified | 🔴 |
| 13 | Data retention policy, log compaction, cluster metadata | Flipkart, Mphasis | 🟡 |
| 14 | Kafka Streams: KStream vs KTable; how to know a message was consumed; schema registry | Citi, TechM, Mastercard | 🔴 |
| 15 | Kafka producer/consumer config in Spring Boot (`bootstrap.servers`, serializers, `group.id`, `acks`, `retries`, `linger.ms`, `batch.size`, `max.poll.interval.ms`, `isolation.level`) ; Spring Kafka | Comviva, Cap, CTS | 🟡 |
| 16 | DB commit succeeded but Kafka publish failed (and vice-versa) → Outbox / transactional producer | WF, Infosys, Misc | 🔴 |
| 17 | Consume XML from Kafka → transform → publish downstream; Service A → Kafka → B → REST → C | Infosys (LinkedIn 2026) | 🟡 |
| 18 | Kafka vs REST – when; 5 microservices must read the same message asynchronously (pub-sub, consumer groups) ; notification service async | EY, JPM, Flipkart, Infosys | 🟡 |
| 19 | Process 1 lakh msgs/sec; millions of messages/day; highly-available EDA; real-time pipeline | EY, TCS, Comviva, Airtel | 🔴 |
| 20 | Event sourcing; orchestration vs choreography | Citi | 🟡 |
| 21 | RabbitMQ basics (exchanges, queues, ack) | Misc | 🟢 |

### Key points

- **Reliable producer**: `acks=all`, `enable.idempotence=true`, `retries` high, `min.insync.replicas=2`, replication factor 3, `max.in.flight.requests.per.connection ≤ 5`.
- **Reliable consumer**: disable auto-commit; process → persist → `ack`; make handler idempotent (event-id table / upsert / unique key); `ErrorHandlingDeserializer`.
- **Exactly-once** inside Kafka = idempotent producer + transactions (`transactional.id`, `isolation.level=read_committed`, `sendOffsetsToTransaction`). End-to-end with external DB = at-least-once + idempotent sink or outbox.
- **Retry design**: `DefaultErrorHandler` + `ExponentialBackOff` → after N attempts → `DeadLetterPublishingRecoverer` → `<topic>.DLT`; or retry topics (`@RetryableTopic`) to avoid blocking partition; distinguish retriable vs non-retriable (deserialization, validation) exceptions.
- **Lag troubleshooting checklist**: `kafka-consumer-groups --describe` → is lag in all partitions or one (hot key)? → slow processing (DB/API calls) → `max.poll.interval.ms` exceeded causing rebalance loops → fewer consumers than partitions → GC pauses → batch + parallel processing → scale partitions.
- **Number of partitions** ≈ max(target throughput / per-partition producer throughput, target / per-partition consumer throughput); remember parallelism ≤ partitions, ordering per partition, more partitions = more file handles/rebalance time.
- **Ordering across 2 topics** isn't guaranteed – use a single topic/partition key or sequence numbers.

```java
@KafkaListener(topics = "payments", groupId = "ledger", containerFactory = "manualAckFactory")
void consume(ConsumerRecord<String, PaymentEvent> rec, Acknowledgment ack) {
    if (processed.existsById(rec.value().eventId())) { ack.acknowledge(); return; }  // dedupe
    ledgerService.apply(rec.value());          // @Transactional: business write + processed-event insert
    ack.acknowledge();                         // commit offset AFTER success
}
```

➡️ **Follow-ups**: What is ISR and `unclean.leader.election`? What triggers a rebalance and how to reduce (static membership, cooperative sticky assignor)? Why is Kafka fast (sequential IO, zero-copy, batching, page cache)? Kafka vs Redis Pub/Sub trade-offs (durability, replay, consumer groups)? How to replay events safely?

---

## 11. Redis, Caching & Performance

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | How is Redis used in your app; supported data types (String, Hash, List, Set, ZSet, Stream, Bitmap, HyperLogLog) | Alti, WF, Amazon, Oracle, Walmart | 🟢🟡 |
| 2 | **Cache-aside** pattern – why; write-through / write-behind / read-through; Redis vs Caffeine (Synchron) | WF, MC, Synchron, Optum | 🟡 |
| 3 | **Cache stampede / thundering herd** (1000 requests after key expiry) – mutex/single-flight lock, probabilistic early refresh, TTL jitter, request coalescing | WF | 🔴 |
| 4 | **Stale cache** – why `@Cacheable` returns old price after DB change; fix (`@CacheEvict`/`@CachePut`, TTL, event-driven invalidation) | NavajNa, TechM, EY, Deloitte | 🟡 |
| 5 | Replication vs partitioning (sharding), Redis Cluster, persistence (RDB/AOF), eviction policies (LRU/LFU) | Alti | 🟡 |
| 6 | When/why to use Redis caching; fetch same master data repeatedly → cache | Amazon, TechM, Walmart | 🟡 |
| 7 | Distributed cache design; thread-safe cache with expiry; LRU | JPM, Synchron | 🔴 |
| 8 | Incorrect cache config → `OutOfMemoryError` (unbounded cache; use size/TTL) | PwC | 🔴 |
| 9 | React/Angular caching; HTTP caching/CDN | MC, Crunchyroll | 🟡 |
| 10 | Distributed locking and rate limiting with Redis | Wissen, Misc | 🔴 |

**Performance questions**: slow API → profile/APM, query count, indexes, pagination, caching, async/parallel downstream calls, connection pool sizing, payload compression, GC; "API returns lots of data – optimise" (pagination/streaming/projection); processing millions of records without OOM (streaming/chunking, `Stream` + cursor/`fetchSize`, Spring Batch with checkpointing & restartability – Wipro WEGA).

```java
@Cacheable(value = "products", key = "#id")             Product get(Long id)            { ... }
@CachePut (value = "products", key = "#p.id")           Product update(Product p)       { ... }
@CacheEvict(value = "products", key = "#id")            void delete(Long id)            { ... }
```
**Stampede guard (Redis)**: on miss → `SET lock:key uuid NX PX 5000` → winner recomputes & sets with TTL + random jitter; others wait/retry briefly or serve stale value.

➡️ **Follow-ups**: Cache invalidation strategies? What if Redis is down (fail-open to DB + circuit breaker)? Hot key problem? Redis single-threaded – why fast? TTL vs eviction?

---

## 12. AWS, Docker, Kubernetes & CI/CD

| # | Question | Companies | Level |
|---|---|---|---|
| 1 | Deploy Spring Boot microservices to AWS/Azure; deployment flow; config & secrets; monitoring; scalability/fault tolerance; securing communication | 🔥 HiperBrain, EY, Infosys, Mphasis, Synchron, Acc, Misc | 🟡 |
| 2 | EC2 vs ECS vs Lambda (serverless); create EC2; connect EC2 with S3; S3 max object size (5 TB; single PUT 5 GB); IAM roles | EY, Bitwise, Misc | 🟡 |
| 3 | Load balancing (ALB/NLB), Auto Scaling groups, vertical vs horizontal scaling | 🔥 Acc, Infosys, HCL, Synchron | 🟡 |
| 4 | Monitor apps in AWS (CloudWatch, X-Ray) ; Prometheus + Grafana; ELK/EFK; Kubernetes pod logs; CI/CD logs | 🔥 Airtel, Bitwise, EY, Synchron, Walmart | 🟡 |
| 5 | Store passwords/secrets in AWS (Secrets Manager, Parameter Store, KMS) | Infosys, TechM | 🟡 |
| 6 | **Docker**: Dockerfile for Spring Boot (multi-stage, layered jar, non-root), image vs container, Docker Compose, common commands, `.dockerignore` | 🔥 Acc, HCL, Infosys, Misc, Synchrony, Walmart | 🟢🟡 |
| 7 | **Kubernetes**: Pod vs Deployment vs ReplicaSet vs Service; ConfigMap/Secret; scale pods; HPA; **liveness vs readiness probes**; init containers; what happens if pod/node crashes; Kubernetes vs OpenShift; EKS pre-traffic checks | 🔥 EPAM, IntraEdge, i-exceed, Misc, WF, Citi, HCL | 🟡 |
| 8 | **CI/CD** pipeline for Spring Boot (checkout → build → unit tests → Sonar → package → image → scan → deploy → smoke tests); Jenkins pipeline; GitHub Actions; unit test failure; failed prod deployment; rollback | 🔥 Acc, Infosys, HCL, Nagaro, Walmart, Misc, Synchron, MC | 🟡 |
| 9 | Deployment strategies: blue-green, canary, rolling; zero-downtime deploy in K8s | Citi, HCL, Misc | 🟡🔴 |
| 10 | SonarQube & code coverage (JaCoCo) | Cap, Deloitte, Honey Bee | 🟢 |
| 11 | Git: pull vs fetch, merge vs rebase, conflict resolution, common commands; Agile/Scrum/JIRA | Acc, Cognizant, Logixal | 🟢 |
| 12 | Terraform migration, container vulnerability response, cloud cost reduction (DevOps scenarios) | Mastercard | 🔴 |
| 13 | Check pipeline fails midway / deployment halfway leaves mixed versions – recovery | Bitwise, MC | 🔴 |
| 14 | Types of testing; performance testing in CI; smoke tests; health checks (app vs downstream) | MC, IntraEdge | 🟡 |

### Key points
**Dockerfile (Spring Boot, multi-stage)**
```dockerfile
FROM maven:3.9-eclipse-temurin-21 AS build
WORKDIR /app
COPY pom.xml .
RUN mvn -q dependency:go-offline
COPY src ./src
RUN mvn -q package -DskipTests

FROM eclipse-temurin:21-jre
RUN useradd -r app
USER app
COPY --from=build /app/target/*.jar /app.jar
EXPOSE 8080
ENTRYPOINT ["java","-XX:MaxRAMPercentage=75","-jar","/app.jar"]
```
- **Liveness** = "should the container be restarted?" ; **Readiness** = "should it receive traffic?" (use `/actuator/health/liveness|readiness`); **startup probe** for slow apps. **Init containers** run to completion before app (wait for DB, migrations).
- **Failed prod deployment**: automatic rollback (`kubectl rollout undo`/helm rollback), canary with metrics gates, feature flags, DB migrations backward-compatible (expand/contract).
- **Zero-downtime**: rolling update with `maxUnavailable=0`, readiness probes, `preStop` hook + graceful shutdown (`server.shutdown=graceful`), PodDisruptionBudget.
- **Pod crash**: kubelet restarts (CrashLoopBackOff w/ backoff); node down: scheduler reschedules pods from Deployment/ReplicaSet on other nodes after eviction timeout.
- **HPA**: scales replicas on CPU/memory/custom metrics against `requests`; needs metrics-server.

➡️ **Follow-ups**: Container keeps restarting with no app errors (OOMKilled, probe failing, exit code, `kubectl describe`/`logs --previous`)? Image layers & caching? Difference between `CMD` and `ENTRYPOINT`? Secrets in K8s are base64 – how to secure (external secrets/KMS)?

---


---

## 13. DSA & Java Coding Problems

All solutions below are **compiled and tested** (single file `Solutions.java`, ends with `ALL OK`).

| # | Problem | Companies | Diff | Technique |
|---|---------|-----------|------|-----------|
| 1 | Reverse string / palindrome | Common | 🟢 | Two pointers |
| 2 | First non-repeating character | Accenture, Deloitte, EPAM, HCL, Bravura | 🟢 | LinkedHashMap count |
| 3 | Longest substring without repeating chars | Amazon, Amex, Altimetrik, EPAM, Flipkart, Google, JPM, Synchrony, Wells Fargo | 🟡 | Sliding window |
| 4 | Group anagrams | Flipkart, Google, Common | 🟡 | Sorted-key map |
| 5 | Isomorphic strings | ACL | 🟡 | Two maps |
| 6 | Longest common prefix | JPM, Deloitte | 🟢 | Shrink prefix |
| 7 | Valid brackets | Deloitte, Common | 🟢 | Stack |
| 8 | Add two huge numbers (strings) | Wissen | 🟡 | Carry loop |
| 9 | Good substrings of length 3 | PhonePe | 🟢 | Window |
| 10 | Second smallest/largest w/o sorting | ACL, Hughes, Barclays, Accenture, HCL, NavajNa | 🟢 | Single pass |
| 11 | Two Sum / 3Sum | Airtel, Deloitte, NavajNa | 🟢/🟡 | HashMap / sort + 2 pointers |
| 12 | Missing number (sorted / unsorted) | Comviva, Accenture, JPM | 🟢 | Sum / binary search |
| 13 | Move zeroes | Flipkart, JPM | 🟢 | Write pointer |
| 14 | Sort 0/1/2 in one pass | Common | 🟡 | Dutch flag |
| 15 | Search in rotated sorted array | Airtel | 🟡 | Modified binary search |
| 16 | Trapping rain water | Flipkart, Google | 🔴 | Two pointers |
| 17 | Find duplicate, O(1) space, read-only | Delhivery | 🔴 | Floyd cycle |
| 18 | Partition by threshold / merge sorted arrays in place | EPAM, TCS | 🟢 | Two pointers |
| 19 | Max sum subarray of size K | Wells Fargo | 🟢 | Sliding window |
| 20 | Min-length subarray with sum ≥ target | Deloitte | 🟡 | Sliding window |
| 21 | Extra elements of list1 vs list2 | Capgemini, MasterCard | 🟢 | Frequency map |
| 22 | Min deletions for unique char frequencies | Amex | 🟡 | Greedy + set |
| 23 | Merge intervals | Google, Flipkart | 🟡 | Sort |
| 24 | Top K frequent | Flipkart, Google | 🟡 | Min-heap |
| 25 | Trailing zeros of n! | Tech Mahindra | 🟢 | Count factor 5 |
| 26 | Travel pass min cost | Kotak | 🟡 | DP |
| 27 | Coin change / stock buy-sell / LIS / word break | Flipkart, Google, Oracle | 🟡 | DP |
| 28 | Combination Sum | Hughes, JPM | 🟡 | Backtracking |
| 29 | Subset count with sum K | Tech Mahindra | 🟡 | 0/1 knapsack DP |
| 30 | 2^n digit sum / digital root | Kotak | 🟡 | Modular pow |
| 31 | Linked list: reverse, cycle, middle, components | Delhivery, Common | 🟢/🟡 | Fast/slow |
| 32 | Number of Islands (+diagonal) | Google, Flipkart | 🟡 | DFS (BFS alt.) |
| 33 | Celebrity problem | Amex | 🟡 | Stack elimination |
| 34 | Infix → postfix | Deloitte | 🟡 | Shunting-yard |
| 35 | LRU cache (HashMap + DLL) | Amazon, Flipkart, Google | 🟡 | O(1) get/put |

**Not coded here (explain verbally):** Dijkstra (PriorityQueue), LCA of binary tree, course schedule (Kahn topological sort), clone graph (map old→new + BFS), median of two sorted arrays (binary search on partition), min window substring (sliding window + counts), 0/1 knapsack, kth largest in stream (min-heap of size k), water jug 5/3→4 (gcd/BFS: fill 5, pour into 3, empty 3, pour remaining 2, refill 5, top up 3 → 4 left), JSON nested object count (recursion).

**Follow-ups to expect:** time/space complexity; brute force → optimal; handle empty/null/negative/duplicates; "what if input doesn't fit in memory?"; "can you do it without extra space?"

```java
import java.util.*;
import java.util.stream.*;

public class Solutions {

    // ---------- Strings ----------
    static String reverse(String s) { char[] c = s.toCharArray(); for (int i = 0, j = c.length - 1; i < j; i++, j--) { char t = c[i]; c[i] = c[j]; c[j] = t; } return new String(c); }

    static boolean isPalindrome(String s) { int i = 0, j = s.length() - 1; while (i < j) if (s.charAt(i++) != s.charAt(j--)) return false; return true; }

    static int firstUniqueChar(String s) {
        Map<Character, Integer> m = new LinkedHashMap<>();
        for (char c : s.toCharArray()) m.merge(c, 1, Integer::sum);
        for (int i = 0; i < s.length(); i++) if (m.get(s.charAt(i)) == 1) return i;
        return -1;
    }

    static int lengthOfLongestSubstring(String s) {
        Map<Character, Integer> last = new HashMap<>();
        int best = 0, left = 0;
        for (int r = 0; r < s.length(); r++) {
            Integer prev = last.get(s.charAt(r));
            if (prev != null && prev >= left) left = prev + 1;
            last.put(s.charAt(r), r);
            best = Math.max(best, r - left + 1);
        }
        return best;
    }

    static List<List<String>> groupAnagrams(String[] words) {
        Map<String, List<String>> m = new HashMap<>();
        for (String w : words) { char[] c = w.toCharArray(); Arrays.sort(c); m.computeIfAbsent(new String(c), k -> new ArrayList<>()).add(w); }
        return new ArrayList<>(m.values());
    }

    static boolean isIsomorphic(String a, String b) {
        if (a.length() != b.length()) return false;
        Map<Character, Character> ab = new HashMap<>(), ba = new HashMap<>();
        for (int i = 0; i < a.length(); i++) {
            char x = a.charAt(i), y = b.charAt(i);
            if (ab.putIfAbsent(x, y) != null && ab.get(x) != y) return false;
            if (ba.putIfAbsent(y, x) != null && ba.get(y) != x) return false;
        }
        return true;
    }

    static String longestCommonPrefix(String[] s) {
        if (s.length == 0) return "";
        String p = s[0];
        for (String w : s) while (!w.startsWith(p)) p = p.substring(0, p.length() - 1);
        return p;
    }

    static boolean validBrackets(String s) {
        Deque<Character> st = new ArrayDeque<>();
        for (char c : s.toCharArray()) {
            if ("([{".indexOf(c) >= 0) st.push(c);
            else {
                if (st.isEmpty()) return false;
                char o = st.pop();
                if ((c == ')' && o != '(') || (c == ']' && o != '[') || (c == '}' && o != '{')) return false;
            }
        }
        return st.isEmpty();
    }

    static String addLargeNumbers(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int i = a.length() - 1, j = b.length() - 1, carry = 0;
        while (i >= 0 || j >= 0 || carry > 0) {
            int s = carry + (i >= 0 ? a.charAt(i--) - '0' : 0) + (j >= 0 ? b.charAt(j--) - '0' : 0);
            sb.append(s % 10); carry = s / 10;
        }
        return sb.reverse().toString();
    }

    static int goodSubstrings(String s) {
        int c = 0;
        for (int i = 0; i + 2 < s.length(); i++) if (s.charAt(i) != s.charAt(i + 1) && s.charAt(i) != s.charAt(i + 2) && s.charAt(i + 1) != s.charAt(i + 2)) c++;
        return c;
    }

    static int strStr(String h, String n) { return h.indexOf(n); } // interview expects manual loop

    // ---------- Arrays ----------
    static int secondSmallest(int[] a) {
        int min = Integer.MAX_VALUE, second = Integer.MAX_VALUE;
        for (int x : a) { if (x < min) { second = min; min = x; } else if (x > min && x < second) second = x; }
        return second;
    }

    static int secondLargestDistinct(int[] a) {
        long max = Long.MIN_VALUE, second = Long.MIN_VALUE;
        for (int x : a) { if (x > max) { second = max; max = x; } else if (x < max && x > second) second = x; }
        return (int) second;
    }

    static int[] twoSum(int[] a, int target) {
        Map<Integer, Integer> seen = new HashMap<>();
        for (int i = 0; i < a.length; i++) {
            Integer j = seen.get(target - a[i]);
            if (j != null) return new int[]{j, i};
            seen.put(a[i], i);
        }
        return new int[0];
    }

    static List<List<Integer>> threeSum(int[] a) {
        Arrays.sort(a);
        List<List<Integer>> res = new ArrayList<>();
        for (int i = 0; i < a.length - 2; i++) {
            if (i > 0 && a[i] == a[i - 1]) continue;
            int l = i + 1, r = a.length - 1;
            while (l < r) {
                int s = a[i] + a[l] + a[r];
                if (s == 0) { res.add(List.of(a[i], a[l], a[r])); l++; r--; while (l < r && a[l] == a[l - 1]) l++; while (l < r && a[r] == a[r + 1]) r--; }
                else if (s < 0) l++; else r--;
            }
        }
        return res;
    }

    static int missingNumberUnsorted(int[] a) { int n = a.length + 1; int sum = n * (n + 1) / 2; for (int x : a) sum -= x; return sum; }

    static int missingNumberSorted(int[] a) { // values start at a[0], consecutive with one missing
        int lo = 0, hi = a.length - 1;
        while (lo < hi) { int mid = (lo + hi) >>> 1; if (a[mid] - a[0] == mid) lo = mid + 1; else hi = mid; }
        return a[0] + lo;
    }

    static void moveZeroes(int[] a) { int k = 0; for (int x : a) if (x != 0) a[k++] = x; while (k < a.length) a[k++] = 0; }

    static void sortColors(int[] a) { // 0s,1s,2s in one pass (Dutch flag)
        int lo = 0, mid = 0, hi = a.length - 1;
        while (mid <= hi) { if (a[mid] == 0) swap(a, lo++, mid++); else if (a[mid] == 1) mid++; else swap(a, mid, hi--); }
    }
    static void swap(int[] a, int i, int j) { int t = a[i]; a[i] = a[j]; a[j] = t; }

    static int search(int[] a, int t) { // rotated sorted array
        int l = 0, r = a.length - 1;
        while (l <= r) {
            int m = l + (r - l) / 2;
            if (a[m] == t) return m;
            if (a[l] <= a[m]) { if (t >= a[l] && t < a[m]) r = m - 1; else l = m + 1; }
            else { if (t > a[m] && t <= a[r]) l = m + 1; else r = m - 1; }
        }
        return -1;
    }

    static int trap(int[] h) {
        int l = 0, r = h.length - 1, lm = 0, rm = 0, w = 0;
        while (l < r) { if (h[l] < h[r]) { lm = Math.max(lm, h[l]); w += lm - h[l++]; } else { rm = Math.max(rm, h[r]); w += rm - h[r--]; } }
        return w;
    }

    static int findDuplicateReadOnly(int[] a) { // Floyd, O(n) time O(1) space, values in 1..n, size n+1
        int slow = a[0], fast = a[0];
        do { slow = a[slow]; fast = a[a[fast]]; } while (slow != fast);
        slow = a[0];
        while (slow != fast) { slow = a[slow]; fast = a[fast]; }
        return slow;
    }

    static void partitionByThreshold(int[] a, int t) { int i = 0; for (int j = 0; j < a.length; j++) if (a[j] < t) swap(a, i++, j); }

    static void merge(int[] a, int m, int[] b, int n) { // a has room for m+n
        int i = m - 1, j = n - 1, k = m + n - 1;
        while (j >= 0) a[k--] = (i >= 0 && a[i] > b[j]) ? a[i--] : b[j--];
    }

    static int maxSumSubarrayK(int[] a, int k) {
        int sum = 0, best;
        for (int i = 0; i < k; i++) sum += a[i];
        best = sum;
        for (int i = k; i < a.length; i++) { sum += a[i] - a[i - k]; best = Math.max(best, sum); }
        return best;
    }

    static int minSubarrayLen(int target, int[] a) { // sum >= target (positive numbers)
        int l = 0, sum = 0, best = Integer.MAX_VALUE;
        for (int r = 0; r < a.length; r++) { sum += a[r]; while (sum >= target) { best = Math.min(best, r - l + 1); sum -= a[l++]; } }
        return best == Integer.MAX_VALUE ? 0 : best;
    }

    static List<Integer> extraElements(List<Integer> l1, List<Integer> l2) {
        Map<Integer, Integer> f = new HashMap<>();
        l1.forEach(x -> f.merge(x, 1, Integer::sum));
        l2.forEach(x -> f.computeIfPresent(x, (k, v) -> v == 1 ? null : v - 1));
        List<Integer> out = new ArrayList<>();
        f.forEach((k, v) -> { for (int i = 0; i < v; i++) out.add(k); });
        return out;
    }

    static int minDeletionsUniqueFreq(String s) {
        int[] cnt = new int[26]; for (char c : s.toCharArray()) cnt[c - 'a']++;
        Set<Integer> used = new HashSet<>(); int del = 0;
        for (int f : cnt) { while (f > 0 && !used.add(f)) { f--; del++; } }
        return del;
    }

    static int[][] mergeIntervals(int[][] in) {
        Arrays.sort(in, Comparator.comparingInt(x -> x[0]));
        List<int[]> res = new ArrayList<>();
        for (int[] cur : in) { if (res.isEmpty() || res.get(res.size() - 1)[1] < cur[0]) res.add(cur); else res.get(res.size() - 1)[1] = Math.max(res.get(res.size() - 1)[1], cur[1]); }
        return res.toArray(new int[0][]);
    }

    static int[] topKFrequent(int[] a, int k) {
        Map<Integer, Integer> f = new HashMap<>(); for (int x : a) f.merge(x, 1, Integer::sum);
        PriorityQueue<Map.Entry<Integer, Integer>> pq = new PriorityQueue<>(Map.Entry.comparingByValue());
        for (var e : f.entrySet()) { pq.offer(e); if (pq.size() > k) pq.poll(); }
        return pq.stream().mapToInt(Map.Entry::getKey).toArray();
    }

    static int trailingZeroesFactorial(int n) { int c = 0; while (n > 0) { n /= 5; c += n; } return c; }

    static int minCostTickets(int[] days, int[] costs) {
        int last = days[days.length - 1]; boolean[] travel = new boolean[last + 1]; for (int d : days) travel[d] = true;
        int[] dp = new int[last + 1];
        for (int i = 1; i <= last; i++) {
            if (!travel[i]) { dp[i] = dp[i - 1]; continue; }
            dp[i] = Math.min(dp[i - 1] + costs[0], Math.min(dp[Math.max(0, i - 7)] + costs[1], dp[Math.max(0, i - 30)] + costs[2]));
        }
        return dp[last];
    }

    static int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1]; Arrays.fill(dp, amount + 1); dp[0] = 0;
        for (int a = 1; a <= amount; a++) for (int c : coins) if (c <= a) dp[a] = Math.min(dp[a], dp[a - c] + 1);
        return dp[amount] > amount ? -1 : dp[amount];
    }

    static int maxProfit(int[] p) { int min = Integer.MAX_VALUE, best = 0; for (int x : p) { min = Math.min(min, x); best = Math.max(best, x - min); } return best; }

    static int lis(int[] a) { // O(n log n)
        int[] tails = new int[a.length]; int size = 0;
        for (int x : a) { int i = Arrays.binarySearch(tails, 0, size, x); if (i < 0) i = -(i + 1); tails[i] = x; if (i == size) size++; }
        return size;
    }

    static boolean wordBreak(String s, Set<String> dict) {
        boolean[] dp = new boolean[s.length() + 1]; dp[0] = true;
        for (int i = 1; i <= s.length(); i++) for (int j = 0; j < i; j++) if (dp[j] && dict.contains(s.substring(j, i))) { dp[i] = true; break; }
        return dp[s.length()];
    }

    static List<List<Integer>> combinationSum(int[] c, int target) {
        List<List<Integer>> res = new ArrayList<>(); bt(c, target, 0, new ArrayList<>(), res); return res;
    }
    static void bt(int[] c, int rem, int start, List<Integer> cur, List<List<Integer>> res) {
        if (rem == 0) { res.add(new ArrayList<>(cur)); return; }
        for (int i = start; i < c.length && c[i] <= rem; i++) { cur.add(c[i]); bt(c, rem - c[i], i, cur, res); cur.remove(cur.size() - 1); }
    }

    static int countSubsetsWithSum(int[] a, int k) {
        int[] dp = new int[k + 1]; dp[0] = 1;
        for (int x : a) for (int s = k; s >= x; s--) dp[s] += dp[s - x];
        return dp[k];
    }

    static int digitalRootOfPowerOfTwo(long n) { // 2^n digital root, n up to 1e9: root cycles with period 6 for 2^n mod 9
        int r = (int) pow(2, n, 9); return r == 0 ? 9 : r;
    }
    static long pow(long b, long e, long m) { long r = 1; b %= m; while (e > 0) { if ((e & 1) == 1) r = r * b % m; b = b * b % m; e >>= 1; } return r; }

    // ---------- Linked list / Graph ----------
    static class ListNode { int val; ListNode next; ListNode(int v) { val = v; } }

    static ListNode reverseList(ListNode h) { ListNode prev = null; while (h != null) { ListNode n = h.next; h.next = prev; prev = h; h = n; } return prev; }
    static boolean hasCycle(ListNode h) { ListNode s = h, f = h; while (f != null && f.next != null) { s = s.next; f = f.next.next; if (s == f) return true; } return false; }
    static ListNode middle(ListNode h) { ListNode s = h, f = h; while (f != null && f.next != null) { s = s.next; f = f.next.next; } return s; }
    static int connectedComponents(ListNode head, int[] nums) {
        Set<Integer> set = new HashSet<>(); for (int x : nums) set.add(x);
        int c = 0; boolean in = false;
        for (ListNode n = head; n != null; n = n.next) { if (set.contains(n.val)) { if (!in) { c++; in = true; } } else in = false; }
        return c;
    }

    static int numIslands(char[][] g, boolean diagonal) {
        int c = 0;
        for (int i = 0; i < g.length; i++) for (int j = 0; j < g[0].length; j++) if (g[i][j] == '1') { c++; dfs(g, i, j, diagonal); }
        return c;
    }
    static void dfs(char[][] g, int i, int j, boolean diag) {
        if (i < 0 || j < 0 || i >= g.length || j >= g[0].length || g[i][j] != '1') return;
        g[i][j] = '0';
        for (int di = -1; di <= 1; di++) for (int dj = -1; dj <= 1; dj++) {
            if ((di == 0 && dj == 0) || (!diag && di != 0 && dj != 0)) continue;
            dfs(g, i + di, j + dj, diag);
        }
    }

    static int celebrity(int[][] knows) { // knows[a][b]==1 : a knows b
        int n = knows.length; Deque<Integer> st = new ArrayDeque<>(); for (int i = 0; i < n; i++) st.push(i);
        while (st.size() > 1) { int a = st.pop(), b = st.pop(); if (knows[a][b] == 1) st.push(b); else st.push(a); }
        int c = st.pop();
        for (int i = 0; i < n; i++) if (i != c && (knows[c][i] == 1 || knows[i][c] == 0)) return -1;
        return c;
    }

    static String infixToPostfix(String exp) {
        StringBuilder out = new StringBuilder(); Deque<Character> st = new ArrayDeque<>();
        for (char c : exp.toCharArray()) {
            if (Character.isLetterOrDigit(c)) out.append(c);
            else if (c == '(') st.push(c);
            else if (c == ')') { while (!st.isEmpty() && st.peek() != '(') out.append(st.pop()); st.pop(); }
            else { while (!st.isEmpty() && st.peek() != '(' && (prec(st.peek()) > prec(c) || (prec(st.peek()) == prec(c) && c != '^'))) out.append(st.pop()); st.push(c); }
        }
        while (!st.isEmpty()) out.append(st.pop());
        return out.toString();
    }
    static int prec(char c) { return switch (c) { case '+', '-' -> 1; case '*', '/' -> 2; case '^' -> 3; default -> 0; }; }

    // ---------- LRU (HashMap + doubly linked list) ----------
    static class LRUCache {
        class Node { int k, v; Node prev, next; Node(int k, int v) { this.k = k; this.v = v; } }
        private final int cap; private final Map<Integer, Node> map = new HashMap<>();
        private final Node head = new Node(0, 0), tail = new Node(0, 0);
        LRUCache(int cap) { this.cap = cap; head.next = tail; tail.prev = head; }
        int get(int k) { Node n = map.get(k); if (n == null) return -1; remove(n); addFront(n); return n.v; }
        void put(int k, int v) {
            Node n = map.get(k);
            if (n != null) { n.v = v; remove(n); addFront(n); return; }
            if (map.size() == cap) { Node lru = tail.prev; remove(lru); map.remove(lru.k); }
            n = new Node(k, v); map.put(k, n); addFront(n);
        }
        private void remove(Node n) { n.prev.next = n.next; n.next.prev = n.prev; }
        private void addFront(Node n) { n.next = head.next; n.prev = head; head.next.prev = n; head.next = n; }
    }

    public static void main(String[] a) {
        check(reverse("hello").equals("olleh"));
        check(isPalindrome("madam"));
        check(firstUniqueChar("hackathon") == 2);
        check(lengthOfLongestSubstring("ABCABCBB") == 3);
        check(groupAnagrams(new String[]{"eat", "tea", "tan", "ate", "nat", "bat"}).size() == 3);
        check(isIsomorphic("egg", "add") && !isIsomorphic("foo", "bar"));
        check(longestCommonPrefix(new String[]{"apple", "apply", "approach"}).equals("app"));
        check(validBrackets("([]){}") && !validBrackets("([)]"));
        check(addLargeNumbers("99999999999999999999", "1").equals("100000000000000000000"));
        check(goodSubstrings("xyzzaz") == 1);
        check(secondSmallest(new int[]{5, 2, 9, 1, 3}) == 2);
        check(secondLargestDistinct(new int[]{5, 9, 9, 3}) == 5);
        check(Arrays.equals(twoSum(new int[]{2, 7, 11, 15}, 9), new int[]{0, 1}));
        check(threeSum(new int[]{-1, 0, 1, 2, -1, -4}).size() == 2);
        check(missingNumberUnsorted(new int[]{1, 2, 4, 5}) == 3);
        check(missingNumberSorted(new int[]{1, 2, 3, 5, 6}) == 4);
        int[] z = {1, 0, 1, 0, 0, 1, 0, 1}; moveZeroes(z); check(Arrays.equals(z, new int[]{1, 1, 1, 1, 0, 0, 0, 0}));
        int[] c = {2, 0, 2, 1, 1, 0}; sortColors(c); check(Arrays.equals(c, new int[]{0, 0, 1, 1, 2, 2}));
        check(search(new int[]{4, 5, 6, 7, 0, 1, 2}, 0) == 4);
        check(trap(new int[]{0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1}) == 6);
        int d = findDuplicateReadOnly(new int[]{1, 3, 4, 2, 2}); check(d == 2);
        int[] p = {9, 1, 8, 2, 7}; partitionByThreshold(p, 5); check(p[0] < 5 && p[1] < 5 && p[2] >= 5);
        int[] m = {1, 3, 5, 0, 0, 0}; merge(m, 3, new int[]{2, 4, 6}, 3); check(Arrays.equals(m, new int[]{1, 2, 3, 4, 5, 6}));
        check(maxSumSubarrayK(new int[]{2, 1, 5, 1, 3, 2}, 3) == 9);
        check(minSubarrayLen(7, new int[]{2, 3, 1, 2, 4, 3}) == 2);
        check(extraElements(List.of(1, 2, 3, 4, 4), List.of(1, 2, 3, 4)).equals(List.of(4)));
        check(minDeletionsUniqueFreq("aaabbbcc") == 2);
        check(mergeIntervals(new int[][]{{1, 3}, {2, 6}, {8, 10}}).length == 2);
        check(topKFrequent(new int[]{1, 1, 1, 2, 2, 3}, 2).length == 2);
        check(trailingZeroesFactorial(100) == 24);
        check(minCostTickets(new int[]{1, 4, 6, 7, 8, 20}, new int[]{2, 7, 15}) == 11);
        check(coinChange(new int[]{1, 2, 5}, 11) == 3);
        check(maxProfit(new int[]{7, 1, 5, 3, 6, 4}) == 5);
        check(lis(new int[]{10, 9, 2, 5, 3, 7, 101, 18}) == 4);
        check(wordBreak("leetcode", Set.of("leet", "code")));
        check(combinationSum(new int[]{2, 3, 6, 7}, 7).size() == 2);
        check(countSubsetsWithSum(new int[]{1, 2, 3, 3}, 6) == 3);
        check(digitalRootOfPowerOfTwo(10) == 7); // 1024 -> 7
        ListNode h = new ListNode(0); h.next = new ListNode(1); h.next.next = new ListNode(2); h.next.next.next = new ListNode(3);
        check(connectedComponents(h, new int[]{0, 1, 3}) == 2);
        check(middle(h).val == 2);
        check(reverseList(h).val == 3);
        check(!hasCycle(new ListNode(1)));
        char[][] g = {"11000".toCharArray(), "11000".toCharArray(), "00100".toCharArray(), "00011".toCharArray()};
        check(numIslands(g, false) == 3);
        check(celebrity(new int[][]{{0, 1, 1}, {0, 0, 1}, {0, 0, 0}}) == 2);
        check(infixToPostfix("a+b*(c^d-e)^(f+g*h)-i").equals("abcd^e-fgh*+^*+i-"));
        LRUCache l = new LRUCache(2); l.put(1, 1); l.put(2, 2); check(l.get(1) == 1); l.put(3, 3); check(l.get(2) == -1);
        System.out.println("ALL OK");
    }
    static void check(boolean b) { if (!b) throw new AssertionError(new Throwable().getStackTrace()[1]); }
}
```


---

## 14. Real-World Production Troubleshooting Scenarios

**Universal framework (say this first in any scenario):** 1) Scope & impact (who/what/since when) → 2) Recent changes (deploy/config/data/traffic) → 3) Metrics (RED: rate, errors, duration; USE: CPU, mem, threads, I/O) → 4) Logs + trace by correlation ID → 5) Mitigate first (rollback, scale, feature-flag, restart) → 6) Root cause → 7) Fix + prevention + postmortem.

**Toolbox:** `jstack`/`jcmd Thread.print` (3 dumps, 10 s apart), `jmap -histo` / heap dump + Eclipse MAT, JFR, `top -H` (map hot thread id → hex → `nid` in jstack), GC logs (`-Xlog:gc*`), Actuator, Prometheus/Grafana, ELK, Zipkin/Jaeger/OpenTelemetry, `EXPLAIN ANALYZE`, `kubectl logs --previous / describe pod`, Kafka `kafka-consumer-groups --describe`.

| # | Scenario | Companies | Diff | Approach / likely causes |
|---|----------|-----------|------|--------------------------|
| 1 | OutOfMemoryError in prod | Many | 🟡 | Heap dump on OOM (`-XX:+HeapDumpOnOutOfMemoryError`), MAT dominator tree; leaks: static collections, unbounded caches, ThreadLocal not removed, unclosed resources, large result sets. Distinguish heap / Metaspace / native / "unable to create thread". |
| 2 | High CPU at low traffic | Misc | 🟡 | `top -H` → thread → jstack; infinite loops, regex backtracking, GC thrash, busy-wait polling, HashMap contention loops |
| 3 | Slow after hours / gradually degrades | Misc | 🟡 | Memory leak → GC pressure; connection leak; growing tables/missing index; log file growth; thread leak |
| 4 | GC pauses / latency spikes | Google, MC | 🔴 | GC logs; reduce allocation; right-size heap; G1 → ZGC; check humongous objects, finalizers |
| 5 | Latency 200 ms → 3–5 s after deploy | MC, Wissen, Accenture, Google | 🔴 | Diff the release; N+1 queries, new sync downstream call, missing index, pool size/config change, cold cache, dependency slow; compare traces before/after; rollback |
| 6 | p99 80 ms → 2 s overnight | Google | 🔴 | Percentile vs mean; data growth, GC, noisy neighbor, retry storm, lock contention, cache expiry stampede |
| 7 | 5 % HTTP 500 after release | Deloitte | 🟡 | Which endpoint/instance? Canary/mixed versions, backward-incompatible schema/contract, bad config on some pods; roll back |
| 8 | Mixed versions after failed deploy | Misc | 🟡 | Rolling update stuck; readiness probe, DB migration compat (expand/contract), backward-compatible APIs |
| 9 | Duplicate payments / requests | PayPal, UnClassified | 🔴 | Idempotency key + unique constraint, client retries, Kafka at-least-once, double click; dedupe table, outbox |
| 10 | Thread-pool exhaustion / unresponsive service | Misc | 🟡 | jstack shows all threads WAITING on same downstream/DB; timeouts, bulkheads, bounded queue, circuit breaker |
| 11 | Deadlock / BLOCKED threads | Misc | 🔴 | jstack "Found one Java-level deadlock"; consistent lock ordering, `tryLock` with timeout, shorter critical sections |
| 12 | Race condition / inconsistent data | Misc | 🔴 | Non-atomic check-then-act; fix with DB constraint, optimistic lock (`@Version`), `SELECT … FOR UPDATE`, atomic ops |
| 13 | Works locally, fails in prod | Misc | 🟡 | Config/env/secrets, versions, network/firewall/DNS, TLS certs, data volume, timezone/locale, profile |
| 14 | Slow DB call | Misc | 🟡 | Slow-query log, `EXPLAIN`, index, N+1, lock waits, pool saturation, fetch size/pagination |
| 15 | LazyInitializationException only in prod | Misc | 🟡 | Session closed/OSIV differences; fetch join / `@EntityGraph` / DTO projection |
| 16 | @Transactional partial save | Tech Mahindra | 🟡 | Self-invocation, private method, checked exception no rollback, wrong propagation, catch & swallow |
| 17 | Kafka consumer lag | Airtel, Wissen | 🟡 | Slow processing, rebalances, too few partitions/consumers, poison message; scale, batch, tune `max.poll.*`, DLQ |
| 18 | Stale cache / cache stampede | Misc | 🟡 | TTL, invalidate on write, single-flight / lock, jittered expiry |
| 19 | Added instances, no scaling | Misc | 🟡 | Bottleneck elsewhere (DB, lock, single partition, sticky session, shared downstream limit) |
| 20 | Container restarting without logs | Misc | 🟡 | `kubectl describe` → OOMKilled (exit 137), liveness probe failing, `logs --previous`, crash at startup |
| 21 | Dashboards green, users slow | Misc | 🟡 | Measure from client side/RUM, percentiles not averages, network/CDN/DNS, specific region/tenant |
| 22 | Intermittent timeouts | Misc | 🟡 | One bad pod/node, connection-pool, DNS, retry w/o backoff, GC; trace the slow ones |
| 23 | 401 / 404 / 503 debugging | EY, i-exceed | 🟢 | 401: token expiry/clock skew/issuer; 404: routing/gateway path/context-path/version; 503: no healthy upstream, readiness, overload/circuit open |
| 24 | App starts OK but one endpoint fails | EY | 🟡 | Missing bean/config for that path, downstream creds, lazy init, security rules, serialization |
| 25 | Inconsistent / missing logs; silent crash | Misc | 🟡 | Async appender drops, log level, MDC/correlation ID; OOM-killer (`dmesg`), swallowed exceptions, `UncaughtExceptionHandler` |
| 26 | Trace one request across services | EY | 🟡 | Correlation/trace ID propagated via headers (W3C traceparent), MDC in logs, Sleuth/Micrometer + Zipkin |
| 27 | Large file upload failing | Misc | 🟡 | Multipart limits, timeouts, stream to S3 (presigned URL), chunking, memory |
| 28 | Secrets handling | Misc | 🟢 | Vault / AWS Secrets Manager / K8s secrets, never in git/logs, rotation |

### Thread-dump walkthrough (high CPU)
```bash
top -H -p <pid>                 # find hottest thread id (decimal)
printf '%x\n' <tid>             # to hex
jstack <pid> | grep -A 20 <hex> # see its stack (nid=0x...)
```
### Typical fixes snippet — timeouts + bulkhead
```java
@Bean RestTemplate restTemplate(RestTemplateBuilder b) {
    return b.setConnectTimeout(Duration.ofSeconds(1)).setReadTimeout(Duration.ofSeconds(2)).build();
}
```

**Follow-ups:** How do you reproduce it? What would you alert on? How do you avoid recurrence (SLOs, load tests, canary, feature flags)? What do you do *first* while investigating — mitigate or diagnose?


---

## 15. Extras: Frontend, Behavioral & AI-Screening Rounds

### 15.1 Angular / React (asked mostly in full-stack roles)
| Topic | Key points | Diff |
|-------|-----------|------|
| Angular lifecycle | ngOnInit vs constructor, ngOnChanges, ngOnDestroy (unsubscribe) | 🟢 |
| Change detection | Default vs `OnPush`, signals | 🟡 |
| RxJS flattening | `switchMap` (cancel previous, search), `mergeMap` (parallel), `concatMap` (ordered), `exhaustMap` (ignore while busy – prevents double-click save) | 🟡 |
| Subscription leaks | `async` pipe, `takeUntil`, `takeUntilDestroyed` | 🟡 |
| Interceptors / guards / forms | Auth header + error handling; reactive vs template-driven | 🟡 |
| React hooks | `useEffect` deps/cleanup, `useMemo`/`useCallback`, reconciliation & keys | 🟡 |
| State | Redux vs Context; avoiding unnecessary re-renders (`memo`) | 🟡 |

### 15.2 Behavioral / HR
Prepare STAR stories (Situation, Task, Action, Result) for: toughest bug, production incident you owned, disagreement with a teammate/lead, tight deadline, why this company, biggest learning, how you use AI tools (and verify their output), career gap/notice period/salary expectation. Always be ready to explain **your project** end-to-end: architecture, your exact contribution, scale numbers, trade-offs.

### 15.3 AI-screening portals
| Portal | Format | Tips |
|--------|--------|------|
| HiperBrain | MCQ/short-answer + hard coding + AI voice interview | Time-box; speak in structured sentences |
| HYRGPT | Intro mentioning stack, AI follow-ups, editable transcript | Mention tech keywords in intro; follow-ups probe them |
| Wipro WEGA | 1-min intro, resume-based scenario questions, voice only | Look at camera, no reading, be concise |
| Karat / HackerRank | Live/online coding + design | Talk through approach, test edge cases |

### 15.4 Other recurring topics
- **Spring Batch** (10M records): chunk processing, restartability via JobRepository, skip/retry, partitioning, idempotent writers.
- **Spring AI / RAG**: embeddings + vector store + retrieval + prompt; guard against hallucination and PII leakage.
- **Design-pattern coding (Kotak/Flipkart LLD):** Strategy, Factory, Builder, Observer, Singleton; parking lot, vending machine, rate limiter, notification service.


---

## 16. Preparation Priority Checklist

### 🔥 P0 – Must know (asked by most companies)
- [ ] HashMap internals (hash, buckets, treeify, resize) & ConcurrentHashMap
- [ ] `equals`/`hashCode`, immutability, String pool, exceptions
- [ ] `synchronized` vs `ReentrantLock`, `volatile`, deadlock, ExecutorService, CompletableFuture
- [ ] Streams: groupingBy, second highest, flatMap, Optional
- [ ] `@Transactional` (propagation, rollback rules, self-invocation), N+1, lazy loading
- [ ] Spring Boot auto-configuration, bean lifecycle, `@Controller` advice
- [ ] JWT / Spring Security filter chain / OAuth2 flows
- [ ] SQL: second-highest salary, joins, group by/having, indexes
- [ ] Microservices: Saga, idempotency, circuit breaker, API gateway, outbox
- [ ] Kafka: partitions/ordering, consumer groups, duplicates, lag, DLQ, exactly-once
- [ ] Production debugging: OOM, latency spike, thread dump
- [ ] DSA basics: sliding window, two pointers, HashMap, stack, binary search

### ⭐ P1 – Should know
- [ ] GC types, JVM memory areas, tuning flags
- [ ] Redis: data types, eviction, cache-aside, stampede, distributed lock
- [ ] Payment system / rate limiter / URL shortener design
- [ ] Docker, Kubernetes (probes, HPA, rolling update), CI/CD pipeline
- [ ] LRU cache, DP basics, linked list, trees/graphs BFS/DFS
- [ ] Design patterns (Singleton, Strategy, Factory, Builder)

### 📘 P2 – Good to have
- [ ] Spring Batch, Spring AI, GraphQL, gRPC
- [ ] Angular/React basics, AWS services (S3, SQS, Lambda, RDS)
- [ ] Heavier DP, Dijkstra, topological sort

### Suggested 4-week plan
| Week | Focus |
|------|-------|
| 1 | Core Java, collections, concurrency, streams (§1–4) |
| 2 | JVM, Spring, Security, Hibernate/SQL (§5–8) |
| 3 | Microservices, Kafka, Redis, cloud, system design (§9–12) |
| 4 | DSA daily (§13), production scenarios (§14), mock interviews, project story (§15) |

---

## 17. Company Cheat-Sheet (where to focus)

| Company | Focus areas |
|---------|-------------|
| Deloitte | Saga/Kafka, AI-tool usage, production incidents, coding (brackets, LCP) |
| Airtel | Kafka, SLA/monitoring, DSA (rotated search, 3Sum), design |
| Wissen | Kafka ordering/outbox, concurrency puzzles, big-number addition, streams |
| EPAM | DSA + streams + thread pool, array tasks |
| EY | Production scenarios, 401/404 debugging, fund-transfer design |
| JPMorgan / Google / Amex | Payments, system design, hard DSA (islands, windows, combination sum) |
| Amazon / Flipkart | DSA (LRU, rain water), LLD, inventory systems |
| Kotak | DSA + LLD/design patterns |
| Cognizant / Accenture / Capgemini / Infosys / TCS / HCL | Core Java fundamentals, Spring, SQL, project explanation |
| PayPal / MasterCard / PhonePe | Idempotency, latency, concurrency, payments |
| Tech Mahindra | `@Transactional`, subset-sum DP, trailing zeros |
| Delhivery | Linked list, Floyd cycle, design |

*Compiled from the 60 company-wise files in this repository. Difficulty ratings are indicative.*
