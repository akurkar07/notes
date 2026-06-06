# Java Demo Assessment - 4 Questions

Sources:

- `C:\Users\Alex\Downloads\ExamSys_ Assessment_2.htm` - Q1
- `C:\Users\Alex\Downloads\ExamSys_ Assessment_3.htm` - Q2
- Q3 from your Iterator-pattern practice question
- `C:\Users\Alex\Downloads\ExamSys_ Assessment.htm` - Q4

## Q1. True/False and Quick Checks

### True/False

State whether each statement is true or false.

1. C is an object oriented language because it supports structs.
2. Java is an object oriented language because it prevents you having global functions. Instead all functions must be associated with a class.
3. Encapsulation is the idea that your data is hidden inside objects, preventing it being accessed.
4. The singleton pattern allows you to ensure that there is only one class that does any specific thing in your program.
5. The factory pattern involves objects creating other objects.
6. Generics in Java are implemented using parametric polymorphism and are the Java implementation of subtype polymorphism.
7. The observer pattern is a good way to let other objects know about changes that happen, but they have to tell the object that they want to observe that they want to be notified, or they won't be told.
8. The Java implementation of the iterator pattern involved a change to the language rather than just adding some interfaces and classes. Because of this, you need to use specific interfaces, `Iterator` and `Iterable`.
9. The strategy pattern is only useful where there is only one set of responsibilities, as it has to be clear which responsibilities will go to the strategy.
10. The MVC pattern, Most Valued Controller, is all about ensuring that the controller is the "most valued", and hence makes all decisions.

### Quick Multiple Choice Checks

Generics in Java: which statements are entirely correct?

- Generics in Java are implemented using parametric polymorphism.
- Generics are the Java implementation of subtype polymorphism.
- When you create a generic object you should also specify an additional class at the same time.

MVC: which statements are entirely correct?

- The MVC pattern stands for "Most Valued Controller".
- MVC involves ensuring that some part, called the controller, is "most valued" in terms of decision making.
- The controller must make all decisions related to enforcing program restrictions and side effects.

Factory pattern: which statements are entirely correct?

- The factory pattern is a design pattern.
- You can implement the factory pattern in Java.
- It always involves objects creating other objects.

### Answer Guidance

1. False. C structs group data, but C does not directly support the full OO style: methods in classes, inheritance, polymorphism, encapsulation as a language design, etc.
2. Mostly true. Java supports OO partly by requiring methods to be inside classes, although this alone is not the whole definition of OO.
3. Partly true but imprecise. Encapsulation groups data and methods together; data hiding is the related idea of restricting direct access to fields.
4. False. Singleton ensures only one object/instance of a class, not only one class doing a thing.
5. True. Factory is about centralising/wrapping object creation.
6. False. Generics are parametric polymorphism, not subtype polymorphism.
7. True. Observers/listeners register with the subject if they want notification.
8. False. Java supports the Iterator pattern with interfaces/classes and for-each syntax support; the pattern itself is not a special new language feature in the sense implied here.
9. False. Strategy is useful when you want to delegate a responsibility to interchangeable strategy objects. A class may delegate multiple responsibilities using multiple strategy interfaces.
10. False. MVC means Model-View-Controller.

Generics quick check:

- Correct: generics use parametric polymorphism.
- Incorrect: generics are not subtype polymorphism.
- Mostly correct in ordinary use: when creating a generic object, you specify a type argument such as `ArrayList<String>`.

MVC quick check:

- The first two are false.
- The third is too strong/misleading. The controller handles input/control flow, but the model should enforce core program state and rules.

Factory quick check:

- All three are broadly correct for the simple factory examples in the slides.

## Q2. Fill In The Blanks

Fill in the missing words.

Object oriented languages have various common features:

To be object oriented, languages really need to support ______ and objects. These group data items together with ______ that act upon them. This grouping together is called ______. Data ______ is a related feature which aims to avoid the attributes being visible outside of the class.

Most object oriented languages will support ______ polymorphism, often called ______ because classes inherit functionality and data from other classes. In Java there are two different keywords used for this: ______ is used where a class is inheriting from an interface, and ______ is used where a class is inheriting from another class, or an interface is inheriting from another interface.

Another type of polymorphism supported by Java is ______ polymorphism, which is where a class has two or more methods with the same name but different ______ types.

A third type of polymorphism supported in Java is ______ polymorphism, where one class is parameterised on another type. In Java this is limited so that the parameterised type must be a ______, not a basic data type. Java provides a workaround for this using auto-______, where a basic data type will automatically be wrapped to make an object when it is clear to the compiler that an object is needed. A specific class is provided in the language for each of the basic data types to wrap data of that type.

### Answer Guidance

```text
classes
methods
encapsulation
hiding
subtype
inheritance
implements
extends
overloading
parameter
parametric
class
boxing
```

