# Introduction to Java

## A Short History of Java

Java began in 1991 as part of the Green Project at Sun Microsystems. A small team led by James Gosling was developing software for consumer electronic devices, which often had limited resources and used different processor architectures. The team therefore needed a compact, reliable language whose programs could run on multiple types of hardware.

The language was initially called *Oak* and was later renamed *Java*. Instead of compiling programs directly into instructions for a specific processor, Java compiles source code into an intermediate format called *bytecode*. This bytecode runs on a Java Virtual Machine (JVM), making it possible to execute the same program on different operating systems and hardware platforms. This idea became known as **"write once, run anywhere."**

Sun Microsystems officially introduced Java in 1995, initially promoting it as a language for interactive web content. Java 1.0 was released in 1996 and included support for browser-based programs called *applets*. Although applets were eventually discontinued because of security concerns and changes in web technology, Java became widely adopted for server-side, desktop, and enterprise applications.

Several releases marked important stages in the language's evolution. Java 5, released in 2004, introduced generics, annotations, enumerations, autoboxing, and the enhanced `for` loop. Java 8, released in 2014, added lambda expressions, the Stream API, and other features that enabled a more functional programming style. Java 9 introduced the module system in 2017 and prepared the platform for a faster release process.

Since Java 10, a new feature release has generally appeared every six months. Long-term support (LTS) releases are maintained for longer periods and are commonly preferred for production systems. Java 8, 11, 17, 21, and 25 are LTS releases. Today, Java continues to evolve through the OpenJDK project and is widely used for backend services, enterprise systems, cloud applications, and many other types of software.


## Java's Main Characteristics

### Object-oriented

**Java as an Object-Oriented Language**

Java is commonly described as an object-oriented programming language. This is one of its most important characteristics, because object-oriented programming influences not only how Java code is written, but also how Java applications are designed, organized, extended, and maintained.

A computer program ultimately consists of instructions and data. At the lowest level, the computer does not understand concepts such as customers, invoices, employees, bank accounts, or products. It works with values stored in memory and operations performed on those values.

Programming languages give developers ways to organize this information.

One possible approach is to think primarily in terms of procedures: first perform one operation, then another, then another. Data exists separately, and functions manipulate that data.

Object-oriented programming introduces a different perspective. Instead of organizing the entire program mainly around sequences of operations, we organize significant parts of the program around objects.

An object represents something that has informations and behavior associated with it.

Consider a banking application. The program might need to represent concepts such as a customer, a bank account, a transaction, and a credit card.

Object-oriented programming allows us to represent this idea as a software object instead of keeping all of these pieces scattered throughout the program.

The important conceptual change is that data and the operations related to that data can belong to the same logical entity.

This combination is one of the foundations of object-oriented programming.

**Object as models**

An object can be understood as a model of something that exists within the problem the software is trying to solve.

That "something" does not necessarily have to be a physical object.

For example, a program might contain objects representing: `Customer`, `Product`, `Order`, `Invoice`, `Payment`.

Some of these correspond relatively closely to concepts from the real world. A customer or product is easy to imagine.

But objects can also represent more abstract concepts: `AuthenticationRequest`, `DatabaseConnection`, `EmailService`, `Configuration`, `Transaction`, `Session`.

The purpose of object-oriented programming is therefore not simply to imitate physical objects from the real world. The more important idea is to create software entities that represent meaningful concepts within a system.

These entities can contain information and provide operations related to their responsabilities.

### Strongly typed

Java is considered a **strongly typed language**, which means that every value in Java program has a specific type, and the language enforces rules about how values of different types can be used. A type describes what kind of information a value represents and which operations are valid for it. For example, a number, a boolean value, a text value, and an object are treated as different kinds of data rather than as interchangeable value.

This type informations allows Java to prevent many invalid operations. If a variable is insteded to contain a number, Java does not normally allow unrelated data, such as text or an arbitrary object, to be stored there.  
Similary, an operation that makes sense for one type may not make sense for another. Java uses these restrictions to maintain consistency throughout the program.

Java is also **statically typed**, a concept closely related to strong typing but not exactly the same. Static typing means that the types of variables and expressions are largely determined and checked before the program runs, during compilation. Strong typing refers more generally to how strictly the language respects the boundaries between different types. In Java, both characteristics work together.

