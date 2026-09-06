# Java Core Roadmap

> Objective: build a strong Java Core foundation before moving into Spring Boot, with enough depth to eventually operate at Senior Software Engineer / Technical Lead level.

---

## 1. Introduction to Java ✅

* [x] A Short History of Java
* [x] Java's Main Characteristics

  * [x] Object-oriented
  * [x] Strongly typed
  * [x] Platform independent
  * [x] Garbage collected
* [x] JDK - JRE - JVM

  * [x] JDK - Java Development Kit
  * [x] JRE - Java Runtime Environment
  * [x] JVM - Java Virtual Machine
* [x] How Java code is executed

  * [x] Source code
  * [x] Compilation
  * [x] Bytecode
  * [x] JVM execution
* [x] Java Editions

  * [x] Java SE
  * [x] Jakarta EE
* [x] Java Versions and the LTS concept
* [x] Basic structure of a Java project
* [x] Basic idea of `.java` and `.class` files
* [x] The `main` method

---

# Part I — Java Language Fundamentals

## 2. Variables, Types and Operators

* [ ] Variables

  * [x] Declaration and initialization
  * [x] Variable scope
  * [x] Local variables
  * [x] Instance variables
  * [x] Static variables
* [ ] Primitive types

  * [x] `byte`
  * [x] `short`
  * [x] `int`
  * [x] `long`
  * [x] `float`
  * [x] `double`
  * [x] `char`
  * [x] `boolean`
* [x] Reference types
* [ ] Primitive vs reference semantics
* [ ] Default values
* [ ] Literals

  * [ ] Numeric literals
  * [ ] Character literals
  * [ ] String literals
  * [ ] Underscores in numeric literals
* [ ] Type conversion

  * [ ] Implicit conversion
  * [ ] Explicit casting
  * [ ] Widening
  * [ ] Narrowing
* [ ] Numeric overflow and underflow
* [ ] `var` and local variable type inference
* [ ] Constants with `final`
* [ ] Operators

  * [ ] Arithmetic operators
  * [ ] Assignment operators
  * [ ] Comparison operators
  * [ ] Logical operators
  * [ ] Unary operators
  * [ ] Increment and decrement
  * [ ] Bitwise operators
  * [ ] Shift operators
  * [ ] Ternary operator
  * [ ] Operator precedence
* [ ] Short-circuit evaluation
* [ ] Floating-point precision
* [ ] `BigInteger`
* [ ] `BigDecimal`

  * [ ] Why `BigDecimal` is preferable for money
  * [ ] Scale
  * [ ] Rounding modes
  * [ ] `equals()` vs `compareTo()`

---

## 3. Control Flow

* [ ] Conditional statements

  * [ ] `if`
  * [ ] `if-else`
  * [ ] `else-if`
* [ ] `switch`

  * [ ] Traditional `switch`
  * [ ] Switch expressions
  * [ ] Arrow syntax
  * [ ] `yield`
* [ ] Loops

  * [ ] `for`
  * [ ] Enhanced `for`
  * [ ] `while`
  * [ ] `do-while`
* [ ] Loop control

  * [ ] `break`
  * [ ] `continue`
  * [ ] Labeled statements
* [ ] Nested control structures
* [ ] Pattern matching basics

  * [ ] Pattern matching with `instanceof`
  * [ ] Pattern matching with `switch`

---

## 4. Methods

* [ ] Method declaration
* [ ] Parameters
* [ ] Return values
* [ ] `void`
* [ ] Method signatures
* [ ] Method overloading
* [ ] Pass-by-value semantics

  * [ ] Primitive arguments
  * [ ] Object references
  * [ ] Why Java is always pass-by-value
* [ ] Variable arguments — varargs
* [ ] Recursive methods
* [ ] Static methods
* [ ] Instance methods
* [ ] Method scope
* [ ] Method design

  * [ ] Cohesion
  * [ ] Side effects
  * [ ] Pure functions
  * [ ] Command-query separation

---

## 5. Arrays and Strings

### Arrays

* [ ] Array declaration
* [ ] Array initialization
* [ ] Accessing elements
* [ ] Array bounds
* [ ] Iterating over arrays
* [ ] Multidimensional arrays
* [ ] Arrays of objects
* [ ] `java.util.Arrays`

  * [ ] `sort()`
  * [ ] `binarySearch()`
  * [ ] `copyOf()`
  * [ ] `fill()`
  * [ ] `equals()`
  * [ ] `deepEquals()`

### Strings

* [ ] `String`
* [ ] String immutability
* [ ] The String Pool
* [ ] String literals vs `new String()`
* [ ] `==` vs `equals()`
* [ ] Common String operations
* [ ] `StringBuilder`
* [ ] `StringBuffer`
* [ ] `String` vs `StringBuilder` vs `StringBuffer`
* [ ] String concatenation
* [ ] How string concatenation is compiled
* [ ] Text Blocks
* [ ] Unicode basics
* [ ] Character encoding

  * [ ] UTF-8
  * [ ] UTF-16
* [ ] Regular expressions

  * [ ] `Pattern`
  * [ ] `Matcher`

---

# Part II — Object-Oriented Programming

## 6. Classes and Objects

* [ ] Classes
* [ ] Objects
* [ ] Fields
* [ ] Methods
* [ ] Object state and behavior
* [ ] Constructors

  * [ ] Default constructor
  * [ ] Parameterized constructors
  * [ ] Constructor overloading
  * [ ] Constructor chaining
* [ ] `this`
* [ ] `static`

  * [ ] Static fields
  * [ ] Static methods
  * [ ] Static initialization blocks
* [ ] `final`

  * [ ] Final variables
  * [ ] Final methods
  * [ ] Final classes
* [ ] Initialization order

  * [ ] Static fields
  * [ ] Static blocks
  * [ ] Instance fields
  * [ ] Instance initialization blocks
  * [ ] Constructors
* [ ] Object references
* [ ] Object identity
* [ ] Object lifecycle
* [ ] Immutability

  * [ ] Designing immutable classes
  * [ ] Defensive copies

