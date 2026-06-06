# Java and OO Exam Guide

Based on: [Lecture Slides](<Lecture Slides>) and [PGP Wrapup](<99 - PGP Wrapup.pdf>).

Note: I did not find a separate official Java/OO exam guide in Downloads. This is a revision guide built from the Java lecture slide topics and the Java/OO exam information in the PGP wrapup.

## Assessment Context

The Programming Paradigms exam covers both functional programming/Haskell and object-oriented programming/Java.

From the PGP wrapup:

- the exam is in person;
- it is an ExamSys exam;
- it lasts two hours;
- there are questions on both paradigms;
- exam guides are available on Moodle.

For the Java side, expect questions to test:

- understanding of object-oriented ideas;
- ability to read and write small Java examples;
- ability to explain relationships between classes;
- recognition of patterns used in the Java/Swing examples;
- comparison between procedural C-style code and object-oriented Java design.

## Java/OO Wrapup Checklist

The PGP wrapup explicitly says you should know these OO features:

- objects and classes;
- encapsulation;
- abstraction and interfaces;
- data hiding;
- composition and aggregation;
- inheritance;
- sub-type polymorphism, also called dynamic dispatch or late binding;
- generics, as parametric polymorphism;
- anonymous classes and lambdas;
- design patterns and standard solutions;
- Java UI classes as examples of OO design principles.

The wrapup also stresses that these ideas are not Java-only. Java is the language used to learn and illustrate broader OO design principles.

## Java Benefits and Comparisons

The wrapup highlights why Java is useful for OO development:

- Java code is compiled to `.class` files.
- `.class` files run on the Java virtual machine.
- Java programs can often be compiled once and run elsewhere on a suitable JVM.
- Java simplifies or removes many C/C++ memory-management problems.
- Garbage collection handles object cleanup after references disappear.
- Java avoids common pointer errors such as use-after-free, forgetting to free memory, and freeing memory twice.

The wrapup also compares OO and FP:

- OO usually works with mutable object state.
- Controlling who can change state is central to OO design.
- Java can use `final` or omit setters to make some objects immutable.
- FP usually treats data as immutable.
- OO helps decompose larger problems into independent parts.
- OO supports reuse through inheritance, aggregation/composition, and standard libraries.

## Core Java Topics

### Classes and Objects

Know the difference between a class and an object.

- A class is a blueprint or design.
- An object is an instance created from a class.

```java
public class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}

Person p = new Person("Alex");
```

Likely question style:

- Explain class versus object.
- Write a small class with fields and methods.
- Identify which parts of code are class-level and which are object-level.

### Encapsulation and Data Hiding

Encapsulation means putting data and the methods that operate on it in the same class. Data hiding means restricting direct access to fields.

```java
public class Counter {
    private int value = 0;

    public void increment() {
        value++;
    }

    public int getValue() {
        return value;
    }
}
```

Avoid exposing fields directly:

```java
counter.value = 100; // bad design if value should be controlled
```

Likely question style:

- Explain why fields are usually `private`.
- Write getters/setters.
- Explain how encapsulation improves maintainability.

### Static Versus Instance Members

Instance members belong to individual objects. Static members belong to the class itself.

```java
public class Ball {
    private static int count = 0;
    private int x;

    public Ball() {
        count++;
    }

    public static int getCount() {
        return count;
    }
}
```

Important:

- Static methods have no `this`.
- `main` is static because the program starts before any object has been created.
- Static methods can feel like C-style global functions, but overusing them leads to procedural Java rather than OO Java.

Likely question style:

- Explain why `main` is static.
- Explain why a static method cannot directly use instance fields.
- Compare static data with per-object data.

## Object-Oriented Relationships

### Aggregation and Composition: Has-A

Aggregation/composition means one object contains or uses another object.

```java
import java.util.ArrayList;

public class Notebook {
    private ArrayList<String> notes = new ArrayList<>();

    public void addNote(String note) {
        notes.add(note);
    }

    public int getNoteCount() {
        return notes.size();
    }
}
```