### Platform independent

Java is considered platform independent because a Java program is not compiled directly into machine code for a specific operating system or processor. Instead, Java source code is compiled into an intermediate format called `bytecode`. This bytecode is designed to be executed by the `Java Virtual Machine (JVM)` rather than directly by the operating system.

Because JVM implementations exist for different platforms such as Windows, Linux, and macOS, the same compiled Java bytecode can usually run on any of them without being recompiled. This idea is commonly summarized by the phrase `"Write Once, Run Anywhere"`. The operating system-specific details are handled by the JVM, allowing the Java program itself to remain largely independent of the underlying platform.

Platform independence does not mean that every Java application will behave identically in every environment, since programs can still depend on operating-system features, external libraries, files, or hardware. However, the Java execution model greatly reduces platform-specific concerns and is one of the main reasons Java became popular for portable applications.

### Garbage collected

Java is considered a **garbage-collected language** because memory management is handled automatically by the **Java Virtual Machine (JVM)**. When a program creates objects, memory is allocated for them, but the programmer usually does not need to manually release that memory when the objects are no longer neeeded. Instead, a component called the `Garbage Collector (GC)` periodically identifies objects that are no longer reachable by the application and reclaims the memory they were using.

This automatic memory management reduces the risk of common problems such as forgetting to free memory or incorrectly releasing memory that is still in use. However, garbage collection does not mean that developers can completely ignore memory usage: poorly designed programs can still consume excessive memory or keep unnecessary objects alive. The main idea is that Java delegates most memory cleanup to the JVM, allowing developers to focus more on application logic than on manually managing memory.

## JDK - JRE - JVM

### JDK - Java Development Kit

The `JDK (Java Development Kit)` is the complete toolchain used to develop, compile, inspect, package, test, and run Java applications. Its purpose is broader than simply providing a Java runtime: it gives developers everything required to transform Java source code into something the JVM can execute. The central flow is `source code -> javac -> bytecode -> JVM`. The `javac` compiler validates syntax and type rules and produces `.class` files containing JVM bytecode; the `java` launcher starts a JVM, loads those classes, verifies them, and executes them using interpretation and **JIT compilation** where appropriate. A JDK therefore contains a Java runtime plus development and diagnostic tools. Historically, Java distinguised sharply between the **JDK** and a separately distributed **JRE (Java Runtime Environment)**, but modern Java distributions, particularly since the Java 9 module system, increasingly treat the runtime as something derived from the JDK rather than requiring a separate JRE installation.

The JDK includes several important tools that form part of the Java engineering ecosystem. `javac` is the compiler, `java` launches applications, `jar` creates and manipulates Java archives, `javadoc` generates API documentation, `javap` inspects compiled bytecode, `jdb` provides debugging capabilities, and tools such as `jcmd`, `jstack`, `jmap`, and Java Flight help diagnose running JVMs, thread problems, memory usage, garbage collection, and performance. It also contains the Java standard libraries and the JVM implementation supplied by the distribution. Build systems such as **Maven** and **Gradle** do not replace the JDK; they orchestrate it, invoking its compiler, runtime, and tooling while managing dependencies and build lifecycle tasks. Likewise, an IDE normally uses a configured JDK underneath. In production architecture, JDK selection matters because Java version, JVM implementation, vendor distribution, security patches, garbage collectors, container behavior, and runtime flags can affect compatibility, observability, performance, and operational risk.

```bash
javac Hello.java
java Hello
```

A **Junior developer** should understand that the JDK is required to develop Java software, know the difference between source code, bytecode, and JVM execution, and know that `JAVA_HOME` usually points to a JDK installation. A **Mid-level developer** should understand JDK versions, LTS releases, compatibility, build-tool integration, compiler configuration, and the difference between compile-time and runtime environments. A **Senior or Technical Lead** should additionally understand JDK distribution choices, upgrade strategy, bytecode compatibility, JVM diagnostics, security patching, container/runtime sizing, and how the selected JDK affects production behavior. Common mistakes include treating the JDK and JVM as synonyms, assuming Maven or an IDE contains Java independently, compiling with one Java version while unknowingly running another, and believing that "Java version" refers to only the language syntax rather than a combination of language features, APIs, compiler behavior, bytecode level, and JVM capabilities. In a Senior interview, you may be asked to explain the relationship between **JDK, JVM, bytecode, compiler and runtime**, what happens from `javac` to execution, how Java-version compatibility works, or how you would approach a JDK upgrade in a production system.

