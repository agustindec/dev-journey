# Variables, Type and Operators

## Variables

Variables in Java are named references to data used by a program. Every variable has a compile-time type, a lifetime, and a scope that determines where it can be accessed.  
Understanding these distinctions becomes important in larger systems because the kind of variable you choose affects object state, concurrency, memory retention, testability, and API design.

### Declaration and initialization

A variable declaration introduces a variable to the compiler by spicifying its type and name. Initialization assigns its first value. Java is statically and strongly typed: once a variable is declared with a type, assignments must be compatible with that type according to Java's type system.

```Java
int age;                // Declaration
age = 30;               // Initialization

String name = "Alice";  // Declaration + initialization
```

For primitive variables, the variable contains the primitive value itself. For reference types, the variable contains a reference to an object rather than the object itself.

```Java
int count = 10;

User user = new User("Alice");
```

Conceptually:

```text
count
 └── 10

user
 └── reference ─────► User object
                       name = "Alice"
```

Initialization rules depend on where the variable is declared. Fields - instance and static variables - receive JVM-defined default values such as `0`, `false`, and `null`. Local variables do not receive automatic initialization and must be definitely assigned before they are read. The compiler performs this "definite assignment" analysis at compile time.

```Java
void example() {
  int x;

  // System.out.println(x);
  // Compile-time error: x might not have been initialized

  x = 10;
  System.out.println(x);
}
```

A common mistake is to assume that every variable receives a default value. Only fields do. Explicit initialization is often preferable even when a default exists because it makes intent visible. Also distinguish variable initialization from object construction: `User user = new User()` initializes `user` with a reference returned by object creation; they are related operations, but they are not conceptually the same thing.

### Variable Scope

Scope determines the region of source code in which a variable name can be referenced. Java uses lexical, or static, scope: accessibility can normally be determined by examining the structure of the source code rather than the runtime execution path. Blocks delimited by `{}` frequently introduce nested scopes.

```Java
void process() {
    int total = 0;

    if (total == 0) {
        String message = "Empty";

        System.out.println(total);   // Accessible
        System.out.println(message); // Accessible
    }

    System.out.println(total);

    // System.out.println(message);
    // Compile-time error
}
```

Scope should not be confused with lifetime. Scope describes where a name can be referenced in source code; lifetime describes how long the associated value or object remains relevant at runtime. An object referenced by a local variable, for example, may remain reachable after that particular local variable goes out of scope if another object retains a reference to it.

```Java
class Repository {

    private User cachedUser;

    void load() {
        User user = new User(); // local scope
        cachedUser = user;
    }
}
```

After `load()` returns, the local variable `user` no longer exists as an accessible variable, but the `User` object may remain reachable through `cachedUser`.

Keeping scopes as small as practical improves maintainability. A variable declared close to where it is used reduces the number of states a reader must reason about and prevents unrelated code from modifying it. Excessively broad scope is frequently a symptom of methods or classes carrying too many responsibilities.

### Local Variables

A local variable is declared inside a method, constructor, or block. It exists for the execution of that invocation or block and is inaccessible outside its lexical scope. Method parameters are closely related and behave largely like local variables initialized by the caller.

```Java
public double calculateTotal(double price, int quantity) {
    double subtotal = price * quantity;
    double tax = subtotal * 0.22;

    return subtotal + tax;
}
```

Here, `price` and `quantity` are parameters, while `subtotal` and `tax` are local variables.

Local variables do not receive default initialization. The Java compiler requires definite assignment before use, preventing an entire category of undefined-value bugs common in lower-level languages. Local variables also cannot use access modifiers such as `private` or `public`, because their visibility is determined entirely by their enclosing block.

```Java
void example() {
    // private int value = 10;
    // Invalid

    int value = 10;
}
```