---

## 7. Encapsulation and Access Control

* [ ] Encapsulation
* [ ] Access modifiers

  * [ ] `private`
  * [ ] package-private
  * [ ] `protected`
  * [ ] `public`
* [ ] Getters and setters
* [ ] Why exposing mutable state is dangerous
* [ ] Defensive copying
* [ ] Package boundaries
* [ ] API design and visibility

---

## 8. Inheritance and Polymorphism

* [ ] Inheritance
* [ ] `extends`
* [ ] Base classes and subclasses
* [ ] `super`
* [ ] Constructor chaining
* [ ] Method overriding
* [ ] `@Override`
* [ ] Dynamic dispatch
* [ ] Runtime polymorphism
* [ ] Upcasting
* [ ] Downcasting
* [ ] `instanceof`
* [ ] Composition vs inheritance
* [ ] The fragile base class problem
* [ ] Favor composition over inheritance
* [ ] Liskov Substitution Principle
* [ ] Covariant return types

---

## 9. Abstract Classes and Interfaces

### Abstract Classes

* [ ] Abstract classes
* [ ] Abstract methods
* [ ] Concrete methods
* [ ] Constructors in abstract classes
* [ ] State in abstract classes

### Interfaces

* [ ] Interfaces
* [ ] Interface implementation
* [ ] Multiple interface inheritance
* [ ] Default methods
* [ ] Static interface methods
* [ ] Private interface methods
* [ ] Interface constants
* [ ] Functional interfaces

### Design Decisions

* [ ] Interface vs abstract class
* [ ] Interface segregation
* [ ] Programming to an interface
* [ ] Dependency inversion basics

---

## 10. `Object`, Equality and Object Contracts

* [ ] `java.lang.Object`
* [ ] `toString()`
* [ ] `equals()`
* [ ] `hashCode()`
* [ ] `getClass()`
* [ ] `clone()` and why it is generally avoided
* [ ] Object identity vs logical equality
* [ ] `equals()` contract

  * [ ] Reflexive
  * [ ] Symmetric
  * [ ] Transitive
  * [ ] Consistent
  * [ ] Null handling
* [ ] `hashCode()` contract
* [ ] Relationship between `equals()` and `hashCode()`
* [ ] Why broken equality breaks `HashMap` and `HashSet`
* [ ] Mutable objects as hash keys

---

## 11. Enums, Records and Sealed Types

### Enums

* [ ] Enum basics
* [ ] Enum fields
* [ ] Enum constructors
* [ ] Enum methods
* [ ] Enum polymorphism
* [ ] `EnumSet`
* [ ] `EnumMap`

### Records

* [ ] Records
* [ ] Record components
* [ ] Generated methods
* [ ] Canonical constructors
* [ ] Compact constructors
* [ ] Records and immutability
* [ ] Records vs traditional classes
* [ ] Records as DTOs and value objects

### Sealed Types

* [ ] Sealed classes
* [ ] Sealed interfaces
* [ ] `sealed`
* [ ] `non-sealed`
* [ ] `permits`
* [ ] Exhaustive pattern matching
* [ ] Modeling closed domain hierarchies

---

# Part III — Error Handling

## 12. Exceptions

* [ ] Exception hierarchy

  * [ ] `Throwable`
  * [ ] `Error`
  * [ ] `Exception`
  * [ ] `RuntimeException`
* [ ] Checked exceptions
* [ ] Unchecked exceptions
* [ ] Checked vs unchecked exceptions
* [ ] `try`
* [ ] `catch`
* [ ] Multiple `catch` blocks
* [ ] Multi-catch
* [ ] `finally`
* [ ] `throw`
* [ ] `throws`
* [ ] Exception propagation
* [ ] Stack unwinding
* [ ] Stack traces
* [ ] Custom exceptions
* [ ] Exception chaining
* [ ] Exception causes
* [ ] Try-with-resources
* [ ] `AutoCloseable`
* [ ] Suppressed exceptions
* [ ] Exception handling best practices

  * [ ] Don't swallow exceptions
  * [ ] Don't catch `Exception` unnecessarily
  * [ ] Preserve exception causes
  * [ ] Translate exceptions at abstraction boundaries
  * [ ] Don't use exceptions for normal control flow

---

# Part IV — Generics and Collections

## 13. Generics

* [ ] Why generics exist
* [ ] Generic classes
* [ ] Generic interfaces
* [ ] Generic methods
* [ ] Type parameters
* [ ] Generic type inference
* [ ] Bounded type parameters

  * [ ] `<T extends X>`
* [ ] Multiple bounds
* [ ] Wildcards

  * [ ] `<?>`
  * [ ] `<? extends T>`
  * [ ] `<? super T>`
* [ ] PECS

  * [ ] Producer Extends
  * [ ] Consumer Super
* [ ] Invariance
* [ ] Generic inheritance
* [ ] Type erasure
* [ ] Bridge methods
* [ ] Runtime limitations of generics
* [ ] Why `new T()` is not allowed
* [ ] Why generic arrays are problematic
* [ ] Heap pollution
* [ ] Raw types
* [ ] Generic API design

---

## 14. Java Collections Framework

### Foundations

* [ ] Collections Framework architecture
* [ ] `Iterable`
* [ ] `Collection`
* [ ] `Iterator`
* [ ] `ListIterator`
* [ ] Fail-fast iterators
* [ ] `ConcurrentModificationException`

### List

* [ ] `List`
* [ ] `ArrayList`
* [ ] `LinkedList`
* [ ] ArrayList internals

  * [ ] Backing array
  * [ ] Capacity growth
* [ ] LinkedList internals
* [ ] Complexity trade-offs
* [ ] When to use each implementation

### Set

* [ ] `Set`
* [ ] `HashSet`
* [ ] `LinkedHashSet`
* [ ] `TreeSet`
* [ ] Duplicate detection
* [ ] Ordering guarantees

### Map