Expanded explanation:

- OO languages need classes and objects.
- Classes group data with methods.
- Encapsulation is the grouping of data and behaviour.
- Data hiding prevents direct external access to fields.
- Subtype polymorphism is linked to inheritance.
- Java uses `implements` for interfaces and `extends` for classes.
- Overloading means same method name, different parameter types.
- Parametric polymorphism means using a type parameter, as in generics.
- Java generic type parameters must be classes/reference types, not primitive types.
- Autoboxing wraps primitives such as `int` into wrapper objects such as `Integer`.

Alternative multiple-choice answers from the ExamSys screen:

- A third type of polymorphism supported in Java is **parametric** polymorphism.
- This is where **one class is parameterised on another class**.
- The parameterised type must be **a class**, not **a basic data type**.
- Java works around this using **auto-boxing**.
- Another problem is **type erasure**.
- Type erasure means it is not possible to **create objects or arrays of objects of the parameterised type**.

## Q3. Iterator Pattern Explanation

Question:

Explain what the Iterator pattern is used for and how it is usually implemented.

### Strong Answer

The Iterator pattern is used to traverse the contents of a collection without exposing how that collection is stored internally. The collection stores the actual data, while an iterator object keeps track of the current position during traversal.

In Java this is usually implemented by making the collection implement `Iterable<T>`, which requires an `iterator()` method. This method returns an `Iterator<T>` object. The iterator provides methods such as `hasNext()`, to check whether there are more elements, and `next()`, to return the next element and move the iterator forward.

This gives a standard way to access elements in different kinds of collections, such as `ArrayList` or `LinkedList`, without needing to know their internal implementation.

```java
Iterator<Item> it = items.iterator();

while (it.hasNext()) {
    Item item = it.next();
    System.out.println(item);
}
```

Key terms to include:

- collection/container;
- traversal;
- hides internal representation;
- `Iterable<T>`;
- `Iterator<T>`;
- `iterator()`;
- `hasNext()`;
- `next()`.

## Q4. Inventory Iterator Code

Question:

Assume that you have a class called `Inventory`, which contains a set of `Item` objects representing the items you have available. Assume that each `Item` supports `toString()`, so it can be converted easily to a `String` showing the name of the item.

Assume that internally `Inventory` stores the `Item` objects in an `ArrayList` called `data`.

Assume that you want to be able to use the Iterator design pattern to output a list of all of the items in your inventory.

Explain how you would do this in Java, providing Java code and simple explanations for:

- any changes you would make to `Inventory`;
- any new classes you would add and their implementation;
- the code which will actually output the text if you have an object reference named `inv` to the `Inventory` object.

### Strong Answer: Use `Iterable<Item>`

The clean Java answer is to make `Inventory` implement `Iterable<Item>`. This means an `Inventory` object promises that it can provide an `Iterator<Item>`.

```java
import java.util.ArrayList;
import java.util.Iterator;

public class Inventory implements Iterable<Item> {
    private ArrayList<Item> data = new ArrayList<>();

    public void add(Item item) {
        data.add(item);
    }

    @Override
    public Iterator<Item> iterator() {
        return data.iterator();
    }
}
```

Because `ArrayList` already supports iteration, the simplest implementation is to return `data.iterator()`.

Then output all items like this:

```java
Iterator<Item> it = inv.iterator();

while (it.hasNext()) {
    Item item = it.next();
    System.out.println(item.toString());
}
```

Because `Inventory` implements `Iterable<Item>`, a for-each loop is also possible:

```java
for (Item item : inv) {
    System.out.println(item);
}
```

### Alternative: Custom Inner Iterator

If the question expects a manual implementation, add an inner class implementing `Iterator<Item>`.

```java
import java.util.ArrayList;
import java.util.Iterator;

public class Inventory implements Iterable<Item> {
    private ArrayList<Item> data = new ArrayList<>();

    public void add(Item item) {
        data.add(item);
    }

    @Override
    public Iterator<Item> iterator() {
        return new InventoryIterator();
    }

    private class InventoryIterator implements Iterator<Item> {
        private int index = 0;

        @Override
        public boolean hasNext() {
            return index < data.size();
        }

        @Override
        public Item next() {
            Item item = data.get(index);
            index++;
            return item;
        }
    }
}
```

Use it:

```java
Iterator<Item> it = inv.iterator();

while (it.hasNext()) {
    System.out.println(it.next().toString());
}
```

### What Q4 Tests

This question combines:

- `ArrayList<Item>` as internal storage;
- encapsulation: `Inventory` hides `data`;
- `Iterable<Item>` on the container;
- `Iterator<Item>` for traversal;
- generics;
- the Iterator design pattern;
- calling `toString()` for output.