Local variables are commonly associated with JVM stack frames, and primitive locals or object references may be stored there. However, treating "local variable = stack" as a strict JVM rule is inaccurate. The JVM specification defines execution semantics and local-variable slots, while JIT compilation may place values in CPU registers, eliminate variables entirely, or optimize object allocation through escape analysis. From an engineering perspective, local state is generally preferable to shared mutable state because it naturally limits coupling and significantly simplifies concurrency reasoning.

### Instance Variables

Instance variables, also called instance fields, are variables declared inside a class but outside methods, constructors, and initialization blocks, without the `static` modifier. Every instance of the class conceptually has its own copy of those fields.

```Java
class BankAccount {

    private String owner;
    private double balance;

    BankAccount(String owner) {
        this.owner = owner;
        this.balance = 0;
    }

    void deposit(double amount) {
        balance += amount;
    }
}
```

Two objects maintain independent state:

```Java
BankAccount accountA = new BankAccount("Alice");
BankAccount accountB = new BankAccount("Bob");

accountA.deposit(100);
accountB.deposit(500);
```

Conceptually:

```text
accountA ───► BankAccount
              owner = "Alice"
              balance = 100

accountB ───► BankAccount
              owner = "Bob"
              balance = 500
```

Instance variables describe the persistent state of an object and therefore participate directly in object-oriented design and encapsulation. They receive default values if constructors or field initializers do not explicitly assign them.

```Java
class Example {
    int number;       // 0
    boolean enabled;  // false
    String name;      // null
}
```

Fields should normally be `private`, with modifications controlled through methods that maintain class invariants. Exposing mutable fields directly makes it difficult to guarantee valid states. For example, allowing arbitrary assignments to a bank balance bypasses business rules that should belong to the object.

```Java
class BankAccount {

    private double balance;

    public void withdraw(double amount) {
        if (amount <= 0 || amount > balance) {
            throw new IllegalArgumentException();
        }

        balance -= amount;
    }
}
```

Instance fields also matter for concurrency. If the same object is shared between threads, its mutable fields become shared state and may require synchronization, locks, atomic operations, immutability, or another concurrency strategy.

### Static Variables

A static variable, or static field, belongs to the class rather than to an individual object. Conceptually there is one field associated with the loaded class, shared by all instances using that class definition.

```Java
class User {

    private static int userCount = 0;

    private String name;

    User(String name) {
        this.name = name;
        userCount++;
    }

    static int getUserCount() {
        return userCount;
    }
}
```

```Java
User a = new User("Alice");
User b = new User("Bob");

System.out.println(User.getUserCount()); // Output: 2
```

Conceptually:

```text
User class
 └── userCount = 2

a ───► User("Alice")
b ───► User("Bob")
```

Static fields are initialized as part of class initialization performed by the JVM. Static field initializers and static initialization blocks execute when the class is initialized, subject to JVM class-loading and initialization rules.

```Java
class Configuration {

    static String environment;

    static {
        environment = "production";
    }
}
```
Static fields are particularly appropriate for constants:

```Java
public static final int MAX_RETRIES = 3;
```

Mutable static state should be used cautiously. It creates effectively global shared state, which increases coupling, complicates tests, can introduce race conditions, and may retain objects for as long as the defining class remains loaded. A common architectural mistake is turning services, caches, configuration, or dependencies into static variables simply to make them globally accessible. Dependency injection—commonly used by frameworks such as Spring—usually provides a more explicit and testable way to manage shared application components.

### Local vs Instance vs Static

| Characteristic           | Local variable        | Instance variable   | Static variable             |
| ------------------------ | --------------------- | ------------------- | --------------------------- |
| Declared                 | Method/block          | Class               | Class                       |
| Belongs to               | Method invocation     | Object instance     | Class                       |
| Separate copy per object | N/A                   | Yes                 | No                          |
| Shared between instances | No                    | No                  | Yes                         |
| Default initialization   | No                    | Yes                 | Yes                         |
| Typical access           | Direct name           | `this.field`        | `ClassName.field`           |
| Typical purpose          | Temporary computation | Object state        | Class-level state/constants |
| Concurrency concern      | Usually low           | If object is shared | Usually high if mutable     |