* [ ] `Map`
* [ ] `HashMap`
* [ ] `LinkedHashMap`
* [ ] `TreeMap`
* [ ] HashMap internals

  * [ ] Hashing
  * [ ] Buckets
  * [ ] Collisions
  * [ ] Bucket treeification
  * [ ] Capacity
  * [ ] Load factor
  * [ ] Resizing
* [ ] HashMap and `equals/hashCode`
* [ ] Null keys and values
* [ ] Ordering guarantees

### Queue and Deque

* [ ] `Queue`
* [ ] `Deque`
* [ ] `ArrayDeque`
* [ ] `PriorityQueue`
* [ ] Heap-based priority queues

### Utilities

* [ ] `Collections`
* [ ] Sorting
* [ ] Searching
* [ ] Shuffling
* [ ] Unmodifiable collections
* [ ] Immutable collection factories

  * [ ] `List.of()`
  * [ ] `Set.of()`
  * [ ] `Map.of()`
* [ ] `Comparable`
* [ ] `Comparator`
* [ ] Natural ordering
* [ ] Comparator chaining
* [ ] Time complexity of common collection operations
* [ ] Memory trade-offs between collection implementations

---

# Part V — Functional Java

## 15. Lambdas and Functional Interfaces

* [ ] Lambda expressions
* [ ] Lambda syntax
* [ ] Target typing
* [ ] Effectively final variables
* [ ] Capturing variables
* [ ] Method references

  * [ ] Static method references
  * [ ] Instance method references
  * [ ] Constructor references
* [ ] Functional interfaces
* [ ] `@FunctionalInterface`
* [ ] Core functional interfaces

  * [ ] `Predicate<T>`
  * [ ] `Function<T,R>`
  * [ ] `Consumer<T>`
  * [ ] `Supplier<T>`
  * [ ] `UnaryOperator<T>`
  * [ ] `BinaryOperator<T>`
* [ ] Primitive specializations
* [ ] Function composition

  * [ ] `andThen()`
  * [ ] `compose()`
  * [ ] Predicate composition

---

## 16. Streams API

### Stream Fundamentals

* [ ] What a Stream is
* [ ] Stream vs Collection
* [ ] Stream pipelines
* [ ] Stream sources
* [ ] Intermediate operations
* [ ] Terminal operations
* [ ] Lazy evaluation
* [ ] Internal iteration
* [ ] Single-use streams

### Operations

* [ ] `filter()`
* [ ] `map()`
* [ ] `flatMap()`
* [ ] `distinct()`
* [ ] `sorted()`
* [ ] `limit()`
* [ ] `skip()`
* [ ] `peek()`
* [ ] `forEach()`
* [ ] `reduce()`
* [ ] `collect()`
* [ ] `findFirst()`
* [ ] `findAny()`
* [ ] `anyMatch()`
* [ ] `allMatch()`
* [ ] `noneMatch()`
* [ ] `count()`

### Collectors

* [ ] `Collectors.toList()`
* [ ] `Collectors.toSet()`
* [ ] `Collectors.toMap()`
* [ ] `joining()`
* [ ] `groupingBy()`
* [ ] `partitioningBy()`
* [ ] `mapping()`
* [ ] `counting()`
* [ ] `summarizing*()`
* [ ] Downstream collectors

### Advanced Streams

* [ ] Primitive streams

  * [ ] `IntStream`
  * [ ] `LongStream`
  * [ ] `DoubleStream`
* [ ] Boxing and unboxing costs
* [ ] Parallel streams
* [ ] Fork/Join integration
* [ ] Spliterators
* [ ] Stream performance
* [ ] Side effects in streams
* [ ] Stateful operations
* [ ] When not to use Streams

---

## 17. `Optional`

* [ ] Purpose of `Optional`
* [ ] `Optional.of()`
* [ ] `Optional.ofNullable()`
* [ ] `Optional.empty()`
* [ ] `isPresent()`
* [ ] `isEmpty()`
* [ ] `ifPresent()`
* [ ] `map()`
* [ ] `flatMap()`
* [ ] `filter()`
* [ ] `orElse()`
* [ ] `orElseGet()`
* [ ] `orElseThrow()`
* [ ] Eager vs lazy fallback evaluation
* [ ] Optional chaining
* [ ] Proper use of `Optional`
* [ ] Why `Optional` fields are usually discouraged
* [ ] Why `Optional` parameters are usually discouraged
* [ ] `Optional` vs null

---

# Part VI — Date, Time and Utility APIs

## 18. Date and Time API

* [ ] Problems with legacy `Date` and `Calendar`
* [ ] `java.time`
* [ ] `LocalDate`
* [ ] `LocalTime`
* [ ] `LocalDateTime`
* [ ] `Instant`
* [ ] `ZonedDateTime`
* [ ] `OffsetDateTime`
* [ ] `ZoneId`
* [ ] `ZoneOffset`
* [ ] `Duration`
* [ ] `Period`
* [ ] `DateTimeFormatter`
* [ ] Parsing and formatting dates
* [ ] Time zones
* [ ] UTC
* [ ] Daylight Saving Time
* [ ] Epoch timestamps
* [ ] Choosing the correct temporal type
* [ ] Date/time persistence considerations

---

## 19. Useful Java Standard Library APIs

* [ ] Wrapper classes

  * [ ] `Integer`
  * [ ] `Long`
  * [ ] `Double`
  * [ ] `Boolean`
* [ ] Autoboxing
* [ ] Unboxing
* [ ] Wrapper caching
* [ ] `Math`
* [ ] `Objects`

  * [ ] `requireNonNull()`
  * [ ] `equals()`
  * [ ] `hash()`
* [ ] `UUID`
* [ ] `Random`
* [ ] `SecureRandom`
* [ ] `Base64`
* [ ] `Locale`
* [ ] `Currency`
* [ ] `Properties`

---

# Part VII — I/O and Data

## 20. Java I/O

### Classic I/O

