# Core Java Basics (Study Guide + Examples)

## Table of Contents
- Java Overview
- JDK, JRE, JVM
- Compilation to Bytecode
- Syntax Basics (Identifiers, Keywords, Literals, Comments)
- Data Types and Ranges
- Variables, Scope, Lifetime, Shadowing
- Operators (Arithmetic, Relational, Logical, Bitwise, Shift, Ternary)
- Type Conversion and Casting
- Control Flow (if/switch/loops/labels)
- Arrays (1D/2D), Varargs
- Strings and String Pool
- Wrapper Classes, Autoboxing/Unboxing
- Packages and Imports
- Access Modifiers and Other Modifiers (static, final, abstract, sealed)
- Initialization Order (static/instance blocks, constructors)
- Assertions
- Logging (java.util.logging) quick intro
- Common Utilities (Objects, Math, Random, UUID)

---

## Java Overview
Java is a statically-typed, object‑oriented, general‑purpose language. Source code (.java) is compiled to bytecode (.class) and executed by the JVM. Write once, run anywhere.

## JDK, JRE, JVM
- JDK: Compiler (javac), tools, and JRE for development.
- JRE: Runtime libraries and JVM for running applications.
- JVM: Loads, verifies, JIT‑compiles, and executes bytecode.

## Compilation to Bytecode
```bash
javac Hello.java
java Hello
```
`javac` produces .class files. The JVM uses a class loader, verifier, and execution engine to run them.

## Syntax Basics
- Identifiers: letters, digits, `_`, `$` (not recommended for public APIs).
- Keywords: class, interface, enum, if, else, switch, try, catch, finally, return, etc.
- Literals: numeric (10, 0xFF), char ('a'), string ("abc"), boolean (true/false), text blocks (Java 15+).
- Comments: //, /* ... */, /** javadoc */.

## Data Types and Ranges
- Primitives: byte(8), short(16), int(32), long(64), float(32), double(64), char(16), boolean(1 bit logical).
- Reference types: arrays, classes, interfaces, enums, records.

Example:
```java
int a = 10;
long b = 10L;
double d = 10.5;
char c = 'A';
boolean ok = true;
```

## Variables, Scope, Lifetime, Shadowing
- Local variables live on the stack frame and must be initialized before use.
- Instance variables get default values.
- Shadowing occurs when a local variable has the same name as a field.
```java
class ShadowingExample {
    int value = 10;
    void show() {
        int value = 5; // shadows the field
        System.out.println(value);      // 5
        System.out.println(this.value); // 10
    }
}
```

## Operators
- Arithmetic: + - * / %
- Relational: == != > >= < <=
- Logical: && || !
- Bitwise: & | ^ ~
- Shift: << >> >>>
- Ternary: cond ? a : b
```java
int x = 5, y = 2;
int div = x / y;       // 2
double exact = x / 2.0; // 2.5
int mask = 0b1010 & 0b1100; // 0b1000
```

## Type Conversion and Casting
- Widening: automatic (int → long).
- Narrowing: explicit cast (long → int). Beware overflow.
```java
long big = 1_000_000_000_000L;
int small = (int) big; // overflow
```

## Control Flow
- if/else, switch (supports strings and enums), loops (for, enhanced for, while, do-while), break, continue, labeled break.
```java
switch (day) {
    case "MON": case "TUE": System.out.println("Weekday"); break;
    default: System.out.println("Other");
}
```

## Arrays and Varargs
- Fixed-size, zero-indexed, length property.
- Varargs compile to arrays; only one varargs parameter at end of signature.
```java
int[] a = {1, 2, 3};
int[][] m = { {1,2}, {3,4} };

static int sum(int... nums) {
    int s = 0;
    for (int n : nums) s += n;
    return s;
}
```

## Strings and String Pool
- Immutable; literals stored in string pool for sharing.
- Use StringBuilder for frequent concatenation.
```java
String s1 = "java";
String s2 = "java";
System.out.println(s1 == s2);   // true (same pool entry)
```

## Wrapper Classes, Autoboxing, Unboxing
- Integer, Long, Double, etc.
- Beware NullPointerException during unboxing.
```java
Integer i = null;
// int n = i; // NPE
```

## Packages and Imports
Organize types into namespaces. Import types with `import pkg.Type;` or `import pkg.*;`

## Access and Other Modifiers
- Access: public, protected, package‑private, private.
- Other: static, final, abstract, synchronized, native, strictfp, transient, volatile, sealed (17), non‑sealed.

## Initialization Order
1) Static fields/blocks (parent → child)  
2) Instance fields/blocks (parent → child)  
3) Constructors (parent → child)

## Assertions
Enable with -ea. Do not use for argument validation in public APIs.
```java
assert x > 0 : "x must be positive";
```

## Logging (java.util.logging) Minimal
```java
import java.util.logging.Logger;
Logger log = Logger.getLogger("app");
log.info("starting");
```

## Common Utilities
Objects.requireNonNull, Objects.equals; Math; Random and ThreadLocalRandom; UUID.
