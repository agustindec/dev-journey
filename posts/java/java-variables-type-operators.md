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

Instance variable
    → state of an object

Static variable
    → state of a class
```