* [ ] `java.io`
* [ ] Byte streams

  * [ ] `InputStream`
  * [ ] `OutputStream`
* [ ] Character streams

  * [ ] `Reader`
  * [ ] `Writer`
* [ ] Buffered streams
* [ ] File streams
* [ ] Input/output decorators
* [ ] Resource management

### NIO and NIO.2

* [ ] `java.nio`
* [ ] `Path`
* [ ] `Paths`
* [ ] `Files`
* [ ] Reading files
* [ ] Writing files
* [ ] Copying files
* [ ] Moving files
* [ ] Deleting files
* [ ] Directory traversal
* [ ] File attributes
* [ ] `ByteBuffer`
* [ ] Channels
* [ ] Buffers
* [ ] Non-blocking I/O basics
* [ ] Selectors
* [ ] Classic I/O vs NIO

---

## 21. Serialization

* [ ] Java object serialization
* [ ] `Serializable`
* [ ] `serialVersionUID`
* [ ] `transient`
* [ ] Serialization lifecycle
* [ ] Security problems with native Java serialization
* [ ] Why native Java serialization should usually be avoided
* [ ] Serialization vs data interchange formats
* [ ] Conceptual relationship with JSON
* [ ] DTOs and serialization boundaries

---

# Part VIII — Concurrency and Parallelism

## 22. Thread Fundamentals

* [ ] Processes vs threads
* [ ] Java threads
* [ ] Thread lifecycle
* [ ] Thread states
* [ ] Creating threads

  * [ ] Extending `Thread`
  * [ ] Implementing `Runnable`
* [ ] `start()` vs `run()`
* [ ] `sleep()`
* [ ] `join()`
* [ ] `interrupt()`
* [ ] Interruption policy
* [ ] Daemon threads
* [ ] Thread scheduling
* [ ] Context switching
* [ ] Race conditions
* [ ] Thread safety
* [ ] Atomicity
* [ ] Visibility
* [ ] Ordering

---

## 23. Java Memory Model and Synchronization

* [ ] Java Memory Model — JMM
* [ ] Main memory vs CPU caches
* [ ] Happens-before relationship
* [ ] Memory visibility
* [ ] Instruction reordering
* [ ] `synchronized`
* [ ] Intrinsic locks / monitors
* [ ] Reentrant synchronization
* [ ] `volatile`
* [ ] Atomicity vs visibility
* [ ] `wait()`
* [ ] `notify()`
* [ ] `notifyAll()`
* [ ] Spurious wakeups
* [ ] Deadlock
* [ ] Livelock
* [ ] Starvation
* [ ] Safe publication
* [ ] Immutability for thread safety
* [ ] Double-checked locking

---

## 24. Modern Java Concurrency

### Executors

* [ ] `Executor`
* [ ] `ExecutorService`
* [ ] Thread pools
* [ ] Fixed thread pools
* [ ] Cached thread pools
* [ ] Scheduled executors
* [ ] Pool sizing
* [ ] Queueing strategies
* [ ] Graceful shutdown

### Futures

* [ ] `Callable`
* [ ] `Future`
* [ ] Cancellation
* [ ] Timeouts

### CompletableFuture

* [ ] `CompletableFuture`
* [ ] `supplyAsync()`
* [ ] `runAsync()`
* [ ] `thenApply()`
* [ ] `thenCompose()`
* [ ] `thenCombine()`
* [ ] `allOf()`
* [ ] `anyOf()`
* [ ] Error handling
* [ ] Async execution
* [ ] Custom executors

### Locks and Synchronizers

* [ ] `Lock`
* [ ] `ReentrantLock`
* [ ] `ReadWriteLock`
* [ ] `StampedLock`
* [ ] `Semaphore`
* [ ] `CountDownLatch`
* [ ] `CyclicBarrier`
* [ ] `Phaser`

### Atomic Types

* [ ] `AtomicInteger`
* [ ] `AtomicLong`
* [ ] `AtomicReference`
* [ ] Compare-and-swap — CAS
* [ ] `LongAdder`

---

## 25. Concurrent Collections

* [ ] `ConcurrentHashMap`
* [ ] `CopyOnWriteArrayList`
* [ ] `CopyOnWriteArraySet`
* [ ] `ConcurrentLinkedQueue`
* [ ] `BlockingQueue`
* [ ] `ArrayBlockingQueue`
* [ ] `LinkedBlockingQueue`
* [ ] Concurrent collections vs synchronized wrappers
* [ ] Weakly consistent iterators
* [ ] Producer-consumer patterns

---

## 26. Virtual Threads

* [ ] Platform threads
* [ ] Virtual threads
* [ ] Project Loom
* [ ] Creating virtual threads
* [ ] Virtual thread executors
* [ ] Blocking I/O with virtual threads
* [ ] Thread-per-request model
* [ ] Virtual threads vs thread pools
* [ ] Pinning
* [ ] Thread-local considerations
* [ ] CPU-bound vs I/O-bound workloads
* [ ] When virtual threads help
* [ ] When virtual threads do not help
* [ ] Relationship with Spring Boot

---

# Part IX — JVM Internals

## 27. JVM Memory Model

* [ ] JVM runtime data areas
* [ ] Heap
* [ ] Stack
* [ ] Stack frames
* [ ] Program Counter
* [ ] Native Method Stack
* [ ] Metaspace
* [ ] Object allocation
* [ ] Object headers
* [ ] References
* [ ] Escape analysis
* [ ] Stack vs heap misconceptions
* [ ] `StackOverflowError`
* [ ] `OutOfMemoryError`

---

## 28. Garbage Collection

* [ ] Garbage Collection fundamentals
* [ ] Reachability
* [ ] GC Roots
* [ ] Strong references
* [ ] Soft references
* [ ] Weak references
* [ ] Phantom references
* [ ] Generational hypothesis
* [ ] Young generation
* [ ] Old generation
* [ ] Minor vs major/full collections
* [ ] Stop-the-world pauses
* [ ] Common garbage collectors

  * [ ] Serial GC
  * [ ] Parallel GC
  * [ ] G1 GC
  * [ ] ZGC