A useful mental model is:

```text
Local variable
    → state of an execution

Instance **variable**
    → state of an object

Static variable
    → state of a class
```


## Primitive Types

Java defines eight primitive types: `byte`, `short`, `int`, `long`, `float`, `double`, `char`, and `boolean`. They represent simple values directly rather than objects and are built into the language and JVM. Primitive predictable memory representations, efficient arithmetic, and a clear type system for fundamental values such as integers, floating-point numbers, characters, and logical states.

Unlike reference types, primitive variables conceptually contain the value itself rather than a reference to an object. This distinction affects memory usage, comparison semantics, nullability, method calls, generics, and performance. Java deliberately specifices the size and behavior of most primitive types independently of the underlying CPU architecture, which helps preserve Java's platform-independent execution model.

At the JVM level, primitive values are used directly by bytecode instructions such as interger addition, floating-point arithmetic, comparisons, and conversations. The JVM may internally represent some smaller primitives using wider machine words, so their language-level size does not necessarily imply an identical runtime storage footprint in every context.

### `byte`

`byte` is an 8-bit signed integer type with values from `-128` to `127`. It is mainly useful when representing raw binary data, compact numeric structures, network protocols, file formats, or APIs whose external representation is explicitly byte-oriented.

```Java
byte status = 120;

byte min = -128;
byte max = 127;
```

A common misconception is that using `byte` instead of `int` automatically makes every calculation more memory-efficient. Java promotes `byte`, `short`, and `char` operands to `int` during most arithmetic operations.

```Java
byte a = 10;
byte b = 20;

// Does not compile:
// byte result = a + b;

int result = a + b;
```

The expression `a + b` produces an `int`, not a `byte`. This promotion simplifies arithmetic semantics and aligns better with how processors typically operate.

`byte` becomes particularly important when working with `byte[]`, streams, serialization, cryptography, image data, network packets, and binary protocols. In such contexts, it represents actual 8-bit data rather than merely a small number.

### `short`

`short` is a 16-bit signed integer with values from `-32,768` to `32,767`.

```Java
short temperature = 250;
```

Its practical use in modern application code is limited. Like `byte`, it is promoted to `int` during arithmetic operations.

```Java
short x = 10;
short y = 20;

int result = x + y;
```

`short` is primarily userful when interacting with binary formats, native protocols, legacy systems, or data structures where a 16-bit signed representation is explicitly required.  
Using `short` merely because a number currently happens to be small generally reduces readability without providing meaningful performance beneficits.

Large arrays can be an exception. A `short[]` may consume significantly less memory than an `int[]`, making it useful in memory-sensitive workloads such as image processing, scientific computing, or very large in-memory datasets.

### `int`

`int` is a 32-bit signed integer and is the default integer type in Java. Its range is `-2,147,483,648` to `2,147,483,647`.

Integer literals such as 10, 500, or 1_000_000 are normally `int` values.

```Java
int users = 1_000_000;
int retries = 3;
```

`int` is typically the correct choice for counters, indexes, sizes, identifiers with bounded ranges, loop variables, and general-purpose integer arithmetic. Even when smaller primitive types could technically hold the value, `int` often results in simpler and more idiomatic code because the JVM's integer operations naturally work with 32-bit values.

The most important architectural issue with `int` is overflow. Java integer arithmetic does not automatically throw an exception when the result exceeds the representable range.

```Java
int max = Integer.MAX_VALUE;

System.out.println(max);
System.out.println(max + 1);
```

Output:

```Text
2147483647
-2147483648
```

This is two's - complement wraparound. Overflow can become a correctness or security problem when arithmetic is used for financial values, capacity calculations, array sizes, counters, or validation logic. Methods such as `Math.addExact()` can be used when overflow should fail explicitly.

```Java
int result = Math.addExact(a, b);
```

### `long`

`long` is a 64-bit signed integer with a range of approximately +-9.22 quintillion. Its range is `-9,223,372,036,854,775,808` to `9,223,372,036,854,775,807`.

