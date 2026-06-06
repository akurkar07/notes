# Java Relearning Exercises

Use these to rebuild Java and OO fluency. Try each task in a small Java file and compile/run it.

## 1. Syntax Warm-Up

Write a class called `HelloWorld` with a `main` method that prints three lines:

```text
Hello Java
Classes contain code
main is static
```

Then modify it to print command-line arguments.

```java
public static void main(String[] args) {
    // print each argument with its index
}
```

### Answer

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello Java");
        System.out.println("Classes contain code");
        System.out.println("main is static");

        for (int i = 0; i < args.length; i++) {
            System.out.println(i + ": " + args[i]);
        }
    }
}
```

`main` is `static` because the program starts before Java has created any object of the class.

## 2. Static Methods

Create a class `TextTools` with static methods:

```java
printMessage(String message)
repeat(String text, int n)
isLongerThan(String text, int limit)
```

Example behaviour:

```java
TextTools.repeat("ha", 3) // "hahaha"
TextTools.isLongerThan("hello", 3) // true
```

### Answer

```java
public class TextTools {
    public static void printMessage(String message) {
        System.out.println(message);
    }

    public static String repeat(String text, int n) {
        String result = "";
        for (int i = 0; i < n; i++) {
            result = result + text;
        }
        return result;
    }

    public static boolean isLongerThan(String text, int limit) {
        return text.length() > limit;
    }

    public static void main(String[] args) {
        printMessage("Hello");
        System.out.println(repeat("ha", 3));
        System.out.println(isLongerThan("hello", 3));
    }
}
```

These methods are static because they are utility operations called on the class, not on a particular `TextTools` object.

## 3. Basic Classes

Create a `Person` class with:

- private `name`;
- private `age`;
- constructor;
- getters;
- setter for age;
- method `describe()`.

Example:

```java
Person p = new Person("Alex", 19);
System.out.println(p.describe());
```

### Answer

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

    public String describe() {
        return name + " is " + age + " years old";
    }

    public static void main(String[] args) {
        Person p = new Person("Alex", 19);
        System.out.println(p.describe());
    }
}
```

The fields are private so outside code cannot directly put the object into a bad state. Access goes through public methods.

## 4. Constructors and `this`

Create a `Counter` class:

- private `value`;
- constructor taking initial value;
- `increment()`;
- `add(int n)`;
- `getValue()`.

Use `this.value` inside the constructor.

### Answer

```java
public class Counter {
    private int value;

    public Counter(int value) {
        this.value = value;
    }

    public void increment() {
        value++;
    }

    public void add(int n) {
        value = value + n;
    }

    public int getValue() {
        return value;
    }

    public static void main(String[] args) {
        Counter c = new Counter(10);
        c.increment();
        c.add(5);
        System.out.println(c.getValue());
    }
}
```

`this.value = value;` means the field in the current object gets the value from the constructor parameter.

## 5. Static Data

Modify `Counter` so it also tracks how many `Counter` objects have been created.

```java
Counter a = new Counter(0);
Counter b = new Counter(10);
System.out.println(Counter.getCount()); // 2
```

### Answer

```java
public class Counter {
    private int value;
    private static int count = 0;

    public Counter(int value) {
        this.value = value;
        count++;
    }

    public void increment() {
        value++;
    }

    public void add(int n) {
        value = value + n;
    }

    public int getValue() {
        return value;
    }

    public static int getCount() {
        return count;
    }

    public static void main(String[] args) {
        Counter a = new Counter(0);
        Counter b = new Counter(10);
        System.out.println(Counter.getCount());
    }
}
```

`value` is instance data because every counter has its own value. `count` is static data because there is one shared count for the whole class.

## 6. Aggregation

Create a `Notebook` class that has an `ArrayList<String>` inside it.

Methods:

```java
addNote(String note)
getNoteCount()
getNote(int index)
printAll()
```

The point: `Notebook` hides the `ArrayList` and exposes notebook-specific behaviour.

### Answer

```java
import java.util.ArrayList;

public class Notebook {
    private ArrayList<String> notes;

    public Notebook() {
        notes = new ArrayList<>();
    }

    public void addNote(String note) {
        notes.add(note);
    }

    public int getNoteCount() {
        return notes.size();
    }

    public String getNote(int index) {
        return notes.get(index);
    }

    public void printAll() {
        for (String note : notes) {
            System.out.println(note);
        }
    }

    public static void main(String[] args) {
        Notebook notebook = new Notebook();
        notebook.addNote("Revise classes");
        notebook.addNote("Revise inheritance");
        notebook.printAll();
    }
}
```

