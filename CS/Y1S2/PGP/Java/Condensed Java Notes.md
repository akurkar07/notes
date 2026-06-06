# Condensed Java Notes

Sources: [Lecture Slides](<Lecture Slides>) and [PGP Wrapup](<99 - PGP Wrapup.pdf>)

These notes are aimed at relearning the Java/OO half of Programming Paradigms. The key thing is not memorising Java library trivia; it is understanding how Java demonstrates object-oriented design.

## 1. Object Orientation

Object-oriented programming models a program as a set of interacting objects. Each object can have:

- state: data stored inside the object;
- behaviour: methods that operate on that data;
- identity: it is a particular thing in memory, separate from other objects of the same class.

A class is the blueprint. An object is an actual instance created from the blueprint.

```java
public class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public void kick(Football ball) {
        ball.move();
    }
}

Person jason = new Person("Jason");
Football ball = new Football();
jason.kick(ball);
```

Core OO ideas:

- class versus object;
- encapsulation: put data and methods together;
- data hiding: restrict direct access to data;
- abstraction: expose what an object can do, not how it does it;
- aggregation/composition: one object has another object;
- inheritance: one class is a specialised kind of another;
- polymorphism: the same method call can run different implementations depending on the runtime object.

The wrapup stresses that these ideas are not Java-only. Java is being used as the language for learning general OO design.

## 2. Java Compared With C

Java deliberately keeps some C-style syntax while removing many low-level C responsibilities.

Similarities:

- braces for blocks;
- semicolons after statements;
- `if`, `for`, `while`;
- familiar primitive types such as `int`, `float`, `double`, `char`, `boolean`;
- array indexing with `[i]`.

Important differences:

- all executable code must be inside a class;
- there are no global functions;
- there is no C-style pointer syntax;
- there is no `malloc`, `sizeof`, or manual `free`;
- objects are created with `new`;
- garbage collection handles cleanup;
- arrays know their own length;
- Java compiles `.java` files to `.class` files, which run on the JVM.

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

`main` has to be `static` because the program starts before any object has been created.

Exam angle: be able to explain that Java simplifies memory management compared with C/C++, especially by avoiding manual deallocation and many pointer errors.

## 3. Static Methods and Procedural Java

The early slides convert C-style code into Java using `static` methods. This is useful for learning syntax, but it is not proper OO design for larger programs.

```java
public class Lecture2 {
    public static void printMessage(String message) {
        System.out.println(message);
    }

    public static void main(String[] args) {
        printMessage("Hello");
    }
}
```

Static method:

- belongs to the class;
- is called without an object;
- has no `this`;
- can directly access other static members;
- cannot directly access instance fields.

Instance method:

- belongs to an object;
- is called on an object reference;
- has a `this` reference;
- can access that object's fields.

```java
public class Counter {
    private int value = 0;
    private static int created = 0;

    public Counter() {
        created++;
    }

    public void increment() {
        value++;       // instance field
    }

    public static int getCreated() {
        return created; // static field
    }
}
```

Common exam trap:

```java
public static void bad() {
    value++; // error: no current object
}
```

There is no `this` inside a static method, so Java does not know which object's `value` you mean.

## 4. Strings, StringBuffer, and Command-Line Arguments

`String` is a class, but Java gives strings special syntax.

```java
String message = "Hello";
String combined = message + " World";
System.out.println(combined);
```

String concatenation with `+` works left to right.

```java
System.out.println("" + 4 + 5 + "A"); // "45A"
System.out.println(4 + 5 + "A");      // "9A"
```

Why:

- `"" + 4` makes a string, so the rest is concatenation.
- `4 + 5` happens first in the second example, giving `9`, then `"A"` is concatenated.

`String` is immutable, meaning its contents do not change. Operations that appear to change a string create a new string.

```java
String s = "abc";
s = s + "d"; // s now refers to a new String
```

Use `StringBuffer` or `StringBuilder` when you need a mutable character sequence.

```java
StringBuffer copy = new StringBuffer("abc");
copy.setCharAt(0, 'x');
System.out.println(copy); // xbc
```