It is commonly used when the possible range exceeds `int`, including timestamps, large counters, database identifiers, file sizes, distributed-system sequence numbers, and large quantities.

```Java
long population = 8_000_000_000L;
```

The `L` suffix is important because integer literals are interpreted as `int` when possible.

```Java
long values = 3_000_000_000L;
```

Wihout `L`, the literal itself may be rejected before it can be assigned to the `long`.

Like `int`, `long` uses two's - complement arithmetic and silently wraps on overflow.  
Therefore, selecting `long` increases the available range but does not eliminate overflow as a design concern.

For timestamps, a common representation is milliseconds or nanoseconds stored in a `long`.

```Java
long timestamp = System.currentTimeMillis();
```

However, application-level date and time logic should normally use APIs such as `Instant`, `LocalDateTime`, or `Duration` rather than manipulating raw timestamps directly.

### `float`

`float` is a 32-bit IEEE 754 floating-point type. It represents approximate real numbers using a sign, exponent, and significand rather than storing decimal digits exactly.

```Java
float temperature = 21.5F;
```

The `F` suffix is required because floating-point literals are `double` by default.

```Java
float value = 10.5F;
```

A `float` provides roughly 6-7 decimal digits of precision. Its main advantage over `double` is reduced memory consumption, which can matter in large arrays, graphics, machine learning, simulations, or hardware-oriented APIs.

Floating-point values should not be treated as exact decimal arithmetic.

```Java
float result = 0.1F + 0.2F;

System.out.println(result);
```

The result may not mathematically equal the expected decimal representation because values such as 0.1 cannot be represented exactly in binary floating-point.

this limitation is not specific to Java; it comes from IEEE 754 floating-point representation.


### `double`

`double` is a 64-bit IEEE 754 floating-point type and is Java's default type for decimal literals.

```Java
double latitude = -34.9011;
double percentage = 99.95;
```

It provides approximately 15-16 decimal digits of precision and is normally preferred over `float` for general-purpose numerical calculations. Modern processors and JVMs handle `double` efficiently, so choosing `float` purely for assumed speed advantages is usually unjustified.

Like `float`, `double` represents binary approximations rather than exact decimal values.

```Java
double result = 0.1 + 0.2;

System.out.println(result);
```

Typical output: ```0.30000000000000004```.

This becomes particularly important for financial calculations.

```Java
double price = 0.1;
double tax = 0.2;
```

Using `double` for monetary values can introduce rounding inconsistencies. Financial or accounting systems normally use `BigDecimal` or integer representatioons of the smallest monetary unit.

```Java
BigDecimal amount =
        new BigDecimal("0.1")
            .add(new BigDecimal("0.2"));
```

`double` also supports special IEEE 754 values: `NaN`, `Positive Infinity`, `Negative Infinity`.

For example:

```Java
double x = 0.0 / 0.0;
double y = 1.0 / 0.0;
```

These produce `NaN` and positive infinity respectively rather than throwing an arithmetic exception.

### `char`

`char` is an unsigned 16-bit type whose values range from: `0` to `65,535`.

It stores a UTF-16 code unit.

```Java
char letter = 'A';
char digit = '7';
char symbol = '#';
```

An important distinction is that a Java `char` does not necessarily represent a complete Unicode character. Unicode contains more than 65,536 code points, while `char` is limited to 16 bits. Characters outside the Basic Multilingual Plane are represented using two UTF-16 code units called a surrogate pair.

For example:

```Java
String emoji = "😀";

System.out.println(emoji.length());
```

Output: `2`

The string contains one Unicode code point but two Java `char` values.

For Unicode-aware systems, developers should distinguish between UTF-16 code units and Unicode code points. APIs such as the following are safer when iterating over arbitrary Unicode text:

```Java
text.codePoints();
```

This becomes important in internationalization, text processing, validations, indexing, search systems, and security-sensitive string handling.

Because `char` is technically an integral type, arithmetic operations are possible:

```Java
char c = 'A';

System.out.println((int) c);
```

Output: `65`.

However, relying excessively on numeric `char` arithmetic can make Unicode-related code brittle.

### `boolean`

`boolean` represent logical truth values:

```Java
boolean active = true;
boolean deleted = false;
```

Unlike languages such as C or C++, Java does not treat integers as booleans.

This is invalid:

```Java
int value = 1;

// Does not compile:
// if (value) {}
```

The condition must explicitly produces a `boolean`.

```Java
if ( value == 1 ) {
    // ...
}
```

This rule prevents an entire class of accidental assignments and implicit numeric-to-boolean conversions.

The Java Language Specification does not define `boolean` as one-byte numeric type and does not expose a numeric representation such as `0` or `1`. JVM implementations may represent booleans differently depending on whether they are local variables, fields, or array elements.

From a design perspective, excessive boolean parameters can become a maintainability problem:

```Java
process(true, false, true);
```

The meaning of the arguments is unclear. For APIs with multiple modes, enums or dedicated configuration objects are often clearer.

```Java
process(
    ProcessingMode.ASYNC,
    ValidationMode.STRICT
);
```

## Reference Types

A reference type in Java is a type whose variables do not conceptually contain the object itself; instead, they contain a reference that allows the JVM to access an object, array, or other reference-typed value. This distinguishes reference types from primitive types such as `int`, `double`, or `boolean`, whose variables directly represent primitive values.  
Reference types make Java's object model possible: multiple variables can refer to the same object, objects can participate in inheritance and polymorphism, and the Garbage Collector can manage their lifetime automatically.

Java reference types includes class types, interface types, array types, and type variables used by generics. Examples include `String`, `User`, `List<String>`, `Runnable`, `int[]`, and a generic type such as `T`. The Java Language Specification defines references abstractly; it does not require a particular machine-level representation such as a raw memory address. JVM implementations are therefore free to use internal representations optimized for the runtime, including techniques such as compressed object references.

The most important consequence of reference semantics is that assigment, parameter passing, and comparison operate on the reference value rather than automatically copying the referenced object. Understanding this distinction is fundamental for reasoning about mutability, aliasing, object identity, thread safety, API design, garbage collection, and application architecture.

```Java
User user1 = new User("Alice");
User user2 = user1;

ser2.setName("Bob");

System.out.println(user1.getName()); // Bob
```

Both variables refer to the same `User` object.

### Reference Variables and Objects

A reference variable and an object are two different things. The declaration creates a varaible capable of holding a reference, while an expression such as `new User()` creates an object. In a typical JVM implementation, ordinary objects are dynamically allocated in memory managed by the JVM - commonly described as the heap - while references may exist in local variables, object fields, static fields, arrays, or internal JVM structures. However, "objects are always physically allocated on the heap" is an implementation-level simplification: JVM optimizations such as escape analysis may eliminate or transform allocations while preserving Java's observable semantics.

```Java
User user;          // Reference variable
user = new User();  // Object creation + reference assignment
```

A useful conceptual model is:

```text
Local variable                  Managed JVM memory

user ──────────────────────────► User object
                                  name = "Alice"
                                  age  = 30
```

The reference should not be thought of as an object containing all of the object's fields. It is merely the value through which the object is accessed.

### Aliasing

Because reference values can be copied, multiple varaibles may point to the same object. This situation is called aliasing. Copying a reference does not clone or duplicate the referenced object.

```Java
Account a = new Account(100);
Account b = a;

b.deposit(50);

System.out.println(a.getBalance()); // 150;
```

Conceptually:

```text
a ──────┐
        │
        ├────────► Account { balance = 150 }
        │
b ──────┘
```

Aliasing is powerful but architecturally important. Shared mutable objects can create non-obvious dependecies between components and become especially problematic under concurrency. Immutable objects, defensive copies, encapsulation, and carefully designed ownership boundaries are common techniques for reducing these risks.

### Reference Assignment