This is aggregation/composition because a `Notebook` has an `ArrayList<String>`. Outside code uses notebook methods instead of depending directly on the internal list.

## 7. Inheritance

Create:

```java
class Animal
class Bear extends Animal
class Fish extends Animal
```

Each animal should have:

```java
getName()
getNoise()
```

Then store them in an `Animal[]` and loop through them.

```java
Animal[] animals = { new Animal(), new Bear(), new Fish() };
for (Animal a : animals) {
    System.out.println(a.getName() + ": " + a.getNoise());
}
```

### Answer

```java
public class Animal {
    public String getName() {
        return "Animal";
    }

    public String getNoise() {
        return "Unknown";
    }
}
```

```java
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

```java
public class Fish extends Animal {
    @Override
    public String getName() {
        return "Fish";
    }

    @Override
    public String getNoise() {
        return "Blub";
    }
}
```

```java
public class AnimalTest {
    public static void main(String[] args) {
        Animal[] animals = { new Animal(), new Bear(), new Fish() };

        for (Animal a : animals) {
            System.out.println(a.getName() + ": " + a.getNoise());
        }
    }
}
```

The array type is `Animal[]`, but the actual objects can be `Animal`, `Bear`, or `Fish`. Java chooses the overridden method using the runtime object.

## 8. Interfaces

Replace the `Animal` superclass with an `Animal` interface.

```java
public interface Animal {
    String getName();
    String getNoise();
}
```

Make `Bear` and `Fish` implement it. Check that the loop still works.

### Answer

```java
public interface Animal {
    String getName();
    String getNoise();
}
```

```java
public class Bear implements Animal {
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

```java
public class Fish implements Animal {
    @Override
    public String getName() {
        return "Fish";
    }

    @Override
    public String getNoise() {
        return "Blub";
    }
}
```

```java
public class AnimalTest {
    public static void main(String[] args) {
        Animal[] animals = { new Bear(), new Fish() };

        for (Animal a : animals) {
            System.out.println(a.getName() + ": " + a.getNoise());
        }
    }
}
```

The loop still works because both classes promise to provide the methods required by the `Animal` interface.

## 9. Exceptions

Write a method:

```java
public static int safeDivide(int a, int b) throws ArithmeticException
```

If `b` is zero, throw an exception. Then call it inside a `try`/`catch`.

### Answer

```java
public class DivideDemo {
    public static int safeDivide(int a, int b) throws ArithmeticException {
        if (b == 0) {
            throw new ArithmeticException("division by zero");
        }
        return a / b;
    }

    public static void main(String[] args) {
        try {
            System.out.println(safeDivide(10, 0));
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero");
        }
    }
}
```

Throwing an exception means leaving the normal return path and reporting an exceptional situation to code that can handle it.

## 10. Collections

Create an `ArrayList<String>` of names.

Do the following:

- add five names;
- print them with a for-each loop;
- sort them using `Collections.sort`;
- reverse them using `Collections.reverse`;
- print again.

### Answer

```java
import java.util.ArrayList;
import java.util.Collections;

public class NamesDemo {
    public static void main(String[] args) {
        ArrayList<String> names = new ArrayList<>();
        names.add("Alex");
        names.add("Sam");
        names.add("Priya");
        names.add("Mina");
        names.add("Jordan");

        for (String name : names) {
            System.out.println(name);
        }

        Collections.sort(names);
        Collections.reverse(names);

        for (String name : names) {
            System.out.println(name);
        }
    }
}
```

`ArrayList<String>` is generic: it stores `String` objects and gives type checking at compile time.

## 11. Generics

Create a generic `Box<T>` class.

```java
public class Box<T> {
    private T value;
}
```

Add:

```java
Box(T value)
T get()
void set(T value)
```

Test with `Box<String>` and `Box<Integer>`.

### Answer

```java
public class Box<T> {
    private T value;

    public Box(T value) {
        this.value = value;
    }

    public T get() {
        return value;
    }

    public void set(T value) {
        this.value = value;
    }

    public static void main(String[] args) {
        Box<String> words = new Box<>("hello");
        Box<Integer> number = new Box<>(42);

        System.out.println(words.get());
        System.out.println(number.get());
    }
}
```

Generics are parametric polymorphism: the same class is written once, then used with different object types.

## 12. Iterators

Create a class `SimpleBag<T>` that stores items in an `ArrayList<T>` and implements `Iterable<T>`.

Minimum methods:

```java
add(T item)
iterator()
```

Then make this work:

```java
SimpleBag<String> bag = new SimpleBag<>();
bag.add("A");
bag.add("B");

for (String item : bag) {
    System.out.println(item);
}
```

### Answer

```java
import java.util.ArrayList;
import java.util.Iterator;

public class SimpleBag<T> implements Iterable<T> {
    private ArrayList<T> items;

    public SimpleBag() {
        items = new ArrayList<>();
    }

    public void add(T item) {
        items.add(item);
    }

    @Override
    public Iterator<T> iterator() {
        return items.iterator();
    }

    public static void main(String[] args) {
        SimpleBag<String> bag = new SimpleBag<>();
        bag.add("A");
        bag.add("B");

        for (String item : bag) {
            System.out.println(item);
        }
    }
}
```

`Iterable<T>` means the object can produce an iterator. The for-each loop works by calling `iterator()`.

## 13. Anonymous Classes

Write a tiny Swing program with a `JButton` and `JLabel`. Use an anonymous `ActionListener` so clicking the button changes the label.

Core idea:

```java
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        label.setText("Clicked");
    }
});
```

### Answer

```java
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;

public class AnonymousButtonDemo {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Demo");
        frame.setLayout(new FlowLayout());

        JLabel label = new JLabel("Waiting");
        JButton button = new JButton("Click");

        button.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                label.setText("Clicked");
            }
        });

        frame.add(label);
        frame.add(button);
        frame.pack();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
```

The anonymous class creates one object that implements `ActionListener`. This is useful when the listener is only needed in one place.

## 14. Lambdas

Rewrite the previous exercise using a lambda.

```java
button.addActionListener(e -> label.setText("Clicked"));
```

### Answer

```java
import java.awt.FlowLayout;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;

public class LambdaButtonDemo {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Demo");
        frame.setLayout(new FlowLayout());

        JLabel label = new JLabel("Waiting");
        JButton button = new JButton("Click");

        button.addActionListener(e -> label.setText("Clicked"));

        frame.add(label);
        frame.add(button);
        frame.pack();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
```

A lambda works here because `ActionListener` has one abstract method, `actionPerformed`.

## 15. Singleton

Implement this singleton:

```java
public class AppConfig {
    private static AppConfig oneObject = null;

    private AppConfig() { }

    public static AppConfig get() {
        // return the one shared object
    }
}
```

Add a field such as `themeName` and prove that two calls to `AppConfig.get()` return the same shared object.

### Answer

```java
public class AppConfig {
    private static AppConfig oneObject = null;
    private String themeName;

    private AppConfig() {
        themeName = "Light";
    }

    public static AppConfig get() {
        if (oneObject == null) {
            oneObject = new AppConfig();
        }
        return oneObject;
    }

    public String getThemeName() {
        return themeName;
    }

    public void setThemeName(String themeName) {
        this.themeName = themeName;
    }

    public static void main(String[] args) {
        AppConfig a = AppConfig.get();
        AppConfig b = AppConfig.get();

        a.setThemeName("Dark");
        System.out.println(b.getThemeName());
        System.out.println(a == b);
    }
}
```

The constructor is private, so outside code cannot call `new AppConfig()`. The static `get()` method controls the single shared object.

## 16. Factory

Create an `AnimalFactory`.

```java
public class AnimalFactory {
    public Animal createBear() {
        return new Bear();
    }

    public Animal createFish() {
        return new Fish();
    }
}
```

Use the factory from `main` without directly calling `new Bear()` or `new Fish()` there.

### Answer

```java
public interface Animal {
    String getName();
    String getNoise();
}
```

```java
public class Bear implements Animal {
    public String getName() {
        return "Bear";
    }

    public String getNoise() {
        return "Growl";
    }
}
```

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

```java
public class AnimalFactory {
    public Animal createBear() {
        return new Bear();
    }

    public Animal createFish() {
        return new Fish();
    }
}
```

```java
public class FactoryDemo {
    public static void main(String[] args) {
        AnimalFactory factory = new AnimalFactory();

        Animal a = factory.createBear();
        Animal b = factory.createFish();

        System.out.println(a.getName() + ": " + a.getNoise());
        System.out.println(b.getName() + ": " + b.getNoise());
    }
}
```

Factory keeps creation details out of client code. `main` works with the `Animal` interface instead of directly choosing concrete classes.

## 17. Mini Exam-Style Questions

1. Explain the difference between a class and an object, using a Java example.