Command-line arguments are stored in `args`.

```java
public static void main(String[] args) {
    String word = "Hello World";
    if (args.length >= 1) {
        word = args[0];
    }
    System.out.println(word);
}
```

Difference from C: Java's first command-line argument is `args[0]`; the program name is not stored in `args[0]`.

## 5. Classes, Fields, and Methods

A class groups fields and methods.

- Fields store object data.
- Methods define operations.
- The constructor initialises the object.

```java
public class MyClass {
    private String myText;

    public MyClass(String initialText) {
        myText = initialText;
    }

    public void setMyText(String str) {
        myText = str;
    }

    public String getMyText() {
        return myText;
    }
}
```

Creating and using an object:

```java
MyClass object = new MyClass("Hello");
object.setMyText("Goodbye");
System.out.println(object.getMyText());
```

`object.setMyText("Goodbye")` means: follow the reference in `object`, find the actual object, and run `setMyText` on that object.

Reference variables are not objects themselves. They store references to objects.

```java
MyClass a = new MyClass("A");
MyClass b = a;
b.setMyText("B");
System.out.println(a.getMyText()); // B
```

Both `a` and `b` refer to the same object.

## 6. Encapsulation and Data Hiding

Encapsulation means combining data with the methods that operate on it. Data hiding means preventing other classes from directly changing internal fields.

```java
public class BankAccount {
    private int balance;

    public BankAccount(int initialBalance) {
        if (initialBalance >= 0) {
            balance = initialBalance;
        }
    }

    public void deposit(int amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public int getBalance() {
        return balance;
    }
}
```

This protects the invariant that balance should not be changed by arbitrary outside code.

Bad design:

```java
account.balance = -999;
```

Better design:

```java
account.deposit(50);
```

Exam phrase: make fields private and expose public interface methods. The user of the class should know what methods do, not how the data is represented internally.

## 7. Constructors and `this`

A constructor runs automatically when an object is created with `new`.

```java
public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

`this` means "the current object". It is most commonly used when a parameter has the same name as a field.

```java
this.name = name;
```

Left side: field in the object.  
Right side: constructor parameter.

Constructors can be overloaded.

```java
public Person(String name) {
    this.name = name;
    this.age = 0;
}

public Person(String name, int age) {
    this.name = name;
    this.age = age;
}
```

If you do not write any constructor, Java gives a default no-argument constructor. If you write a constructor yourself, Java no longer automatically gives that default.

## 8. Static Fields and Methods

Static fields are shared by all objects of the class.

```java
public class Ball {
    private static int count = 0;
    private int x;
    private int y;

    public Ball(int x, int y) {
        this.x = x;
        this.y = y;
        count++;
    }

    public static int getCount() {
        return count;
    }
}
```

Example:

```java
Ball a = new Ball(0, 0);
Ball b = new Ball(1, 1);
System.out.println(Ball.getCount()); // 2
```

Use static for:

- constants;
- class-wide counters;
- utility methods;
- `main`.

Do not overuse static when the behaviour belongs to an object.

## 9. Packages, Imports, and Access

Packages group related classes and affect access permissions.

```java
package animals;

public class Bear {
}
```

Imports tell Java which class name you mean.

```java
import java.util.ArrayList;

ArrayList<String> lines = new ArrayList<>();
```

Access levels:

- `public`: accessible from anywhere;
- `private`: accessible only inside the same class;
- `protected`: accessible inside the same class, package, and subclasses;
- no modifier: package-private.

Simple examples can be misleading because classes in the same package have extra access. The slides warn that packages matter when demonstrating access permissions.

Exam tip: if asked about good design, prefer `private` fields and `public` methods.

## 10. Aggregation and Composition

Aggregation/composition is a has-a relationship.

```java
import java.util.ArrayList;

public class PGPText {
    private ArrayList<String> lines;

    public PGPText() {
        lines = new ArrayList<>();
    }

    public void addLine(String line) {
        lines.add(line);
    }

    public String getLine(int index) {
        return lines.get(index);
    }