Assignment between compatible reference variables copies the reference value, not the object.  
Consequently, changing which object one variable references does not change another reference variable that previously received the same reference.

```Java
User a = new User("Alice");
User b = a;

b = new User("Bob");

System.out.println(a.getName());    // Alice
System.out.println(b.getName());    // Bob
```

After the second assignment:

```text
a ─────────► User("Alice")

b ─────────► User("Bob")
```

This distinction between modifying an object and assigning a new reference is one of the most important aspects of Java's object semantics.

### `null`

Every reference variable can normally hold the special value `null`, meaning that it currently refers to no object. Instance fields and static reference fields receive `null` as their default value, while local variables must be explicitly initialized before being read.

```Java
User user = null;
```

Dereferencing `null` produces a `NullPointerException`.

```Java
User user = null;

user.getName(); // NullPointerException
```

Large Java systems typically attempt to make nullability explicit through validation, API contracts, annotations such as `@Nullable` / `@NonNull`, or abstractions such as `Optional` in appropriate return-value scenarios. `Optional`, however, should not automatically replace every nullable reference; it is primarily intended to model the optional resence of a result in APIs.

### Class Type

A class defines a reference type whose values may refer to instances of that class or, depending on inheritance relationships, intaces of compatible subclasses.

```Java
class Animal {
    void makeSound() {
        System.out.println("Animal");
    }
}

class Dog extends Animal {
    @Override
    void makeSound(){
        System.out.println("Woof");
    }
}

Animal animal = new Dog();
```

The variable's compile-time type is `Animal`, while the runtime object is `Dog`. The compiler uses the declared type to determine which operations are legally accessible, while the JVM uses the runtime object's actual class for dynamically dispatched instance methods.

```Java
animal.makeSound(); // Woof
```

This separation between reference type and runtime object type is the foundation of subtype polymorphism and allows higher-level components to depend on abstractions instead of concrete implementations.

### Interface Types

Interfaces also define reference types. An interface reference can refer to any object whose class implements that interface.

```Java
interface PaymentProcessor{
    void process();
}

class StripeProcessor implements PaymentProcessor {

    @Override
    public void process(){
        System.out.println("Processing payment");
    }
}

PaymentProcessor processor = new StripeProcessor();
```

Interface references are particularly important architecturally because they decouple clients from concrete implementations. Libraries such as Spring heavily exploit this principle through dependency injection, proxies, repositories, service abstractions, and interchangeable implementations.

```Java
List<String> names = new ArrayList<>();
```

The variable depends on `List`, while the runtime implementation happens to be `ArrayList`. Programming against the interface usually reduces coupling and improves testability and maintainability.

### Array Types

Arrays are reference types even when their elements are primitives.

```Java
int[] numbers = new int[5];
String[] names= new String[5];
```

The array itself is an object managed by the JVM. Therefore, array variables follow the same reference semantics as other objects.

```Java
int[] a = {1, 2, 3};
int[] b = a;

b[0] = 100;

System.out.println(a[0]);  // 100
```

Arrays have a fixed length established when the array is created, support runtime bounds checking, and expose their size through the `lengh` field. Java arrays are also covariant - for example, `String[]` can be assigned to `Object[]` - which can produce runtime `ArrayStoreException`. Generics deliberately use different type rules to avoid similar runtime type-safety problems.

### Generic Type Variables

A generic type parameter such as `T` is also a form of reference type.

```Java
class Box<T> {

    private T value;

    public void set(T value) {
        this.value = value;
    }

    public T get() {
        return value;
    }
}
```

Generic types allow algorithms and data structures to express relationships between reference types while maintaining compile-time type safety.

```Java
Box<String> box = new Box<>();
box.set("Java");

String value = box.get();
```

Java generics are primarily implemented through type erasure: most generic type information is checked by the compiler and is not represented as distinct specialized runtime classes. This explains restrictions such as the inability to directly instantiate `new T()` or use primitive types like `List<int>`.

### Reference Type Conversion and Casting

