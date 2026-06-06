# UML Class Diagram Guide

This guide focuses on the UML you need for the Java/OO part of PGP: mainly class diagrams, relationships, access modifiers, and how to translate between diagrams and Java code.

Extracted visual assets:

- [UML Assets](<UML Assets>) - diagrams pulled from the Java lecture slides.
- [ExamSys Assets](<ExamSys Assets>) - diagrams copied from the ExamSys practice questions.

## 1. What UML Is For

UML stands for Unified Modeling Language. In this course, it is mainly used to draw class diagrams: pictures showing classes, interfaces, fields, methods, and relationships between types.

Class diagrams help you see:

- what classes exist;
- what data and methods each class has;
- which classes inherit from others;
- which classes contain or use others;
- where interfaces fit into a design;
- which design pattern a diagram represents.

## 2. Basic Class Box

A UML class is usually drawn as a box with three sections:

![basic class box](<uml-01-basic-class.png>)

Example:

![Person class diagram](<uml-02-person-class.png>)

Equivalent Java:

```java
public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

## 3. Visibility Symbols

UML uses symbols to show access modifiers:

![visibility symbols](<uml-03-visibility.png>)

Examples:

![visibility example class](<uml-04-visibility-example.png>)

Java:

```java
private int value;

public int getValue() {
    return value;
}

protected void helper() {
}
```

Exam tip: private fields plus public methods usually signal encapsulation/data hiding.

## 4. Fields

Field format:

![field format](<uml-05-field-format.png>)

Example:

![fields example](<uml-06-fields-example.png>)

Java:

```java
private ArrayList<String> data;
private int count;
```

## 5. Methods

Method format:

![method format](<uml-07-method-format.png>)

Example:

![methods example](<uml-08-methods-example.png>)

Java:

```java
public void add(Item item) {
}

public Item get(int index) {
    return null;
}

public int size() {
    return 0;
}
```

Constructors often appear as methods with the same name as the class and no return type:

![constructor example](<uml-09-constructor.png>)

Java:

```java
public Person(String name) {
    this.name = name;
}
```

## 6. Interfaces

Interfaces are often shown with `<<interface>>`.

![Animal interface diagram](<uml-10-interface-animal.png>)

Java:

```java
public interface Animal {
    String getName();
    String getNoise();
}
```

A class implementing an interface:

```java
public class Fish implements Animal {
    public String getName() {
        return "Fish";
    }

    public String getNoise() {
        return "Blub";
    }
}
```

## 7. Inheritance: Is-A

Inheritance is shown with a solid line and a hollow triangle pointing to the superclass.

![Bear inherits Animal](<uml-11-bear-animal.png>)

Read this as: `Bear` is an `Animal`.

Java:

```java
public class Animal {
}

public class Bear extends Animal {
}
```

Use inheritance for IS-A relationships:

![IS-A examples](<uml-12-is-a-examples.png>)

Do not use inheritance for HAS-A relationships.

## 8. Interface Implementation

Interface implementation is often shown with a dashed line and hollow triangle pointing to the interface. In simplified course diagrams, you may just see the hollow triangle.

![Fish implements Animal](<uml-13-fish-interface.png>)

Java:

```java
public class Fish implements Animal {
}
```

Important Java distinction:

```java
class Subclass extends Superclass
class ClassName implements InterfaceName
interface ChildInterface extends ParentInterface
```

## 9. Association

Association means one class knows about or uses another. It is often shown as a plain line.

![association example](<uml-14-association.png>)

This might mean an `Order` has a reference to a `Customer`.

Java:

```java
public class Order {
    private Customer customer;
}
```

Association is a broad relationship. Aggregation and composition are more specific versions of association.

## 10. Aggregation: Has-A

Aggregation is a HAS-A relationship where one object contains or refers to another, but the contained object can exist independently.

UML: hollow diamond at the containing/whole side.

![aggregation example](<uml-15-aggregation.png>)

Read as: a `Team` has `Player`s.

Java:

```java
public class Team {
    private ArrayList<Player> players;

    public Team(ArrayList<Player> players) {
        this.players = players;
    }
}
```

The players might exist outside the team too.

## 11. Composition: Strong Has-A

Composition is a stronger HAS-A relationship. The contained parts are owned by the whole and usually do not make sense independently.

UML: filled diamond at the containing/whole side.

![composition example](<uml-16-composition.png>)

Java:

```java
public class House {
    private ArrayList<Room> rooms = new ArrayList<>();

    public House() {
        rooms.add(new Room("Kitchen"));
        rooms.add(new Room("Bedroom"));
    }
}
```

Composition suggests the whole controls the lifetime of the parts.

For this module, the slides often group aggregation/composition together as objects containing other objects, or HAS-A.

## 12. Dependency

Dependency means one class uses another temporarily, often as a method parameter or local variable.

UML: dashed arrow.

![dependency example](<uml-17-dependency.png>)

Java:

```java
public class ReportGenerator {
    public void printReport(Printer printer) {
        printer.print("Report");
    }
}
```

The `ReportGenerator` uses `Printer`, but does not necessarily store one as a field.

## 13. Multiplicity

Multiplicity shows how many objects are involved.

Common symbols:

![multiplicity key](<uml-18-multiplicity-key.png>)

Example:

![Library to Book multiplicity](<uml-19-library-books.png>)

Read as: one library has many books.

Java:

```java
public class Library {
    private ArrayList<Book> books;
}
```

## 14. Abstract Classes and Methods

Abstract classes/methods are often shown in italics, or with `{abstract}`.

![abstract Animal class](<uml-20-abstract-animal.png>)

Java:

```java
public abstract class Animal {
    public abstract String getNoise();