### JRE - Java Runtime Environment

The **JRE (Java Runtime Environment)** is the environment required to **run Java applications**. Its purpose is to provide everything necessary to execute already-compiled Jav bytecode without including the full development toolchain. Conceptually, it contains the **JVM**, the Java runtime libraries, and supporting runtime components. When you execute a Java applications, the JRE provides the environment in which the JVM loads `.class` files, verifies bytecode, resolves required classes, manages memory, performs garbage collection, and executes the program through interpretation and **JIT compilation**. The key distinction is that the JRE is concerned with **execution**, while the **JDK** additionally provides development tools such as `javac`, `javadoc`, and diagnostic utilities.

Historically, Java vendors distributed the JRE as a separate installation: developers installed a JDK, while machines that only needed to run Java applications could install a smaller JRE. Since **Java 9 and the introduction of the Java Platform Module System**, this model has changed significantly. Modern JDK distributions generally do not provide the traditional standalone JRE as a separate Oracle-style package. Instead, the JDK contains the runtime capabilities, and tools such as `jlink` can create a **custom runtime image** containing only the Java modules required by a particular application. This is especially relevant for containers and cloud deployments because smaller runtime images can reduce image size, attack surface and unnecessary dependencies, although they introduce additional build and maintenance considerations.

```text
Traditional model:

JDK
├── Development tools
│   ├── javac
│   ├── javadoc
│   └── ...
└── JRE
    ├── JVM
    └── Runtime libraries
```

```text
Modern conceptual model:

JDK
├── Compiler and development tools
├── JVM
├── Java runtime modules
└── jlink → custom runtime image
```

A **Junior developer** should understand the basic relationship: the JDK is used to develop Java software, while the JRE concept represents what is required to run it, and the **JVM is only one component of that runtime environment**. A **Mid-level developer** should understand Java-version compatibility, runtime configuration, dependency on standard-library modules, and why modern deployments may use a full JDK or a reduced runtime image rather than a standalone JRE. A **Senior or Technical Lead** should understand the operational implications of runtime selection: security patching, JVM vendor and version, container image size, observability tooling, module selection, compatibility, and whether removing development/diagnostic tools from production improves security enough to justify reduced troubleshooting capability. Common interview questions include explaining **JDK vs. JRE vs. JVM**, why the traditional standalone JRE is less relevant in modern Java, what `jlink` provides, and what actually happens when compiled bytecode is executed.

### JVM - Java Virtual Machine

The **JVM (Java Virtual Machine)** is the execution engine of the Java platform. Its purpose is to provide a standardized environment capable of executing **Java bytecode**, isolating applications from the details of the underlying operating system and processor architecture. This is the foundation of Java's platform independence: `javac` compiles source code into `.class` files containing bytecode, and a JVM implementation for the current platform translates that bytecode into operations the machine can execute.  
Internally, the JVM uses a **Class Loader subsystem** to locate and load classes, a **Bytecode Verifier** to check that loaded bytecode respects JVM safety rules, **runtime memory areas** such as the heap, thread stacks, and metadata storage to maintain application state, and an **Execution Engine** to run the instructions. Execution is not simply bytecode interpretation: modern JVMs identify frequently executed code and use a **JIT compiler (Just-In-Time compiler)** to transform it into optimized native machine code. At the same time, the **Garbage Collector** manages heap memory by reclaiming objects that are no longer reachable. These mechanisms allow the JVM to combine portability, memory safety, runtime optimization, and automatic memory management.

The JVM should not be confused with the **JDK** or **JRE**: the JVM executes bytecode; the JRE conceptually provides the JVM plus the libraries and components required to run Java applications; and the JDK provides the runtime plus development tools.

```text
Java source (.java)
        ↓
      javac
        ↓
Bytecode (.class)
        ↓
       JVM
 ┌───────────────┐
 │ Class Loading │
 │ Verification  │
 │ Memory Areas  │
 │ Interpreter   │
 │ JIT Compiler  │
 │ Garbage       │
 │ Collector     │
 └───────────────┘
        ↓
 Native machine code
        ↓
 CPU / Operating System
```