`Notebook` has an `ArrayList<String>`.

Likely question style:

- Identify a has-a relationship.
- Explain why wrapping an `ArrayList` inside a class is abstraction.
- Draw or interpret a simple class diagram showing aggregation.

### Inheritance: Is-A

Inheritance means one class is a specialised type of another.

```java
public class Animal {
    public String getNoise() {
        return "Unknown";
    }
}

public class Bear extends Animal {
    @Override
    public String getNoise() {
        return "Growl";
    }
}
```

A `Bear` is an `Animal`.

```java
Animal a = new Bear();
System.out.println(a.getNoise()); // Growl
```

This demonstrates sub-type polymorphism: the reference type is `Animal`, but the actual object is `Bear`, so the overridden method in `Bear` runs.

Likely question style:

- Explain is-a versus has-a.
- Explain method overriding.
- Predict output from superclass references pointing to subclass objects.
- Explain polymorphism using an array of superclass references.

## Abstract Classes and Interfaces

An abstract class can contain both implemented and unimplemented methods.

```java
public abstract class Animal {
    public abstract String getNoise();

    public void sleep() {
        System.out.println("Sleeping");
    }
}
```

An interface specifies methods that implementing classes must provide.

```java
public interface Animal {
    String getName();
    String getNoise();
}

public class Fish implements Animal {
    public String getName() {
        return "Fish";
    }

    public String getNoise() {
        return "Blub";
    }
}
```

Likely question style:

- Compare abstract classes and interfaces.
- Explain why GUI listeners use interfaces.
- Explain `extends` versus `implements`.

## Access Modifiers

Know the main access levels:

- `public`: accessible from anywhere.
- `private`: accessible only inside the same class.
- `protected`: accessible in the same class, package, and subclasses.
- no modifier: package-private.

Likely question style:

- Decide whether code can access a field or method.
- Explain why private fields are good practice.
- Explain why package structure matters.

## Exceptions

Exceptions report exceptional situations without relying on special return values.

```java
public static int divide(int x, int y) {
    if (y == 0) {
        throw new ArithmeticException("division by zero");
    }
    return x / y;
}
```

Handle exceptions with `try` and `catch`.

```java
try {
    System.out.println(divide(10, 0));
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
```

Likely question style:

- Explain what throwing an exception means.
- Write a `try`/`catch` block.
- Explain why specific exceptions should be caught before general exceptions.
- Explain why exceptions fit naturally with inheritance.

## Generics, Collections, and Boxing

Generics let classes and methods work with a type parameter.

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
Box<String> name = new Box<>("Alex");
Box<Integer> number = new Box<>(3);
```

Important points:

- Java generics use type erasure.
- Primitive types like `int` are not objects.
- Use wrapper classes such as `Integer`, `Double`, and `Boolean`.
- Autoboxing converts primitives to wrappers where needed.

```java
ArrayList<Integer> nums = new ArrayList<>();
nums.add(1); // int autoboxed to Integer
```

Likely question style:

- Explain why `ArrayList<int>` is invalid.
- Explain autoboxing.
- Write or use a generic class.
- Explain why collections use generics.

## Iterators

The Iterator pattern gives a standard way to move through a collection.

```java
Iterator<String> it = list.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

For-each loops use `Iterable`.

```java
for (String item : list) {
    System.out.println(item);
}
```

Likely question style:

- Explain the difference between `Iterable` and `Iterator`.
- Write code using an iterator.
- Explain how for-each loops are supported.
- Recognise Iterator as a design pattern.

## GUI, Events, and Listeners

Swing GUIs use components and containers:

- `JFrame`: window;
- `JPanel`: container for grouping components;
- `JLabel`: text/display component;
- `JButton`: clickable button.

```java
JFrame frame = new JFrame("Demo");
JLabel label = new JLabel("Hello");
JButton button = new JButton("Click");

frame.add(label);
frame.add(button);
frame.pack();
frame.setVisible(true);
```

