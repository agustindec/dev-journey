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

**Bytecode** is the intermediate instruction format produced by the Java compiler and consumed by the JVM. It is stored primarily inside `.class` files and is designed to be independent of a specific operating system or CPU architecture. This is the core mechanism behind Java's platform independence: `java` does not normally generate native instructions for x86, ARM, or another processor; instead, it emits standardized JVM instructions. A `.class` file contains more than executable instructions: it also carries metadata such as the class structure, method definitions, constant pool entries, type information, and version data. Before execution, the JVM loads the class, verifies that the bytecode is structurally valid and respects JVM safety constraints, thne interprets or compiles those instructions into native machine code through the **JIT compiler**.

Bytecode is therefore the contract between Java compilation and JVM execution. It decouples the Java language from the underlying hardware and, importantly, from Java itself: other JVM languages such as Kotlin and Scala also compile to JVM bytecode. This design enables portability, runtime optimization, intrumentation, profiling, and dynamic class loading, but it also introduces compatibility rules: bytecode compiled is simply "machine code for Java"; it is not native CPU code, but an instruction set defined by the JVM specification. Another mistake is assuming that bytecode interpretation makes Java inherently slow; modern JVMs heavily optimize frequently executed bytecode at runtime, often ccompiling hot paths into highly optimized native code.

```text
Java source (.java)
        ↓
      javac
        ↓
 JVM bytecode (.class)
        ↓
   JVM verification
        ↓
 Interpreter / JIT
        ↓
 Native machine code
        ↓
        CPU
```

A useful inspection tool is:

```Bash
javap -c Hello.class
```

This disassembles a `.class` file and shows the JVM instructions generated by the compiler, which is useful when investigating compiler behavior, performance details, language features, or unexpected runtime behavior.

### JVM execution

**JVM execution** is the stage in which compiled Java bytecode is loaded, validated, and transformed into actual work performed by the host machine. When a Java application starts, the JVM creates the runtime environment, loads the required classes through the **Class Loader subsystem**, verifies their bytecode for structural and type-safety rules, allocates the necessary runtime memory areas, and begins executing the program from its entry point. The JVM initially may interpret bytecode instruction by instruction, but it continuously profiles the application. Code paths that execute frequently become candidates for **Just-In-Time (JIT) compilation**, where the JVM converts bytecode into optimized native machine code for the current CPU. At the same time, the JVM manages memory, threads, exceptions, synchronization, and garbage collection.

The important architectural idea is that JVM execution is **dynamic**. The JVM does not simply translate every `.class` file once and run it unchanged; it can optimize methods based on actual runtime behavior, inline frequently used calls, remove unnecessary operations, and sometimes reverse previous optimizations if its assumptions stop being valid. This adaptive model explains concepts such as **JVM warm-up**, where an application may perform differently after running for some time. It also creates operational trade-offs: heap sizing, garbage collector selection, thread behavior, JIT compilation, native memory, and container limits can all influence latency and throughput. Common mistakes include assuming that the JVM only interprets bytecode, that garbage collection manages all forms of memory, or that identical Java code will necessarily have identical performance under every JVM configuration or workload.

```text
.java source
    ↓
javac
    ↓
.class bytecode
    ↓
Class Loading
    ↓
Bytecode Verification
    ↓
Runtime Memory Allocation
    ↓
Interpreter
    ↓
Runtime Profiling
    ↓
JIT Compilation of hot code
    ↓
Native machine instructions
    ↓
**CPU**
```

```Bash
java Hello
```

This command starts a JVM process, loads the required classes, initializes the runtime, locates the application entry point, and begins executing the bytecode using the JVM execution pipeline.

## Java Editions

### Java SE

