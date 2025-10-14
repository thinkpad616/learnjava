# Java Interview Questions and Answers (Basic)

## Overview
This comprehensive list of Java interview questions and answers is designed for candidates preparing for Java developer positions.

## Basic Concepts

### 1. What is the difference between JDK and JVM?
**Answer:**
- JDK (Java Development Kit):
  - Complete development environment
  - Contains compiler, debugger, documentation tools
  - Used by developers to develop Java applications
- JVM (Java Virtual Machine):
  - Runtime environment only
  - Executes Java bytecode
  - Created for each operating system when Java is installed
  - End-users need only JVM to run Java applications

### 2. Why is Java considered platform independent?
**Answer:**
- Java achieves platform independence through bytecode
- When Java code is compiled, it creates .class files (bytecode)
- This bytecode can run on any system that has JVM installed
- The same bytecode works across different operating systems

### 3. What is the difference between heap and stack memory?
**Answer:**
- Heap Memory:
  - Used for dynamic memory allocation
  - Stores objects and instance variables
  - Memory is allocated/deallocated by garbage collector
- Stack Memory:
  - Used for static memory allocation
  - Stores local variables and method calls
  - Memory is automatically managed using LIFO (Last In First Out)
  - Variables are destroyed once method execution completes

### 4. What is the difference between equals() and == operator?
**Answer:**
```java
String str1 = new String("Hello");
String str2 = new String("Hello");

// Using == (compares references)
System.out.println(str1 == str2);        // false

// Using equals() (compares content)
System.out.println(str1.equals(str2));   // true
```

### 5. What is method overloading and overriding?
**Answer:**
**Method Overloading:**
```java
class Calculator {
    // Method with two parameters
    public int add(int a, int b) {
        return a + b;
    }
    
    // Method with three parameters
    public int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

**Method Overriding:**
```java
class Animal {
    public void makeSound() {
        System.out.println("Some sound");
    }
}

class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Woof!");
    }
}
```

### 6. What is the difference between final, finally, and finalize?
**Answer:**
```java
// final variable
final int MAX_VALUE = 100;

// final method
final void display() {
    System.out.println("Cannot be overridden");
}

// finally block
try {
    // Some code that might throw exception
} catch (Exception e) {
    // Handle exception
} finally {
    // Always executes
}

// finalize method
protected void finalize() {
    // Called by garbage collector
}
```

### 7. Explain exception handling in Java
**Answer:**
```java
public class ExceptionExample {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;  // This will throw ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero");
        } catch (Exception e) {
            System.out.println("Generic exception");
        } finally {
            System.out.println("This always executes");
        }
    }
}
```

### 8. What are access modifiers in Java?
**Answer:**
```java
public class AccessModifiersExample {
    public String publicVar;     // Accessible everywhere
    private String privateVar;   // Accessible only within class
    protected String protectedVar; // Accessible in package and subclasses
    String defaultVar;           // Accessible only within package
}
```

### 9. What is a jagged array in Java?
**Answer:**
```java
public class JaggedArrayExample {
    public static void main(String[] args) {
        int[][] jaggedArray = new int[3][];
        jaggedArray[0] = new int[3];  // First row has 3 columns
        jaggedArray[1] = new int[2];  // Second row has 2 columns
        jaggedArray[2] = new int[4];  // Third row has 4 columns
    }
}
```

### 10. How do you declare constants in Java?
**Answer:**
```java
public class Constants {
    // Constant variable
    public static final int MAX_USERS = 100;
    
    // Constant array
    public static final String[] DAYS = {"Mon", "Tue", "Wed"};
    
    // Constant class
    public static final class Config {
        public static final String URL = "http://example.com";
    }
}
```
