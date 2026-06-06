# Java Exam Code Snippets to Memorise

These are the small Java shapes worth being able to write from memory.

## Minimal Program

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

## Command-Line Arguments

```java
for (int i = 0; i < args.length; i++) {
    System.out.println(i + ": " + args[i]);
}
```

## Static Utility Method

```java
public static boolean isLongerThan(String text, int limit) {
    return text.length() > limit;
}
```

## Basic Encapsulated Class

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

## Static Field Shared by All Objects

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

    public static int getCount() {
        return count;
    }
}
```

## Aggregation / Has-A

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

## Inheritance / Is-A

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

## Dynamic Dispatch

```java
Animal a = new Bear();
System.out.println(a.getNoise()); // Growl
```

## Interface

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

## Abstract Class

```java
public abstract class Animal {
    public abstract String getNoise();

    public void sleep() {
        System.out.println("Sleeping");
    }
}
```

## Exception and Try/Catch

```java
public static int divide(int x, int y) {
    if (y == 0) {
        throw new ArithmeticException("division by zero");
    }
    return x / y;
}

try {
    System.out.println(divide(10, 0));
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
```

## ArrayList and Collections

```java
import java.util.ArrayList;
import java.util.Collections;

ArrayList<String> names = new ArrayList<>();
names.add("Alex");
names.add("Sam");

Collections.sort(names);
Collections.reverse(names);

for (String name : names) {
    System.out.println(name);
}
```

## Generic Class

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
}
```

Use:

```java
Box<String> words = new Box<>("hello");
Box<Integer> number = new Box<>(42);
```

## Wrapper Classes and Autoboxing

```java
ArrayList<Integer> nums = new ArrayList<>();
nums.add(3);         // int becomes Integer
int x = nums.get(0); // Integer becomes int
```

## Iterator

```java
import java.util.Iterator;

Iterator<String> it = names.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

## Custom Iterable

```java
import java.util.ArrayList;
import java.util.Iterator;

public class SimpleBag<T> implements Iterable<T> {
    private ArrayList<T> items = new ArrayList<>();

    public void add(T item) {
        items.add(item);
    }

    @Override
    public Iterator<T> iterator() {
        return items.iterator();
    }
}
```

## Swing Frame

```java
import javax.swing.JFrame;
import javax.swing.JLabel;

public class GuiDemo {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Demo");
        frame.add(new JLabel("Hello"));
        frame.pack();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
```

## Anonymous ActionListener

```java
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        label.setText("Clicked");
    }
});
```

## Lambda Listener

```java
button.addActionListener(e -> label.setText("Clicked"));
```

## Strategy Pattern: LayoutManager

```java
frame.setLayout(new java.awt.FlowLayout());
frame.setLayout(new java.awt.GridLayout(2, 2));
```

## Observer Pattern: ActionListener

```java
button.addActionListener(e -> label.setText("Clicked"));
```

Button = subject/event source. Listener = observer. Click = event. `actionPerformed` = notification.

## Singleton

```java
public class Singleton {
    private static Singleton oneObject = null;

    private Singleton() {
    }

    public static Singleton get() {
        if (oneObject == null) {
            oneObject = new Singleton();
        }
        return oneObject;
    }
}
```

## Factory

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

Use:

```java
AnimalFactory factory = new AnimalFactory();
Animal animal = factory.createFish();
```

## Exam Phrases

- A class is a blueprint; an object is an instance.
- Encapsulation combines data with the methods that operate on it.
- Data hiding means fields are private and access is through public methods.
- Static belongs to the class; instance belongs to an object.
- `this` means the current object.
- Aggregation/composition is has-a.
- Inheritance is is-a.
- Polymorphism means the same call can run different implementations depending on the actual object.
- Dynamic dispatch means overridden instance methods are chosen at runtime.
- Generics are parametric polymorphism.
- Interfaces specify behaviour that implementing classes must provide.
- A lambda is short syntax for a single-method interface.