   **Answer:** A class is the blueprint or type definition. An object is an instance made from that class with `new`.

   ```java
   public class Person {
       private String name;

       public Person(String name) {
           this.name = name;
       }
   }

   Person p = new Person("Alex");
   ```

   `Person` is the class. `p` refers to one `Person` object.

2. Explain the difference between `static` and instance methods.

   **Answer:** A static method belongs to the class and is called without an object. An instance method belongs to an object and can use that object's fields through `this`.

   ```java
   Counter.getCount(); // static
   c.increment();      // instance
   ```

   A static method cannot directly use instance fields because there is no current object.

3. Write a class that demonstrates encapsulation using private fields and public methods.

   **Answer:**

   ```java
   public class BankAccount {
       private int balance;

       public BankAccount(int balance) {
           this.balance = balance;
       }

       public void deposit(int amount) {
           if (amount > 0) {
               balance = balance + amount;
           }
       }

       public int getBalance() {
           return balance;
       }
   }
   ```

   The private field is hidden, and outside code must use public methods.

4. Explain the difference between aggregation and inheritance.

   **Answer:** Aggregation/composition is a has-a relationship; inheritance is an is-a relationship.

   ```java
   class Notebook {
       private ArrayList<String> notes; // has-a
   }

   class Bear extends Animal {          // is-a
   }
   ```