* [ ] GC throughput vs latency
* [ ] Memory leaks in garbage-collected languages
* [ ] Common sources of Java memory leaks
* [ ] Basic GC logs interpretation

---

## 29. Class Loading

* [ ] Class loading lifecycle

  * [ ] Loading
  * [ ] Linking
  * [ ] Verification
  * [ ] Preparation
  * [ ] Resolution
  * [ ] Initialization
* [ ] Class loaders

  * [ ] Bootstrap ClassLoader
  * [ ] Platform ClassLoader
  * [ ] Application ClassLoader
* [ ] Parent delegation model
* [ ] Custom class loaders
* [ ] Class identity
* [ ] Static initialization
* [ ] `ClassNotFoundException`
* [ ] `NoClassDefFoundError`

---

## 30. Bytecode and JIT Compilation

* [ ] Java bytecode
* [ ] JVM instructions
* [ ] `javap`
* [ ] Interpreted execution
* [ ] Just-In-Time compilation
* [ ] Hot methods
* [ ] Tiered compilation
* [ ] C1 compiler
* [ ] C2 compiler
* [ ] Method inlining
* [ ] Escape analysis
* [ ] Dead code elimination
* [ ] Deoptimization
* [ ] Why microbenchmarks are difficult on the JVM

---

# Part X — Metadata and Runtime Introspection

## 31. Annotations

* [ ] Annotation syntax
* [ ] Built-in annotations

  * [ ] `@Override`
  * [ ] `@Deprecated`
  * [ ] `@SuppressWarnings`
  * [ ] `@FunctionalInterface`
* [ ] Custom annotations
* [ ] Meta-annotations

  * [ ] `@Target`
  * [ ] `@Retention`
  * [ ] `@Documented`
  * [ ] `@Inherited`
  * [ ] `@Repeatable`
* [ ] Retention policies

  * [ ] `SOURCE`
  * [ ] `CLASS`
  * [ ] `RUNTIME`
* [ ] Annotation processing basics
* [ ] Runtime annotations
* [ ] How frameworks use annotations
* [ ] Relationship with Spring

---

## 32. Reflection

* [ ] Reflection API
* [ ] `Class<?>`
* [ ] Obtaining `Class` objects
* [ ] Inspecting fields
* [ ] Inspecting methods
* [ ] Inspecting constructors
* [ ] Invoking methods dynamically
* [ ] Creating instances dynamically
* [ ] Access modifiers and reflection
* [ ] Reflection performance
* [ ] Reflection security implications
* [ ] Reflection and encapsulation
* [ ] Reflection in frameworks
* [ ] Relationship with Dependency Injection
* [ ] Relationship with Spring

---

# Part XI — Packages, Modules and Application Structure

## 33. Packages and Imports

* [ ] Packages
* [ ] Package naming conventions
* [ ] Imports
* [ ] Static imports
* [ ] Fully qualified class names
* [ ] Package-private visibility
* [ ] Organizing code by package
* [ ] Package by layer vs package by feature
* [ ] Dependency direction between packages

---

## 34. Java Module System

* [ ] Java Platform Module System — JPMS
* [ ] `module-info.java`
* [ ] Named modules
* [ ] Unnamed modules
* [ ] Automatic modules
* [ ] `requires`
* [ ] `exports`
* [ ] `opens`
* [ ] `uses`
* [ ] `provides`
* [ ] Strong encapsulation
* [ ] Module path vs classpath
* [ ] JPMS trade-offs
* [ ] JPMS in real-world backend applications

---

# Part XII — Build and Dependency Management

## 35. Maven

* [ ] Why build tools exist
* [ ] Maven project structure
* [ ] `pom.xml`
* [ ] Coordinates

  * [ ] `groupId`
  * [ ] `artifactId`
  * [ ] `version`
* [ ] Dependencies
* [ ] Transitive dependencies
* [ ] Dependency scopes

  * [ ] `compile`
  * [ ] `provided`
  * [ ] `runtime`
  * [ ] `test`
* [ ] Maven lifecycle
* [ ] Maven phases

  * [ ] `clean`
  * [ ] `compile`
  * [ ] `test`
  * [ ] `package`
  * [ ] `verify`
  * [ ] `install`
  * [ ] `deploy`
* [ ] Maven plugins
* [ ] Dependency management
* [ ] BOMs
* [ ] Parent POMs
* [ ] Multi-module projects
* [ ] Maven Wrapper
* [ ] Dependency conflicts
* [ ] Dependency mediation
* [ ] `dependency:tree`
* [ ] Reproducible builds

---

## 36. Gradle — Conceptual Knowledge

* [ ] Gradle fundamentals
* [ ] Gradle Wrapper
* [ ] Build scripts
* [ ] Groovy DSL
* [ ] Kotlin DSL
* [ ] Dependencies
* [ ] Tasks
* [ ] Plugins
* [ ] Multi-project builds
* [ ] Maven vs Gradle
* [ ] Know how to read and maintain a basic Gradle project

> Maven can be the primary build tool. Gradle should at minimum be understood well enough to work in an existing project.

---

# Part XIII — Testing

## 37. Unit Testing with JUnit

* [ ] Testing fundamentals
* [ ] Unit testing
* [ ] Test isolation
* [ ] JUnit 5
* [ ] `@Test`
* [ ] Assertions
* [ ] `assertThrows()`
* [ ] `@BeforeEach`
* [ ] `@AfterEach`
* [ ] `@BeforeAll`
* [ ] `@AfterAll`
* [ ] Parameterized tests
* [ ] Nested tests
* [ ] Test lifecycle
* [ ] Test naming
* [ ] Arrange-Act-Assert
* [ ] GIVEN-WHEN-THEN
* [ ] Boundary testing
* [ ] Happy paths vs edge cases
* [ ] Testing exceptions
* [ ] Testing immutable/value objects

---

## 38. Mocking with Mockito