**Java SE (Java Platform, Standard Edition)** is the core Java platform and the foundation on which most Java development is built. It defines the language-level APIs and runtime capabilities used for general-purpose applications, including fundamental packages for collections, concurrency, I/O, networking, security, date/time handling, reflection, database connectivity through JDBC, and many other standard service. Java SE is closely tied to the JDK, which provides an implementation of the platform together with development tools such as `javac` and `java`. It should not be confused with a framework: Java SE is the standardized base platform itself, while technologies such as Spring build on top of it.

Architecturally, Java SE establishes the contracts that Java applications and JVM implementations rely on, including the standard library and platform modules introduced with the Java Platform Module System. A common misconception is that Java SE is only for desktop or small applications; in practice, even large backend systems use Java SE as their foundation, with frameworks and servers adding higher-level capabilities. From a Senior perspective, what matters is understanding which functionality belongs to the standard platform versus external frameworks, how Java SE version upgrades affect APIs and compatibility, and how choosing newer platform features can improve maintainability, security, and performance while potentially introducing migration constraints.

### Jakarta EE

**Jakarta EE (Jakarta Enterprise Edition)** is the enterprise platform built on top of Java SE, designed to standardize the APIs and runtime model needed for large-scale server-side applications. It addresses recurring concerns such as HTTP handling, dependency injection, persistence, transactions, validation, security, messaging, and web services through specifications including Jakarta REST, Jakarta Persistence, Jakarta CDI, Jakarta Transactions, and Jakarta Servlet. Jakarta EE itself is not a single framework or application server; it is a set of specifications. Products such as WildFly, Payara, Open Liberty, and others implement those specifications and provide the runtime environment in which Jakarta EE applications execute.

A key historical distinction is that **Jakarta EE** is the successor to **Java EE**, which was transferred from Oracle to the Eclipse Foundation; this eventually caused the package namespace migration from `javax.*` to `jakarta.*`. Architecturally, Jakarta EE favors standardized contracts and portability across compliant runtimes, which can reduce vendor lock-in and provide long-term stability, but it may be less opinionated than frameworks such as Spring Boot. A Senior or Technical Lead should understand where Jakarta EE ends and an implementation begins, how its specifications interact with Java SE, the implications of the `javax` → `jakarta` migration, and the trade-off between standards-based portability and framework-specific productivity or ecosystem choices.

## Java Versions and the LTS concept

Java follows a **time-based release model**, with a new feature release approximately every six months. A Java version represents a particular evolution of the language, Java SE APIs, JVM capabilities, tooling, and class-file format. As of August 2026, **Java 26 is the latest released feature version**, **while Java 25 is the latest LTS release**; Java 27 is planned for September 2026. Oracle currently designates Java 8, 11, 17, 21, and 25 as LTS releases, with Java 29 planned as the next LTS in September 2027.

**LTS (Long-Term Support)** does not mean that the language or JVM fundamentally operates differently; it describes a longer maintenance and support lifecycle. This matters in production because organizations usually value security updates, bug fixes, vendor support, and predictable upgrade windows more than adopting every six-month release. A Technical Lead should also understand that support duration is partly a **JDK-distribution/vendor policy**, not an intrinsic property of bytecode: Oracle, Eclipse Temurin, Amazon Corretto, Azul, and other distributions can have different support policies. Common mistakes include treating every Java release as suitable for long-lived production systems, assuming LTS means "more stable code" by definition, or remaining indefinitely on an old LTS without applying updates.

```text
Feature-release model

Java 21  → LTS
Java 22  → non-LTS
Java 23  → non-LTS
Java 24  → non-LTS
Java 25  → LTS
Java 26  → non-LTS   ← current feature release (August 2026)
Java 27  → planned
...
Java 29  → planned LTS
```

```Bash
java --version
javac --version
```

## Basic structure of a Java project

A Java project is fundamentally a collection of **source files**, **resources**, **dependencies**, **test**, **configuration**, and **build outputs** organized so that they can be compiled and executed consistently. Java itself does not require the Maven/Gradle directory structure commonly seen in professional project; that structure is an ecosystem convetion. In modern backend development, production Java code normally lives under `src/main/java`, configuration and other resource under `src/main/resources`, test under `src/test/java`, and build metadata in files such as `pom.xml` for Maven or `build.gradle` for Gradle. Packages provide logical namespaces for classes and normally correspond to the directory hierarchy underneath the source directory.