    public int getLineCount() {
        return lines.size();
    }
}
```

`PGPText` has an `ArrayList<String>`.

Why this is good:

- code outside does not need to know how lines are stored;
- `PGPText` can later change its internal representation;
- methods can enforce rules;
- the class has a clear responsibility.

Has-a versus is-a:

```java
class Notebook {
    private ArrayList<String> notes; // has-a
}

class Bear extends Animal {          // is-a
}
```

Use fields for has-a. Use inheritance for is-a.

## 11. Inheritance and Sub-Type Polymorphism

Inheritance creates a specialised version of an existing class.

```java
public class Animal {
    public String getName() {
        return "Animal";
    }

    public String getNoise() {
        return "Unknown";
    }
}

public class Bear extends Animal {
    @Override
    public String getName() {
        return "Bear";
    }

    @Override
    public String getNoise() {
        return "Growl";
    }
}
```

A `Bear` is an `Animal`.

```java
Animal animal = new Bear();
System.out.println(animal.getNoise()); // Growl
```

Sub-type polymorphism means code can use a superclass reference while the actual subclass implementation runs at runtime.

```java
Animal[] animals = {
    new Animal(),
    new Bear(),
    new Fish()
};

for (Animal a : animals) {
    System.out.println(a.getName() + ": " + a.getNoise());
}
```

This is also called dynamic dispatch or late binding. The method implementation is selected using the actual object, not just the declared reference type.

`@Override` is useful because the compiler checks that you really are overriding a superclass method.

```java
@Override
public String getNoise() {
    return "Growl";
}
```

Exam trap: private methods are not overridden in the same way as public/protected methods, because private methods are not visible to subclasses.

## 12. Abstract Classes and Interfaces

An abstract class can define some methods and leave others for subclasses.

```java
public abstract class Animal {
    public abstract String getNoise();

    public void sleep() {
        System.out.println("Sleeping");
    }
}
```

You cannot instantiate an abstract class:

```java
Animal a = new Animal(); // error if Animal is abstract
```

An interface describes required behaviour.

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

Use an interface when you want to say "anything with these methods can be used here".

```java
public static void printAnimal(Animal animal) {
    System.out.println(animal.getName());
}
```

Comparison:

- abstract class: use `extends`; can share code and fields; supports an is-a hierarchy;
- interface: use `implements`; specifies behaviour; useful when unrelated classes should be usable in the same way.

GUI listeners such as `ActionListener` are interfaces because Java only needs to know that an object has an `actionPerformed` method.

## 13. Exceptions

Exceptions report exceptional circumstances through a separate control path.

```java
public static int divide(int x, int y) {
    if (y == 0) {
        throw new ArithmeticException("division by zero");
    }
    return x / y;
}
```

Handling:

```java
try {
    int result = divide(10, 0);
    System.out.println(result);
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
```

Exceptions are objects. Exception classes form an inheritance hierarchy.

```text
Throwable
  Exception
    RuntimeException
  Error
```

Catch clauses are checked in order, so catch specific exceptions before general ones.

```java
try {
    risky();
} catch (InterruptedException e) {
    System.out.println("Interrupted");
} catch (Exception e) {
    System.out.println("Other exception");
}
```

Checked exceptions must usually be caught or declared with `throws`. `RuntimeException` is unchecked and does not have to be declared.

Why exceptions matter for OO:

- they are objects;
- specialised exceptions are subclasses;
- catching a superclass can catch many subclass exceptions;
- this demonstrates inheritance and polymorphism.

## 14. Swing GUIs

Swing uses objects heavily. GUIs are built from components and containers.

Common classes:

- `JFrame`: a window;
- `JPanel`: a container for grouping components;
- `JLabel`: displays text or images;
- `JButton`: clickable button;
- layout managers: decide component arrangement.

```java
import javax.swing.JFrame;
import javax.swing.JLabel;

public class GUIHelloWorld {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Demo");
        JLabel label = new JLabel("Hello");

        frame.getContentPane().add(label);
        frame.pack();
        frame.setVisible(true);
    }
}
```

Containers have components.

```java
JPanel panel = new JPanel();
panel.add(new JLabel("A"));
panel.add(new JButton("Click"));
frame.add(panel);
```

Layout managers are an example of the Strategy pattern. The container delegates layout decisions to a separate object.

```java
frame.setLayout(new java.awt.FlowLayout());
frame.setLayout(new java.awt.GridLayout(2, 2));
```

Same frame, different layout strategy.

## 15. Events, Buttons, and Observer

GUI events use listeners. A button does not know what should happen when clicked; it only knows which listeners to notify.

```java
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JLabel;