* [ ] Test doubles

  * [ ] Dummy
  * [ ] Stub
  * [ ] Spy
  * [ ] Mock
  * [ ] Fake
* [ ] Mockito
* [ ] `mock()`
* [ ] `@Mock`
* [ ] `@InjectMocks`
* [ ] `when()`
* [ ] `thenReturn()`
* [ ] `verify()`
* [ ] Argument matchers
* [ ] Argument captors
* [ ] Stubbing exceptions
* [ ] Mocking void methods
* [ ] Spies
* [ ] Mocking vs real collaborators
* [ ] Overmocking
* [ ] Testing behavior vs implementation details
* [ ] When mocking is a design smell

---

## 39. Testing Strategy

* [ ] Unit tests
* [ ] Integration tests
* [ ] End-to-end tests
* [ ] Test pyramid
* [ ] Test coverage
* [ ] Coverage limitations
* [ ] Deterministic tests
* [ ] Flaky tests
* [ ] Test fixtures
* [ ] Test data builders
* [ ] Testing concurrency
* [ ] Testing asynchronous code
* [ ] Test maintainability

---

# Part XIV — Database Access

## 40. JDBC

* [ ] JDBC architecture
* [ ] JDBC drivers
* [ ] `Connection`
* [ ] `Statement`
* [ ] `PreparedStatement`
* [ ] `CallableStatement`
* [ ] `ResultSet`
* [ ] Parameterized queries
* [ ] SQL injection prevention
* [ ] Transactions
* [ ] `commit()`
* [ ] `rollback()`
* [ ] Auto-commit
* [ ] Transaction isolation
* [ ] Batch operations
* [ ] Generated keys
* [ ] Resource management
* [ ] Try-with-resources with JDBC
* [ ] Connection pools
* [ ] Why opening a DB connection is expensive
* [ ] JDBC vs ORM
* [ ] Relationship with Spring JDBC
* [ ] Relationship with JPA/Hibernate

---

# Part XV — Networking

## 41. Networking Fundamentals in Java

* [ ] TCP vs UDP
* [ ] IP addresses
* [ ] Ports
* [ ] Client-server model
* [ ] Sockets
* [ ] `Socket`
* [ ] `ServerSocket`
* [ ] HTTP fundamentals from Java's perspective
* [ ] Java HTTP Client

  * [ ] `HttpClient`
  * [ ] `HttpRequest`
  * [ ] `HttpResponse`
* [ ] Synchronous HTTP
* [ ] Asynchronous HTTP
* [ ] Connection reuse
* [ ] Timeouts
* [ ] TLS basics
* [ ] DNS basics
* [ ] Why network calls are fundamentally unreliable

---

# Part XVI — Java API and Code Design

## 42. Java Coding Conventions and API Design

* [ ] Java naming conventions
* [ ] Class naming
* [ ] Method naming
* [ ] Constant naming
* [ ] Package naming
* [ ] Small methods
* [ ] High cohesion
* [ ] Low coupling
* [ ] Tell, Don't Ask
* [ ] Law of Demeter
* [ ] Fail fast
* [ ] Defensive programming
* [ ] Null handling
* [ ] Preconditions
* [ ] Postconditions
* [ ] Invariants
* [ ] Designing immutable APIs
* [ ] Designing extension points
* [ ] Backward compatibility
* [ ] API contracts

---

## 43. SOLID Principles in Java

* [ ] Single Responsibility Principle
* [ ] Open/Closed Principle
* [ ] Liskov Substitution Principle
* [ ] Interface Segregation Principle
* [ ] Dependency Inversion Principle
* [ ] Recognizing SOLID violations
* [ ] Knowing when applying SOLID adds unnecessary complexity

---

## 44. Object-Oriented Design Principles

* [ ] Composition over inheritance
* [ ] Encapsulate what varies
* [ ] Program to interfaces
* [ ] Favor immutability
* [ ] Separation of concerns
* [ ] Information hiding
* [ ] Dependency management
* [ ] Coupling and cohesion
* [ ] Anemic domain model
* [ ] Rich domain model
* [ ] Value Objects
* [ ] Entities
* [ ] Domain invariants
* [ ] Avoiding primitive obsession
* [ ] Tell, Don't Ask

---

## 45. Common Design Patterns in Java

### Creational

* [ ] Singleton
* [ ] Factory Method
* [ ] Abstract Factory
* [ ] Builder
* [ ] Prototype

### Structural

* [ ] Adapter
* [ ] Decorator
* [ ] Facade
* [ ] Proxy
* [ ] Composite

### Behavioral

* [ ] Strategy
* [ ] Observer
* [ ] Template Method
* [ ] Command
* [ ] Chain of Responsibility
* [ ] State

### Java-specific Perspective

* [ ] Identify patterns in Java's standard library
* [ ] Know when a pattern is unnecessary
* [ ] Prefer simple language features when they solve the same problem
* [ ] Understand how Spring uses common design patterns

---

# Part XVII — Security Fundamentals

## 46. Java Security Basics

* [ ] Secure coding principles
* [ ] Input validation
* [ ] Output encoding
* [ ] SQL injection
* [ ] Path traversal
* [ ] Command injection
* [ ] Unsafe deserialization
* [ ] Secrets management
* [ ] Environment variables
* [ ] Cryptography fundamentals

  * [ ] Hashing
  * [ ] Encryption
  * [ ] Digital signatures
* [ ] `MessageDigest`
* [ ] `SecureRandom`
* [ ] Why passwords should not be encrypted or directly hashed
* [ ] TLS fundamentals
* [ ] Certificate basics
* [ ] Java KeyStore basics
* [ ] Dependency vulnerabilities
* [ ] Principle of least privilege

---

# Part XVIII — Performance and Diagnostics

## 47. Java Performance Fundamentals