References can be assigned without explicit casting when the source type is safely convertible to the target type. Converting a subtype reference to a supertype is called upcasting and normally implict.

```Java
Dog dog = new Dog();

Animal animal = dog;
```

The opposite direction requires an explicit cast because the compiler cannot guarantee that an arbitraty `Animal` actually refers to a `Dog`.

```Java
Animal animal = new Dog();

Dog dog = (Dog) animal;
```

An invalid cast produces `ClassCastException` at runtime. FRequent downcasting often indicates that abstractions or polymorphic responsibilities have been modeled poorly. Modern Java can reduce explicit casting through pattern matching:

```Java
if (animal instanceof Dog dog) {
    dog.fetch();
}
```

### Reference Equality vs Object Equality

The `==` operator applied to reference types compares references - essentially asking whether both operands refer to the same object. It does not normally compare the logical contents of the objects.

```Java
String a = new String("Java");
String b = new String("Java");

System.out.println(a == b);      // false
System.out.println(a.equals(b)); // true
```

`equals()` is the convertional mechanism for logical equality. Classes representing domain values frequently override both `equals()` and `hashCode()` so that logically equivalent objects behave correctly in collections such as `HashMap` and `HashSet`.

```text
==          → object identity
equals()    → logical equality
hashCode()  → hash-based collection contract
```

Using `==` for objects such as `String`, boxed numbers, or domain entities is a common source of bugs because caching or interning can make identity comparisons appear to work in some cases and fail in others.

### Java is Pass-by-value

Java is always pass-by-value. For a reference type, however, the value being copied is the reference.

```Java
void rename(User user){
    user.setName("Bob");
}
```

Calling:

```Java
User user = new User("Alice");

rename(user);

System.out.println(user.getName()); // Bob
```

copies the reference:

```text
caller user ─────┐
                 ├────► User
parameter user ──┘
```

Therefore, the method can modify the referenced object.

But replacing the parameter's reference does not replace the caller's reference:

```Java
void replace(User user) {
    user = new User("Bob");
}

User user = new User("Alice");

replace(user);

System.out.println(user.getName()); // Alice
```

This behavior is sometimes incorrectly described as "pass-by-reference" Java has no pass-by-reference parameter semantics.

### Garbage Collection and Reachability

Reference types are closely connected to garbage collection. The JVM tracks whether objects remain reachable through chains of references originating from GC roots, such as active thread stacks, static fields, and certain JVM-internal structures.

```text
GC Root
   │
   ▼
Service
   │
   ▼
Repository
   │
   ▼
DatabaseClient
```

As long as an object remains strongly reachable through such a chain, it normally cannot be reclaimed.

```Java
User user = new User();

user = null;
```

Setting the variable to `null` does not directly destroy the object. It merely removes that particular reference. If no reachable references to the object remain, the object becomes elegible for garbage collection. Java therefore avoids manual memory deallocation, but it can still suffer from memory leaks when applications unintentionally retain references - for example through static collections, caches, listeners, or long-lived application contexts.

### Reference Types and Memory

A useful simplified mental model is:

```text
Primitive:

int age = 30;

age
┌────┐
│ 30 │
└────┘


Reference:

User user = new User("Alice");

user                       managed object memory
┌───────────┐              ┌─────────────────┐
│ reference │─────────────►│ User            │
└───────────┘              │ name = "Alice"  │
                           └─────────────────┘
```

This model is useful for reasoning but should not be interpreted as an exact JVM memory layout. JVMs may optimize allocations, object layouts, and references while preserving Java's specified behavior. Technologies such as compressed ordinary object pointers, escape analysis, scalar replacement, and generational garbage collectors are implementation details beneath the Java language abstraction.

For performance-sensitive systems, reference-heavy object graphs can affect allocation rates, garbage-collector pressure, CPU cache locality, and memory footprint. This is one reason that primitives, primitive arrays, compact data representations, records, and specialized data structures can sometimes outperform large graphs of small mutable objects.