public class ButtonHandler implements ActionListener {
    private JLabel label;

    public ButtonHandler(JLabel label) {
        this.label = label;
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        label.setText(label.getText() + ".");
    }
}
```

Register the listener:

```java
button.addActionListener(new ButtonHandler(label));
```

This demonstrates the Observer pattern:

- subject: the button;
- observer/listener: the `ActionListener`;
- event: button click;
- registration: `addActionListener`;
- notification: Java calls `actionPerformed`.

Exam phrase: the button is decoupled from the action. It only relies on the listener interface.

## 16. Final, Inner Classes, and Adapters

`final` means unchangeable in different contexts.

```java
public final class FinalClass { }       // cannot be extended
public final void f() { }               // cannot be overridden
public static final int MAX_VALUE = 3;  // constant
final int local = 10;                   // cannot be reassigned
```

Inner classes are classes defined inside other classes.

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

An inner class object is associated with an outer class object, so it can access members of that outer object.

Use inner classes when:

- the helper class is only useful inside the outer class;
- the helper needs access to outer fields;
- implementing event handlers;
- implementing iterators.

Adapters are classes with empty implementations of listener methods. They are useful when an interface has many methods but you only care about one.

```java
class MyMouseHandler extends java.awt.event.MouseAdapter {
    @Override
    public void mouseClicked(java.awt.event.MouseEvent e) {
        System.out.println("Clicked");
    }
}
```

Without an adapter, implementing `MouseListener` directly requires all methods.

## 17. Generics and Boxing

Generics are Java's parametric polymorphism. Parametric polymorphism means writing code with a type parameter, so the same class or method can work for many different types without being rewritten for each one.

In Java, the type parameter is usually written as `T`, but the name is not special. `T` stands for "some type that will be chosen later".

```java
public class Wrapper<T> {
    private T data;

    public Wrapper(T data) {
        this.data = data;
    }

    public T get() {
        return data;
    }
}
```

Use:

```java
Wrapper<String> w = new Wrapper<>("hello");
String s = w.get();
```

Here, `Wrapper<T>` is the generic class. `Wrapper<String>` is a version of that class where `T` is treated as `String`.

Why generics are useful:

- avoid copy-pasting `ArrayInt`, `ArrayString`, `ArrayDouble`, etc.;
- improve type safety;
- reduce casts in user code;
- make reusable containers.

Generic method example:

```java
public static <T> void printTwice(T item) {
    System.out.println(item);
    System.out.println(item);
}
```

This method is also parametrically polymorphic: it can print a `String`, an `Integer`, a `Person`, or any other object type.

Parametric polymorphism is different from sub-type polymorphism:

- sub-type polymorphism: a superclass or interface reference can point to different subclass objects;
- parametric polymorphism: the code is written using a type parameter such as `T`.

```java
// Sub-type polymorphism
Animal a = new Bear();
a.getNoise();

// Parametric polymorphism
Wrapper<Bear> bearBox = new Wrapper<>(new Bear());
Wrapper<Fish> fishBox = new Wrapper<>(new Fish());
```

Type erasure:

- Java checks generic types at compile time;
- much generic type information is removed at runtime;
- this is why arrays of `T` are awkward.

Awkward:

```java
// T[] data = new T[10]; // not allowed
```

Common workaround:

```java
private Object[] data = new Object[10];
```

Then cast when returning:

```java
@SuppressWarnings("unchecked")
public T get(int index) {
    return (T) data[index];
}
```

Primitive types such as `int` are not objects, so generics use wrapper classes.

```java
ArrayList<Integer> nums = new ArrayList<>();
nums.add(1); // autoboxing from int to Integer
int x = nums.get(0); // unboxing from Integer to int
```

Wrapper examples:

- `int` -> `Integer`;
- `double` -> `Double`;
- `boolean` -> `Boolean`;
- `char` -> `Character`.

## 18. Collections and Iterators

Java collection classes such as `ArrayList` and `LinkedList` are generic.

```java
import java.util.ArrayList;
import java.util.Collections;

