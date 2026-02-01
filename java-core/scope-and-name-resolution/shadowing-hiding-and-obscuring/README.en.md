# Hiding, Shadowing, and Obscuring in Java: do you know the difference?

We often use these concepts without even noticing, but understanding the mechanics behind them helps avoid silent bugs and gives you better control over Java’s scoping rules.

## Shadowing
Occurs when a variable in an inner scope (such as a method parameter or local variable) has the same name as a variable in an outer scope (such as a class field). The inner variable “shadows” the outer one.

- **How to handle it**: Use the `this` keyword

```java
public class Example {
    String name = "Global";

    void setName(String name) {
        // The parameter 'name' shadows the class field 'name'
        this.name = name;
    }
}
```

## Hiding
Happens when a static method in a subclass has the same name and signature as a static method in its superclass. There is no override here — this is *hiding*.

```java
class Parent {
    static void show() {
        System.out.println("Parent");
    }
}

class Child extends Parent {
    static void show() {
        System.out.println("Child"); // hiding
    }
}
```

### Difference between overriding and hiding

**Overriding**
- Only applies to **instance methods**
- Resolved at **runtime**
- Depends on the **actual object**

**Hiding**
- Only applies to **static methods**
- Resolved at **compile time**
- Depends on the **reference type**

## Obscuring
This is the rarest case and occurs when a name can be interpreted in multiple ways (for example, a class and a package, or a variable and a class with the same name). Java follows precedence rules to decide which one applies.

- Follow naming conventions (CamelCase for classes, lowerCamelCase for variables) and you will almost never run into this problem.

## See more

[Java Language Specification – 6.4. Shadowing and Obscuring](https://download.java.net/java/early_access/jdk27/docs/specs/jls/jls-6.html#jls-6.4)

[Java Language Specification – 8.4.8.2. Hiding (by Class Methods)](https://download.java.net/java/early_access/jdk27/docs/specs/jls/jls-8.html#jls-8.4.8)

---

>by *Thiago Pompeu*
