# Java Practice Exam 2026 - 21 Questions

Sources: saved ExamSys HTML pages from `C:\Users\Alex\Downloads`.

This collates the 10-screen Java practice assessment into one Markdown file. Diagrams copied from the saved ExamSys pages are in [ExamSys Assets](<ExamSys Assets>).

## Q1. Java Basics

Which of the following statements is true for Java?

1. Only one class in a Java program can have a `main()` function, otherwise it will not be clear which `main()` to run.
2. Every class needs to have a `main()` function, in case it is called.
3. If you add a `main()` function to a class, and create an object of that class, you can call the private methods/functions of that class directly from within `main`.
4. More than one of the above answers are correct.
5. None of the above are true.

**Guidance:** Statement 3 is true. Code inside a class can access private members of objects of that same class. Multiple classes can have `main`, and most classes do not need one.

## Q2. `main()`

The following Java code, which would be put into `Test.java`, compiled, then executed using `java Test`, has missing words. Fill the gaps.

```java
___ class ___
{
    public static ___ main(String[] args)
    {
        System.out.___("Hello World");
    }
}
```

**Likely answer:**

```java
public class Test
{
    public static void main(String[] args)
    {
        System.out.println("Hello World");
    }
}
```

## Q3. `main` Explanation

Explain briefly what each missing word from Q2 means and what it does.

**Guidance:** Explain `public`, `class`, `Test`, `void`, `main`, `String[] args`, and `println`. Mention that `main` is the JVM entry point and is `static` because no object exists yet.

## Q4. Inheritance

Inheritance is a key concept in the object-oriented paradigm. Briefly explain what inheritance is and why it is useful.

**Guidance:** Inheritance lets a class specialise another class. A subclass inherits fields/methods from a superclass and can override behaviour. It is useful for reuse, specialisation, and subtype polymorphism.

```java
class Animal {
    String noise() { return "unknown"; }
}

class Bear extends Animal {
    @Override
    String noise() { return "growl"; }
}
```

## Q5. Inheritance Class Diagram

Consider the simplified class diagram, where `A` is a class. Select all true statements.

![Q5 class diagram](<Q05-class-diagram.png>)

1. The Java code may somewhere include `D extends B`.
2. The Java code may somewhere include `D implements B`.
3. The Java code may somewhere include `D extends C`.
4. The Java code may somewhere include `D implements C`.

**Guidance:** `B` must be a class because it inherits from class `A`, so `D extends B` is plausible. `D implements B` is not. Since Java cannot extend two classes, `C` is most likely an interface, so `D implements C` is plausible and `D extends C` is not.

## Q6. `@Override`

Briefly explain what the annotation `@Override` does in Java and when it would be used.

**Guidance:** `@Override` tells the compiler that a method is intended to override a method from a superclass or interface. It catches mistakes such as misspelling the method name or using the wrong parameters.

```java
@Override
public String toString() {
    return "Item";
}
```

## Q7. Aggregation, Composition, Inheritance

Which are entirely true?

1. Aggregation models the IS-A relationship.
2. Composition models the HAS-A relationship.
3. Inheritance and aggregation both allow a class to include/reuse functionality from another class, reducing code that would otherwise be needed.

**Guidance:** 2 and 3 are true. Aggregation/composition are HAS-A. Inheritance is IS-A.

## Q8. Encapsulation and Data Hiding

Which are entirely true?

1. Aggregation is the idea that you store the data and the methods which act upon it together in a class.
2. Data hiding is the idea that you make data inaccessible by hiding it inside a class and only expose the data through functions.
3. The two ideas of putting data and methods together, and hiding the data, are often used together in OO programs.

**Guidance:** 2 and 3 are true. Statement 1 describes encapsulation, not aggregation.

## Q9. `protected`

Which are entirely true?

1. If you label data as `protected`, a subclass can access this data.
2. If you label data as `protected`, it is possible for a class which is not a subclass to access that data.
3. If you label data as `protected`, all classes can access that data.

**Guidance:** 1 is true. 2 can also be true for classes in the same package. 3 is false.

## Q10. Private Data

Which are entirely true?

1. You should make data private if possible, because it limits what other programmers can do with it.
2. You should make data private because you should not trust other programmers and should make it as hard as possible for them to change things.
3. Making data private means other classes cannot normally access it directly.

**Guidance:** 1 and 3 are the sensible true statements. 2 is too hostile/misleading: the point is controlled access and maintaining invariants, not distrust for its own sake.

## Q11. Lambda Expressions

Which are entirely true?

1. Lambda expressions in Java add more functionality than inner classes, so they are not just syntactic sugar.
2. Lambda expressions can capture the values of some variables from the surrounding function, but some variables cannot be captured.
3. If you see Java code `a -> b`, then `a` must be an object reference and `b` must be an attribute of the object `a` refers to.

**Guidance:** 2 is true. 1 is false for the course framing: lambdas are shorthand for single-method interfaces. 3 is false: `->` is lambda syntax, not C-style pointer/member syntax.

## Q12. Java Strings, Part 1

Consider:

```java
public String handleString(String str)
{
    str = str + " world";
    return str;
}
```

And:

```java
String str = "Hello";
System.out.println(handleString(str));
System.out.println(str);
```

Select all true statements.

1. `handleString()` will change the `String` that is passed in, adding `" world"` to the end of it.
2. The first line of output will be `Hello`.
3. The first line of output will be `Hello world`.

**Guidance:** 3 is true. Strings are immutable; `str + " world"` creates a new string, returned by the function.

## Q13. Java Strings, Part 2

For the same code, select all true statements.

1. The second line of output will be `Hello`.
2. The second line of output will be `Hello world`.
3. Only one line of text will be output.

**Guidance:** 1 is true. The original caller variable still refers to `"Hello"`.

## Q14. Overloaded `multiply`

Consider:

```java
public int multiply(int v1, int v2)
{
    return v1 * v2;
}

public double multiply(double v1, double v2)
{
    return v1 * v2;
}
```

Select all true statements.

1. This code would not compile because there are two functions of the same name.
2. This is an example of ad-hoc polymorphism.
3. We could also add a function with the same name that takes two `int`s and returns a `double`, to give flexibility.

**Guidance:** 2 is true. 1 is false because Java allows overloading. 3 is false if the parameter list is still two `int`s; Java cannot overload on return type alone.

## Q15. Static and Class Context

For the same `multiply` methods, select all true statements.

1. In Java, each of these functions would need to be defined within a class for the code to compile, not as global functions.
2. The first function would still work in the same way if it was made static.
3. The code would still work if both functions were made static in the same class.

**Guidance:** All three are true, assuming the methods do not depend on instance fields.

## Q16. Design Pattern A

This class diagram illustrates one of the design patterns from the course. The class names have been replaced with `CLASS1` and `CLASS2`. What is the pattern?

![Q16 design pattern A](<Q16-design-pattern-a.png>)

**Answer:** Factory pattern.

**Why:** A concrete creator/factory creates concrete products while client code can work through interfaces.

## Q17. Design Pattern B

This class diagram illustrates one design pattern. The class name has been replaced by `CLASSNAME`. What is the pattern?

![Q17 design pattern B](<Q17-design-pattern-b.png>)

**Answer:** Observer pattern.

**Why:** A `Subject` stores/registers objects implementing an interface and calls a method on all of them when something happens.

## Q18. Design Pattern C

This class diagram illustrates one design pattern. The class name has been replaced by `CLASSNAME`. What is the pattern?

![Q18 design pattern C](<Q18-design-pattern-c.png>)

**Answer:** Strategy pattern.

**Why:** `Subject` has one strategy object, can set/change it, and delegates an operation to interchangeable implementations.

## Q19. Explain the Strategy Pattern

The strategy pattern is useful. Explain briefly what it is, why it is used, and how it is implemented in Java.

**Model answer:** Strategy is a behavioural design pattern where a class delegates part of its behaviour to another object, called a strategy. It is used when there are multiple interchangeable ways to perform a responsibility, and we want to switch between them without changing the main class.

In Java, this is usually implemented with an interface for the strategy, multiple concrete classes implementing that interface, and a field in the main class storing a reference to the current strategy.

```java
interface SortStrategy {
    void sort(List<String> data);
}

class AlphabeticalSort implements SortStrategy {
    public void sort(List<String> data) {
        Collections.sort(data);
    }
}

class Processor {
    private SortStrategy strategy;

    public void setStrategy(SortStrategy strategy) {
        this.strategy = strategy;
    }

    public void process(List<String> data) {
        strategy.sort(data);
    }
}
```

Course example: Swing layout managers such as `FlowLayout` and `GridLayout`.

## Q20. Parametric Polymorphism in Java

Explain what parametric polymorphism is and how it is implemented in Java, including example code. You do not need to mention the problems of Java's implementation.

**Model answer:** Parametric polymorphism means writing code with a type parameter so the same class or method can work with different types. Java implements this using generics.

```java
public class Box<T> {
    private T value;

    public Box(T value) {
        this.value = value;
    }

    public T get() {
        return value;
    }
}
```

Use:

```java
Box<String> nameBox = new Box<>("Alex");
Box<Integer> numberBox = new Box<>(5);
```

The same `Box<T>` class works with different types.

## Q21. Adding to a Generic List

Assume you are provided with a generic class `List` for a list of type `T` objects, and a generic class `ListItem` which stores each entry of the list.

Provide the full implementation of a function of the `List` class which creates a new `ListItem` object and links it into the head/start of the list. Include definitions of any variables needed and explain assumptions.

**Model answer:**

```java
public class List<T> {
    private ListItem<T> head = null;

    public void add(T item) {
        ListItem<T> newItem = new ListItem<>(item, head);
        head = newItem;
    }
}
```

Assuming `ListItem<T>` is something like:

```java
public class ListItem<T> {
    private T value;
    private ListItem<T> next;

    public ListItem(T value, ListItem<T> next) {
        this.value = value;
        this.next = next;
    }

    public T getValue() {
        return value;
    }

    public ListItem<T> getNext() {
        return next;
    }
}
```

Explanation: `head` stores the first item in the list. To add at the front, create a new `ListItem` whose `next` points to the old `head`, then update `head` to point to the new item.