## How Java code is executed

### Source code

**Java source code** is the human-readable representation of a Java program, normally stored in files with the `.java` extension. It expresses the program using Java's language constructs - classes, methods, variables, expressions, control flow, and other elements - but it is not what the JVM executes directly. Source code exists primarily as the interface between developers and the Java toolchain: developers write and maintain it, while the Java compiler analyzes it and transforms it into **bytecode**. During compilation, `javac` performs lexical and syntactic analysis, resolves types and symbols, enforces many language rules, and reports compile-time errors before generating `.class` files. This separation between source code and executable bytecode is fundamental to Java's portability and tooling model.

A source file also participates in Java's structural convetions. It can declare a package, import types, define classes or other types, and contain the implementation of their behavior. The compiler does not simply translate each source line directly into an equivalent machine instruction; it builds an internal representation of the program, validates it according to the Java Language Specification, and emits JVM-compatible bytecode. Tools such as IDEs, static analyzers, annotation processors, formatters, and build systems operate around this source-level representation, but they do not replace the compiler or JVM.

A common misconception is that Java source code is "interpreted by the JVM." In the normal Java execution model, the JVM executes **bytecode**, not `.java` source files. Modern Java can launch a single source file directly with commands such as `java Hello.java`, but this is a convencience feature that performs compilation as part of the launch process; it does not change the underlying model. In Senior interviews, this topic often appears indirectly through questions about the difference between **source compatibility, binary compatibility, and runtime compatibility**, what `javac` actually produces, or why code that compiles with one JDK version may fail to compile or run under another.

```java
public class Hello {

  public static void main(String[] args){
    System.out.println("Hello, Java!");
  }
}
```
```text
Hello.java
   ↓
Java compiler (javac)
   ↓
Hello.class
   ↓
JVM
   ↓
Program execution
```

### Compilation

**Compilation** is the stage in which Java source code is transformed into **JVM bytecode** that can later be executed by the Java Virtual Machine. The standard compiler, `javac`, reads `.java` source files, parses their syntax, resolves referenced classes and methods, performs type checking and other compile-time validations, and finally emits one or more `.class` files. Internally, the process is more than a simple text translation: the compiler builds an internal representation of the program, verifies that language rules are satisfied, resolves symbols from the current project and its dependencies, may execute **annotation processors** that generate additional source or metadata, and then produces bytecode conforming to a particular JVM class-file version. Compilation therefore acts both as a transformation step and as an important validation boundary, catching many errors before the program ever reaches the JVM.

A key architectural point is that `javac` normally compiles Java into **bytecode**, **not native CPU instructions**. Native optimization happens later at runtime through mechanisms such as the JVM's interpreter and **JIT compiler**. This separation allows the same `.class` files to run on different operating systems and processor architectures, provided a compatible JVM exists. Build tools such as Maven and Gradle orchestrate compilation by managing dependencies, compiler options, generated sources, and target Java versions, but they ultimately rely on the Java compiler or equivalent compiler APIs. Compiler settings such as `--release` are important because sucessful compilation with a newer JDK does not automatically mean the resulting application is compatible with an older runtime.

```Bash
javac Hello.java
```

```text
Hello.java
    ↓
 Parsing and semantic analysis
    ↓
 Symbol and type resolution
    ↓
 Compile-time validation
    ↓
 Bytecode generation
    ↓
 Hello.class
```

Common mistakes include assuming that successful compilation guarantees correct runtime behavior, confusing compilation with JVM execution, or compiling against APIs that do not exist in the intended production Java version. Large systems also need to consider **incremental compilation, reproducible builds, annotation-processing cost, dependency consistency, and compiler-version upgrades**, because these can affect build performance and maintainability. The essential idea is that Java compilation creates a portable, validated intermediate representation of the program; the JVM is responsible for turning that representation into actual execution later.

### Bytecode

### JVM execution

## Java Editions

### Java SE

### Jakarta EE

## Java Versions and the LTS concept

## Basic structure of a Java project

## Basic idea of `.java` and `.class` files

## The `main` method