ArrayList<String> list = new ArrayList<>();
list.add("Item 1");
list.add("Item 4");
list.add("Item 3");

Collections.sort(list);
Collections.reverse(list);
```

Important difference from FP/Haskell: Java collection operations often mutate the existing collection rather than returning a new one.

```java
Collections.sort(list); // changes list
```

The Iterator pattern separates traversal from storage.

```java
import java.util.Iterator;

Iterator<String> it = list.iterator();
while (it.hasNext()) {
    String item = it.next();
    System.out.println(item);
}
```

Two interfaces:

- `Iterable<T>`: something that can produce an iterator;
- `Iterator<T>`: object that remembers traversal state.

```java
public interface Iterable<T> {
    Iterator<T> iterator();
}

public interface Iterator<T> {
    boolean hasNext();
    T next();
}
```

For-each loops use `Iterable`.

```java
for (String item : list) {
    System.out.println(item);
}
```

Skeleton for a custom iterable class:

```java
public class GenArray<T> implements Iterable<T> {
    private Object[] data = new Object[10];
    private int size = 0;

    public void add(T item) {
        data[size] = item;
        size++;
    }

    @Override
    public Iterator<T> iterator() {
        return new MyIterator();
    }

    private class MyIterator implements Iterator<T> {
        private int index = 0;

        public boolean hasNext() {
            return index < size;
        }

        @SuppressWarnings("unchecked")
        public T next() {
            T item = (T) data[index];
            index++;
            return item;
        }
    }
}
```

## 19. Anonymous Classes and Lambdas

An anonymous class is an inner class without a name, written at the point where an object is needed.

```java
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        label.setText(label.getText() + ".");
    }
});
```

Use anonymous classes when:

- you need one object implementing an interface;
- the class name would only be used once;
- the implementation is tightly tied to the surrounding code.

A lambda is shorter syntax for implementing a single-method interface.

```java
button.addActionListener(e -> label.setText(label.getText() + "."));
```

The compiler knows:

- `addActionListener` expects an `ActionListener`;
- `ActionListener` has one abstract method;
- the lambda body is the implementation of that method.

Lambda syntax:

```java
x -> x + 1
(x, y) -> x + y
() -> System.out.println("Hello")
```

Captured variables must be final or effectively final.

```java
String prefix = "Clicked: ";
button.addActionListener(e -> label.setText(prefix + e.getActionCommand()));
```

This works only if `prefix` is not reassigned after being captured.

## 20. Design Patterns

Design patterns are reusable solutions to common design problems. The exam is likely to test whether you can recognise and explain the pattern, not just recite a name.

### Strategy

Strategy delegates a responsibility to a separate object so the behaviour can be changed.

Example: layout managers.

```java
frame.setLayout(new java.awt.FlowLayout());
frame.setLayout(new java.awt.GridLayout(2, 2));
```

The frame does not implement every possible layout itself. It delegates layout to a layout manager object.

Use when:

- a class has a responsibility with multiple possible algorithms;
- you want to swap behaviour without changing the main class;
- you want each class to have fewer responsibilities.

### Observer

Observer lets one object notify other registered objects when something happens.

```java
button.addActionListener(listener);
```

In Swing:

- button: subject;
- listener: observer;
- click: event;
- `addActionListener`: registration;
- `actionPerformed`: notification method.

Use when:

- one object should react to another object's events;
- the event source should not need to know the details of the reaction.

### Iterator

Iterator provides a standard way to traverse contents.

```java
Iterator<String> it = list.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

The collection stores the data; the iterator stores the current position.

### Singleton

Singleton ensures only one instance of a class is created.

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

Key ingredients:

- private static field stores the one object;
- private constructor prevents outside `new`;
- public static method returns the shared object.