* [ ] Latency vs throughput
* [ ] CPU-bound vs I/O-bound workloads
* [ ] Memory allocation costs
* [ ] Garbage collection costs
* [ ] Object allocation
* [ ] Boxing/unboxing overhead
* [ ] String allocation
* [ ] Collection performance
* [ ] Algorithmic complexity
* [ ] Big O notation

  * [ ] O(1)
  * [ ] O(log n)
  * [ ] O(n)
  * [ ] O(n log n)
  * [ ] O(n²)
* [ ] Premature optimization
* [ ] Measure before optimizing
* [ ] Performance vs readability
* [ ] Performance vs memory trade-offs

---

## 48. Profiling and JVM Diagnostics

* [ ] JVM diagnostic tools
* [ ] `jps`
* [ ] `jstack`
* [ ] `jmap`
* [ ] `jcmd`
* [ ] `jstat`
* [ ] Thread dumps
* [ ] Heap dumps
* [ ] Reading thread states
* [ ] Detecting deadlocks
* [ ] Memory leak investigation
* [ ] CPU profiling
* [ ] Allocation profiling
* [ ] Java Flight Recorder — JFR
* [ ] Java Mission Control — JMC
* [ ] Basic GC log analysis
* [ ] Basic production troubleshooting workflow

---

## 49. Benchmarking with JMH

* [ ] Why normal Java microbenchmarks are unreliable
* [ ] JIT warmup
* [ ] Dead-code elimination
* [ ] Constant folding
* [ ] JVM optimizations affecting benchmarks
* [ ] Java Microbenchmark Harness — JMH
* [ ] Warmup iterations
* [ ] Measurement iterations
* [ ] Forks
* [ ] Benchmark state
* [ ] `Blackhole`
* [ ] Interpreting benchmark results

---

# Part XIX — Packaging and Runtime

## 50. JARs and Java Application Packaging

* [ ] JAR files
* [ ] JAR structure
* [ ] Manifest
* [ ] `META-INF`
* [ ] Executable JARs
* [ ] Classpath
* [ ] Module path
* [ ] Dependency JARs
* [ ] Fat/Uber JAR concept
* [ ] Thin JAR concept
* [ ] `jar` command
* [ ] Running applications with `java -jar`
* [ ] JVM arguments
* [ ] System properties
* [ ] Environment variables
* [ ] Application configuration basics

---

# Part XX — Advanced Java Topics

## 51. Nested and Inner Classes

* [ ] Static nested classes
* [ ] Inner classes
* [ ] Local classes
* [ ] Anonymous classes
* [ ] Capturing enclosing state
* [ ] Lambda expressions vs anonymous classes

---

## 52. Advanced Language Features

* [ ] Pattern matching
* [ ] Pattern matching for `instanceof`
* [ ] Pattern matching for `switch`
* [ ] Record patterns
* [ ] Switch exhaustiveness
* [ ] Sealed hierarchies with pattern matching
* [ ] Text blocks
* [ ] Modern Java language evolution
* [ ] Recognizing preview features
* [ ] Preview vs permanent features
* [ ] Avoiding unnecessary dependence on preview features

---

## 53. Service Provider Interface — SPI

* [ ] Java SPI concept
* [ ] `ServiceLoader`
* [ ] Service providers
* [ ] Provider discovery
* [ ] Decoupling implementations
* [ ] SPI and modular applications
* [ ] Examples of SPI usage in the Java ecosystem

---

# Part XXI — Engineering Practices

## 54. Logging

* [ ] Logging vs `System.out.println`
* [ ] Logging levels

  * [ ] TRACE
  * [ ] DEBUG
  * [ ] INFO
  * [ ] WARN
  * [ ] ERROR
* [ ] Structured logging concepts
* [ ] Parameterized logging
* [ ] Avoiding expensive log construction
* [ ] Exception logging
* [ ] Avoiding duplicate exception logging
* [ ] Sensitive information in logs
* [ ] SLF4J concept
* [ ] Logback concept
* [ ] `java.util.logging` overview
* [ ] Correlation IDs concept

---

## 55. Code Quality and Static Analysis

* [ ] Compiler warnings
* [ ] `@SuppressWarnings`
* [ ] Static analysis concepts
* [ ] Checkstyle
* [ ] PMD
* [ ] SpotBugs
* [ ] SonarQube concepts
* [ ] Code smells
* [ ] Dead code
* [ ] Cyclomatic complexity
* [ ] Duplication
* [ ] Technical debt
* [ ] Refactoring

  * [ ] Extract Method
  * [ ] Extract Class
  * [ ] Rename
  * [ ] Move Method
  * [ ] Replace Conditional with Polymorphism
* [ ] Refactoring with tests

---

## 56. Debugging

* [ ] IDE breakpoints
* [ ] Conditional breakpoints
* [ ] Stepping into methods
* [ ] Stepping over methods
* [ ] Stepping out
* [ ] Watches
* [ ] Variable inspection
* [ ] Evaluating expressions
* [ ] Exception breakpoints
* [ ] Remote debugging basics
* [ ] Reading stack traces
* [ ] Finding root causes instead of symptoms

---

# Part XXII — Senior-Level Java Understanding

## 57. Java Design Trade-offs

* [ ] Mutable vs immutable objects
* [ ] Inheritance vs composition
* [ ] Interface vs abstract class
* [ ] Checked vs unchecked exceptions
* [ ] Streams vs loops
* [ ] Collections choice by workload
* [ ] Synchronous vs asynchronous execution
* [ ] Threads vs virtual threads
* [ ] Locks vs atomic operations
* [ ] Object-oriented vs functional approaches
* [ ] Reflection vs explicit APIs
* [ ] Performance vs maintainability
* [ ] Abstraction vs complexity
* [ ] Generic/reusable design vs YAGNI

---

## 58. Reading and Reasoning About Production Java

* [ ] Trace an execution path through unfamiliar code
* [ ] Identify object ownership
* [ ] Identify mutation points
* [ ] Identify thread-safety risks
* [ ] Identify exception boundaries
* [ ] Identify transaction boundaries conceptually
* [ ] Detect excessive coupling
* [ ] Detect hidden side effects
* [ ] Detect N+1-style design problems conceptually
* [ ] Detect resource leaks
* [ ] Detect unnecessary allocations
* [ ] Detect blocking operations
* [ ] Understand stack traces from production
* [ ] Read third-party Java library code when necessary
* [ ] Navigate JDK source code