Events use listener interfaces.

```java
button.addActionListener(e -> label.setText("Clicked"));
```

Likely question style:

- Explain how a button click is handled.
- Explain why `ActionListener` is an interface.
- Recognise this as the Observer pattern.

## Inner Classes, Anonymous Classes, and Lambdas

An inner class is a class defined inside another class.

```java
public class Outer {
    private int value = 10;

    public class Inner {
        public void print() {
            System.out.println(value);
        }
    }
}
```

An anonymous class creates a one-off class at the point where an object is needed.

```java
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        label.setText("Clicked");
    }
});
```

A lambda is shorter syntax for a single-method interface.

```java
button.addActionListener(e -> label.setText("Clicked"));
```

Likely question style:

- Explain when anonymous classes are useful.
- Convert an anonymous listener into a lambda.
- Explain why lambdas only work for single-method interfaces.

## Design Patterns

### Strategy

Strategy delegates a responsibility to another object so behaviour can change.

Example from slides: layout managers.

```java
frame.setLayout(new FlowLayout());
frame.setLayout(new GridLayout(2, 2));
```

Likely angle: explain how changing the layout object changes behaviour without changing the frame class.

### Observer

Observer lets objects register interest in events and be notified later.

Example from slides: `ActionListener`.

```java
button.addActionListener(listener);
```

Likely angle: the button does not know what the listener will do; it only knows it can call the listener method.

### Iterator

Iterator provides a standard way to traverse a collection.

```java
Iterator<T> iterator()
```

Likely angle: explain `Iterable` creates iterators, while `Iterator` stores traversal state.

### Singleton

Singleton ensures only one object of a class is created.

```java
public class Singleton {
    private static Singleton oneObject = null;

    private Singleton() { }

    public static Singleton get() {
        if (oneObject == null) {
            oneObject = new Singleton();
        }
        return oneObject;
    }
}
```

Likely angle: private constructor prevents external `new`; static method controls creation.

### Factory

Factory moves object creation into a separate object or method.

```java
public class AnimalFactory {
    public Animal createFish() {
        return new Fish();
    }
}
```

Likely angle: client code can work with the base type or interface without knowing the exact concrete class.

## What Is Most Likely To Come Up

This is not a prediction of the exact exam. It is a practical priority list based on the lecture coverage.

### Highest Priority

Know these cold:

- class versus object;
- fields, methods, constructors;
- `private` fields with public methods;
- `static` versus instance;
- has-a versus is-a;
- inheritance and overriding;
- interfaces;
- polymorphism.

If you can write a small class and explain how objects interact, you have the foundation.

### Very Likely

Practise:

- reading small Java snippets and predicting output;
- writing a class with constructor, getters, and setters;
- using an `ArrayList`;
- explaining why direct field access is poor design;
- explaining why Java removed C-style pointer and memory-management complexity;
- drawing or interpreting simple class diagrams.

### Higher-Mark Material

Revise:

- exceptions;
- generics and boxing;
- iterators and `Iterable`;
- Swing events and listeners;
- anonymous classes and lambdas;
- Strategy, Observer, Iterator, Singleton, and Factory patterns.

## Suggested Revision Order

1. Java syntax and `main`.
2. Classes, objects, fields, methods, constructors.
3. Encapsulation and access modifiers.
4. Aggregation/composition.
5. Inheritance and polymorphism.
6. Interfaces and abstract classes.
7. Exceptions.
8. Swing GUI, listeners, and events.
9. Generics, boxing, collections, iterators.
10. Anonymous classes, lambdas, and design patterns.

## Answer Strategy

For explanation questions:

1. Define the concept.
2. Give a tiny Java example.
3. Explain why the concept is useful.
4. Link it to OO design.

For code-writing questions:

1. Start with the class header.
2. Add private fields.
3. Add constructor.
4. Add public methods.
5. Use `@Override` when overriding.
6. Keep relationships clear: use inheritance only for is-a, fields for has-a.