    public void sleep() {
        System.out.println("Sleeping");
    }
}
```

An abstract class cannot be directly instantiated.

```java
Animal a = new Animal(); // not allowed if Animal is abstract
```

## 15. Static Members

Static fields or methods may be underlined in UML.

![static Counter class](<uml-21-static-counter.png>)

If `count` and `getCount()` are underlined, they are static.

Java:

```java
public class Counter {
    private static int count = 0;

    public static int getCount() {
        return count;
    }
}
```

Static means class-level, not object-level.

## 16. Reading Course Diagrams

For the PGP Java slides and ExamSys diagrams, focus on:

- hollow triangle pointing upward: inheritance or interface implementation;
- diamond: object contains/has other objects;
- `<<interface>>`: interface;
- method names in boxes: operations the class/interface supports;
- class names like `Subject`, `Observer`, `Strategy`, `Factory`: likely design pattern clues.

## 17. Common Design Pattern Diagrams

### Observer

Typical structure:

![Observer generic structure](<uml-22-observer-generic.png>)

Meaning:

- `Subject` stores observers/listeners.
- Observers implement an interface.
- Subject has methods like `register`, `unregister`, `notify`, or `doAll`.

Java example:

```java
button.addActionListener(listener);
```

`JButton` is the subject. `ActionListener` is the observer interface.

Course slide version:

![Observer pattern from Java slides](<L10-p16-01.png>)

ExamSys-style version:

![Observer pattern from ExamSys](<Q17-design-pattern-b.png>)

### Strategy

Typical structure:

![Strategy generic structure](<uml-23-strategy-generic.png>)

Meaning:

- Context stores one strategy object.
- Strategies implement the same interface.
- Context delegates work to the strategy.

Java example:

```java
frame.setLayout(new FlowLayout());
frame.setLayout(new GridLayout(2, 2));
```

The layout manager is the strategy.

Course slide version:

![Strategy pattern from Java slides](<L10-p14-01.png>)

ExamSys-style version:

![Strategy pattern from ExamSys](<Q18-design-pattern-c.png>)

### Iterator

Typical structure:

![Iterable and Iterator interfaces](<uml-24-iterator-interfaces.png>)

Java:

```java
Iterator<Item> it = inv.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

### Singleton

Typical structure:

![Singleton class diagram](<uml-25-singleton.png>)

Java:

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

Clues:

- private constructor;
- static field of same type;
- static method returning the one object.

### Factory

Typical structure:

![Factory pattern structure](<uml-26-factory.png>)

Java:

```java
public class AnimalFactory {
    public Animal createFish() {
        return new Fish();
    }
}
```

Clue: a class or method creates objects for you, often returning an interface/base type.

ExamSys-style version:

![Factory pattern from ExamSys](<Q16-design-pattern-a.png>)

## 18. Course Diagram Examples

### Multiple Inheritance-Looking Diagram

This ExamSys diagram is useful because it tests whether you can distinguish `extends` and `implements`.

![Class inheritance/interface diagram](<Q05-class-diagram.png>)

Read it carefully:

- `B` points to `A`, and `A` is stated to be a class, so `B` is a subclass of `A`.
- `D` points to both `B` and `C`.
- Java classes cannot extend two classes.
- Therefore, if `D extends B` is true, then `C` is likely an interface and `D implements C`.

Likely Java shape:

```java
public class A {
}

public class B extends A {
}

public interface C {
}

public class D extends B implements C {
}
```

## 19. How To Translate UML Into Java

### Class

UML:

![Person class name](<uml-27-person-name.png>)

Java:

```java
public class Person {
}
```

### Interface

UML:

![Drawable interface](<uml-28-drawable-interface.png>)

Java:

```java
public interface Drawable {
}
```

### Field

UML:

![field example](<uml-29-field-name.png>)

Java:

```java
private String name;
```

### Method

UML:

![method example](<uml-30-draw-method.png>)

Java:

```java
public void draw() {
}
```

### Inheritance

UML:

![Bear extends Animal](<uml-31-translate-inheritance.png>)

Java:

```java
public class Bear extends Animal {
}
```

### Interface Implementation

UML:

![ButtonHandler implements ActionListener](<uml-32-translate-interface.png>)

Java:

```java
public class ButtonHandler implements ActionListener {
}
```

### Has-A

UML:

![Inventory has Item](<uml-33-translate-has-a.png>)

Java:

```java
public class Inventory {
    private ArrayList<Item> data;
}
```

## 20. How To Answer UML Exam Questions

Use this checklist:

1. Identify classes and interfaces.
2. Look for `<<interface>>`.
3. Look for hollow triangles: inheritance or implementation.
4. Look for diamonds: has-a relationship.
5. Translate relationships into `extends`, `implements`, or fields.
6. Identify whether the relationship is IS-A or HAS-A.
7. If it looks like a design pattern, name the pattern and justify it.

Example answer shape:

![strategy answer shape](<uml-34-answer-shape.png>)

## 21. Common Mistakes

Do not confuse:

- class and object;
- aggregation/composition with inheritance;
- `extends` and `implements`;
- interface and abstract class;
- method overloading and overriding;
- static members and instance members;
- `Iterable` and `Iterator`;
- Strategy and Observer.

Quick distinctions:

![quick UML distinctions](<uml-35-quick-distinctions.png>)