The important architectural principle is **separation of source inputs from generated outputs**. Source code and configuration belong in version control, while compiled classes, generated files, test reports, and packaged artifacts are normally produced under directories such as Maven's `target/` or Gradle's `build/` and should not be manually maintained. In larger systems, a project may also contain multiple modules, each with its own soruces, dependencies, tests, and responsabilities. A common mistake is thinking that the IDE defines the project structure; IntelliJ IDEA or another IDE merely interprets a project ultimately controlled by the build system and source layout.

```text
my-application/
│
├── pom.xml                    # Maven build definition
│
└── src/
    ├── main/
    │   ├── java/
    │   │   └── com/example/app/
    │   │       └── Application.java
    │   │
    │   └── resources/
    │       └── application.properties
    │
    └── test/
        ├── java/
        │   └── com/example/app/
        │       └── ApplicationTest.java
        │
        └── resources/

Generated after building:

target/
├── classes/
└── application.jar
```

## Basic idea of `.java` and `.class` files

A `.java` file contains Java source code intended primarily for developers and the Java compiler, while a `.class` file contains the JVM bytecode and metadata generated from compilation. When `javac` processes source code, it performs parsing, symbol resolution, type checking, and other validations before encoding the resulting program into the standardized JVM class-file format. The `.class` file can contain information about fields, methods, types, constants, annotations, and executable bytecode, allowing the JVM to load and execute the program without needing the original source file.

The relationship is not necessarily one `.java` file to one `.class` file. A source file can result in multiple class files—for example, when nested or other compiler-generated classes are involved. `.class` files are also **platform independent**, but they have a class-file version corresponding to the Java release that generated them; an older JVM generally cannot execute bytecode produced for a newer JVM version. This is why compile-time and runtime Java versions matter in CI/CD and production environments. A common misconception is that `.class` files contain native CPU instructions: they contain JVM instructions, which are later interpreted or JIT-compiled by the JVM.


```text
Application.java
      │
      │ javac
      ▼
Application.class
      │
      │ Class Loader
      ▼
     JVM
      │
      ├── verification
      ├── interpretation
      └── JIT compilation
              │
              ▼
        Native instructions
```
```Bash
javac Application.java
javap -c Application.class
```

## The `main` method

The `main` **method is a launchable entry point for a Java application**. When the `java` launcher is given an initial class, the JVM loads and initializes that class and the launcher selects an eligible `main` method from which application-level execution begins. Traditionally—and still overwhelmingly in production Java—the conventional entry point is `public static void main(String[] args)`: `static` allows it to run without first creating an application object, `void` means it returns no value to the caller, and `String[] args` contains command-line arguments. The `main` method itself is not responsible for starting the JVM; the JVM process already exists by the time `main` is invoked.

```Java
public class Application {

    public static void main(String[] args) {
        System.out.println("Application started");
    }
}
```

There is an important modern nuance: starting with Java 25, Java's launch protocol was expanded so that a launchable `main` method can also be an instance method, can omit the `String[]` parameter, and does not necessarily need to be `public`. This was primarily introduced to simplify smaller and introductory programs; the traditional signature remains the clearest convention for ordinary production applications and is what engineers should recognize immediately. In frameworks such as Spring Boot, developers still see a `main` method, but it usually performs only the bootstrap operation: framework infrastructure subsequently creates the application context and takes control of the application lifecycle. A common mistake is therefore thinking that `main` must contain the application's business logic rather than simply acting as its bootstrap boundary.


```Java
// Traditional and still conventional
public static void main(String[] args) {
    startApplication();
}
```

```Java
// Valid in Java 25+
void main() {
    IO.println("Application started");
}
```
****