---

## 59. Java Architecture Fundamentals

* [ ] Layered architecture
* [ ] Dependency direction
* [ ] Separation of concerns
* [ ] Domain layer
* [ ] Application/service layer
* [ ] Infrastructure layer
* [ ] Presentation/API layer
* [ ] Ports and adapters concept
* [ ] Hexagonal architecture concept
* [ ] Clean Architecture concept
* [ ] Dependency inversion at architectural level
* [ ] DTO vs domain object
* [ ] Mapping between layers
* [ ] Avoiding framework leakage into domain code
* [ ] Package organization
* [ ] Modular monolith fundamentals

---

# Part XXIII — Practical Milestones

## 60. Java Core Projects

### Project 1 — CLI Application

* [ ] Build a non-trivial CLI application
* [ ] Object-oriented model
* [ ] Collections
* [ ] Exceptions
* [ ] File persistence
* [ ] Unit tests
* [ ] Maven build

Suggested examples:

* Expense tracker
* Task manager
* Library management system
* Inventory system

### Project 2 — Concurrent Application

* [ ] ExecutorService
* [ ] CompletableFuture
* [ ] Synchronization
* [ ] Concurrent collections
* [ ] Graceful shutdown
* [ ] Error handling
* [ ] Unit tests

Suggested examples:

* Concurrent file processor
* URL checker
* Parallel data importer

### Project 3 — JDBC Application

* [ ] Relational database
* [ ] JDBC
* [ ] Connection pooling
* [ ] Transactions
* [ ] Repository pattern
* [ ] Unit tests
* [ ] Integration tests

Suggested examples:

* Banking ledger
* Order management
* Booking system

### Project 4 — Production-style Java Application

* [ ] Layered or hexagonal architecture
* [ ] Domain model
* [ ] Dependency inversion
* [ ] Persistence
* [ ] Logging
* [ ] Validation
* [ ] Error handling
* [ ] Configuration
* [ ] Unit tests
* [ ] Integration tests
* [ ] Maven multi-module structure if justified
* [ ] Profiling
* [ ] Documentation

---

# Java Core Completion Gate

Before moving seriously into Spring Boot, I should be able to explain and use without depending heavily on tutorials:

* [ ] OOP and Java object semantics
* [ ] `equals()` / `hashCode()` contracts
* [ ] Generics and PECS
* [ ] Collections and their internal trade-offs
* [ ] HashMap internals
* [ ] Exception design
* [ ] Lambdas and functional interfaces
* [ ] Streams and collectors
* [ ] `Optional`
* [ ] Date/Time API
* [ ] File I/O and NIO
* [ ] Threads and race conditions
* [ ] Java Memory Model
* [ ] `synchronized` and `volatile`
* [ ] Executors
* [ ] CompletableFuture
* [ ] Concurrent collections
* [ ] Virtual threads
* [ ] JVM memory areas
* [ ] Garbage collection fundamentals
* [ ] Class loading
* [ ] JIT compilation fundamentals
* [ ] Annotations
* [ ] Reflection
* [ ] Maven
* [ ] JUnit
* [ ] Mockito
* [ ] JDBC
* [ ] Logging
* [ ] Basic JVM diagnostics
* [ ] SOLID and object-oriented design
* [ ] Common design patterns
* [ ] Performance trade-offs
* [ ] Read and debug unfamiliar Java code
* [ ] Build a complete Java application without Spring

---

# Recommended Learning Order

```text
1.  Introduction to Java
        ↓
2.  Language Fundamentals
        ↓
3.  Object-Oriented Programming
        ↓
4.  Exceptions
        ↓
5.  Generics
        ↓
6.  Collections
        ↓
7.  Lambdas
        ↓
8.  Streams + Optional
        ↓
9.  Date/Time + Standard Library
        ↓
10. I/O + NIO
        ↓
11. Maven
        ↓
12. JUnit + Mockito
        ↓
13. JDBC
        ↓
14. Concurrency
        ↓
15. Virtual Threads
        ↓
16. JVM Internals
        ↓
17. Annotations + Reflection
        ↓
18. Networking
        ↓
19. SOLID + Design Patterns
        ↓
20. Security + Performance + Diagnostics
        ↓
21. Architecture Fundamentals
        ↓
22. Production-style Java Project
        ↓
                SPRING BOOT
```

---

# Priority Levels

## P0 — Essential before Spring Boot

* [ ] Java syntax and type system
* [ ] OOP
* [ ] Exceptions
* [ ] Generics
* [ ] Collections
* [ ] Lambdas
* [ ] Streams
* [ ] Optional
* [ ] Date/Time API
* [ ] Annotations
* [ ] Reflection fundamentals
* [ ] Maven
* [ ] JUnit
* [ ] Mockito
* [ ] JDBC fundamentals
* [ ] Basic concurrency
* [ ] Basic JVM understanding

## P1 — Essential for Senior Java

* [ ] Collections internals
* [ ] Java Memory Model
* [ ] Advanced concurrency
* [ ] CompletableFuture
* [ ] Virtual threads
* [ ] JVM memory management
* [ ] Garbage Collection
* [ ] Class loading
* [ ] JIT
* [ ] Performance diagnostics
* [ ] SOLID
* [ ] Design patterns
* [ ] API design
* [ ] Security fundamentals
* [ ] Testing strategy
* [ ] Architecture fundamentals

## P2 — Advanced / deepen progressively

* [ ] JPMS
* [ ] SPI
* [ ] Bytecode analysis
* [ ] JMH
* [ ] Advanced NIO
* [ ] Custom ClassLoaders
* [ ] Advanced JVM tuning
* [ ] Advanced GC analysis
* [ ] Advanced profiling
* [ ] Low-level concurrency mechanisms