   Use fields when one object contains or uses another object. Use inheritance only when the subclass is genuinely a specialised type of the superclass.

5. Given a superclass reference pointing to a subclass object, explain which overridden method runs and why.

   **Answer:** The subclass method runs because Java uses dynamic dispatch for overridden instance methods.

   ```java
   Animal a = new Bear();
   System.out.println(a.getNoise()); // Bear's getNoise()
   ```

   The declared reference type is `Animal`, but the actual runtime object is `Bear`.

6. Compare abstract classes and interfaces.

   **Answer:** An abstract class can contain fields, constructors, implemented methods, and abstract methods. A class extends an abstract class. An interface mainly specifies behaviour that implementing classes must provide. A class implements an interface.

   ```java
   abstract class Animal {
       public abstract String getNoise();
       public void sleep() {
           System.out.println("Sleeping");
       }
   }

   interface Drawable {
       void draw();
   }
   ```

   Use an abstract class for a shared is-a hierarchy with common code. Use an interface when different classes should promise the same behaviour.

7. Explain why Java uses wrapper classes such as `Integer` with generics.

   **Answer:** Java generics work with object types, not primitive types. `int` is primitive, so `ArrayList<int>` is invalid. Use `Integer` instead.

   ```java
   ArrayList<Integer> nums = new ArrayList<>();
   nums.add(3);        // autoboxing int to Integer
   int x = nums.get(0); // unboxing Integer to int
   ```

8. Explain how `ActionListener` demonstrates the Observer pattern.

   **Answer:** The button is the subject/event source. The `ActionListener` is the observer. The listener is registered with `addActionListener`, and when the button is clicked Java calls `actionPerformed`.

   ```java
   button.addActionListener(e -> label.setText("Clicked"));
   ```

   The button does not need to know exactly what the listener will do.

9. Explain how `LayoutManager` demonstrates the Strategy pattern.

   **Answer:** A layout manager is a separate object that controls how components are arranged. Changing the layout object changes the algorithm without changing the frame or panel class.

   ```java
   frame.setLayout(new FlowLayout());
   frame.setLayout(new GridLayout(2, 2));
   ```

10. Explain when you would use a Factory instead of directly calling `new`.

   **Answer:** Use a Factory when you want creation decisions centralised or hidden from client code. The client asks for an interface/base type and does not need to know the exact concrete class.

   ```java
   AnimalFactory factory = new AnimalFactory();
   Animal animal = factory.createFish();
   ```

   This makes the client code depend on `Animal`, not directly on `Fish`.

## 18. Suggested Practice Loop

1. Write the smallest version that compiles.
2. Add fields and constructors.
3. Add methods one at a time.
4. Test from `main`.
5. Refactor fields to `private`.
6. Replace direct access with methods.
7. Look for whether the relationship is "has-a" or "is-a".