Possible exam explanation: Singleton is useful when code needs an object, not just static methods, but there should only be one instance.

### Factory

Factory moves object creation into a separate method or object.

```java
public interface Animal {
    String getName();
}

public class AnimalFactory {
    public Animal createFish() {
        return new Fish();
    }

    public Animal createBear() {
        return new Bear();
    }
}
```

Use:

```java
AnimalFactory factory = new AnimalFactory();
Animal animal = factory.createFish();
```

Why useful:

- client code uses the interface/base type;
- creation details are centralised;
- the exact concrete class can be hidden;
- creation can be counted, logged, configured, or changed later.

### Model-View Controller (MVC)
- separates a program into three parts:
    - model: stores and manages data/business logic
    - view: displays information to the user
    - controller: handles user input and coordinates between Model and View
- example:
    
    ```java
    // model - stores the actual chess board and rules
    class ChessModel {
        private String[][] board = new String[8][8];
    
        public void movePiece(int fromRow, int fromCol, int toRow, int toCol) {
            board[toRow][toCol] = board[fromRow][fromCol];
            board[fromRow][fromCol] = null;
        }
    
        public String getPiece(int row, int col) {
            return board[row][col];
        }
    }
    
    // view - displays the board
    class ChessView {
        public void displayBoard(ChessModel model) {
            for (int row = 0; row < 8; row++) {
                for (int col = 0; col < 8; col++) {
                    String piece = model.getPiece(row, col);
    
                    if (piece == null) {
                        System.out.print(". ");
                    } else {
                        System.out.print(piece + " ");
                    }
                }
                System.out.println();
            }
        }
    }
    
    // controller - handles the user action and handles model/view 
    class ChessController {
        private ChessModel model;
        private ChessView view;
    
        public ChessController(ChessModel model, ChessView view) {
            this.model = model;
            this.view = view;
        }
    
        public void makeMove(int fromRow, int fromCol, int toRow, int toCol) {
            model.movePiece(fromRow, fromCol, toRow, toCol);
            view.displayBoard(model);
        }
    }
    ```

## 21. Class Diagrams

The slides use simple class diagrams. A class box normally has three parts:

```text
ClassName
----------------
fields / data
----------------
methods
```

Relationships:

- has-a: one class contains a field referring to another class;
- is-a: one class extends or implements another;
- interface implementation: class promises to provide required methods.

Example:

```java
public class Notebook {
    private ArrayList<String> notes;
}
```

This diagram would show `Notebook` has an `ArrayList<String>`.

```java
public class Bear extends Animal {
}
```

This diagram would show `Bear` is a subclass of `Animal`.

## 22. OO Versus FP

The wrapup compares OO and functional programming.

OO:

- usually works with mutable state;
- uses objects to group data and behaviour;
- controls data changes through encapsulation;
- decomposes larger programs into interacting parts;
- supports reuse through standard classes, inheritance, and aggregation.

FP:

- usually treats data as immutable;
- emphasises expressions and functions;
- often creates new data rather than mutating old data;
- uses recursion and higher-order functions heavily;
- can rely on runtime/compiler features such as lazy evaluation.

Java can imitate some FP ideas with lambdas, but lambdas are still objects implementing interfaces.

## 23. Exam-Level Takeaways

Be able to:

- define class and object;
- write a small class with fields, constructor, getters, and setters;
- explain why fields are usually private;
- explain `static` versus instance members;
- explain `this`;
- identify has-a aggregation/composition;
- identify is-a inheritance;
- explain overriding, dynamic dispatch, and polymorphism;
- compare abstract classes and interfaces;
- read simple class diagrams;
- explain Java's memory-management advantages over C/C++;
- explain exceptions and write `try`/`catch`;
- recognise Swing components, containers, layouts, and listeners;
- explain Strategy, Observer, Iterator, Singleton, and Factory;
- use generics, wrapper classes, autoboxing, anonymous classes, and lambdas.

When answering an OO question, a strong pattern is:

1. Define the concept.
2. Give a short Java example.
3. Explain the design benefit.
4. Connect it to has-a, is-a, encapsulation, abstraction, or polymorphism.
