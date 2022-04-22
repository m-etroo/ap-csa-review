---
permalink: /units/7-arraylist
---

# Unit 7: `ArrayList`

<!-- View the [in-depth version](in-depth.md) -->

## Unit Overview

Unit 7 expands upon the array data structure covered in Unit 6 with a new, more versatile class called `ArrayList`. Many tasks which are difficult to do with arrays are simplified with `ArrayList`.

## Essential Knowledge

### Understanding and creating `ArrayList`s

#### About `ArrayList`

An `ArrayList` is an object that stores data of a specific reference type. Internally, the data is stored as an array (the specifics of which are beyond the scope of AP CSA), but the advantages of using an `ArrayList` are numerous because of the flexibility they provide when it comes to resizing the array and performing certain operations.

Unlike arrays, which you should recall are of a **fixed** size that is set upon creation, `ArrayList` objects are **resizable**. This means that the size of the `ArrayList` can be altered simply by modifying its elements, which is discussed later.

Also unlike arrays, `ArrayList` objects may **only** contain object references, not primitive values. An easy way to get around this restriction is to use the wrapper classes, e.g. `Integer` for `int`. This process is made even simpler with autoboxing.

Also note that the `ArrayList` class needs to be imported from the `java.util` package, as such:

```java
import java.util.ArrayList;
```

#### Creating an `ArrayList`

There are several legal ways to create an `ArrayList` using its constructor. First, a distinction must be made between specifying a type and not.

```java
ArrayList<String> myList = new ArrayList<String>();
ArrayList anotherList = new ArrayList();
```

In the first case, a strict type was specified for the `ArrayList` elements. When a type is specified in this manner, all elements must be of this type (or a subclass of it, as discussed in Unit 9). Often in method signatures on the Java Quick Reference, this **generic** type (it's called generic because it can be any arbitrary type) is referred to as `E`. So, in this case, `E` is `String`, but it could be `Integer`, `Dog`, or any other reference type.

In the second case, no strict type was specified. This means that the `ArrayList` can contain any reference type, i.e. any type with an eventual superclass of `Object`. The specifics of this are out of scope for the course, but you should at least know that specifying a type is preferred to ensure that only objects of the correct type are added to the `ArrayList`. If they weren't and a type were specified, the compiler would flag an error.

The angle brackets for the type in the constructor call can be omitted or left with no type inside of them. In these cases, the type, if provided, is just inferred from the variable declaration.

```java
ArrayList<String> myList = new ArrayList();
ArrayList<String> myList = new ArrayList<>();
```

### Manipulating and traversing `ArrayList`s

Once you instantiate an `ArrayList`, that's great, but you won't be able to do much with it unless you use its methods. Unlike arrays, access to `ArrayList` elements is completely method-based, i.e. you must call methods to do so.

There are six (five, really, but one is overloaded) methods that are on the Java Quick Reference and that you should be familiar with for the AP Exam:

* `int size()` – Returns the number of elements in the list
  * This is functionally equivalent to the `length` attribute of an array.

* `boolean add(E obj)` – Appends `obj` to end of list; returns `true`
  * See that `E` generic syntax that was mentioned?
  * Note that with an `ArrayList` specifically, this method always returns `true`. The details as to why this even returns a `boolean` is beyond the scope of the AP Exam, but it involves implementing the `List` interface. Other implementations actually return a `false` value if the add operation fails.

* `void add(int index, E obj)` – Inserts `obj` at position `index` (`0 <= index <= size`), moving elements at position `index` and higher to the right (adds 1 to their indices) and adds 1 to size
  * Note that this overloaded method does **not** return a `boolean` value.

* `E get(int index)` – Returns the element at position `index` in the list
  * Here, this returns a reference of the declared type of the `ArrayList`, assuming one was declared.

* `E set(int index, E obj)` – Replaces the element at position `index` with `obj`; returns the element formerly at position `index`

* `E remove(int index)` – Removes element from position `index`, moving the elements at position `index + 1` and higher to the left (subtracts 1 from their indices) and subtracts 1 from size; returns the element formerly at position `index`

Here are some examples of how you might use these. As a reminder, `ArrayList`s are zero-indexed, just like arrays. If you try to access an element at an invalid index, an `IndexOutOfBoundsException` is thrown.

```java
ArrayList<String> myList = new ArrayList<>();
myList.add("Hello");
myList.add("World");
myList.add("!");
myList.get(1); // returns "World"
myList.set(1, "Earth");
myList.get(1); // returns "Earth"
myList.remove(0); // returns "Hello"
myList.get(0); // returns "Earth"
```

You can also traverse an `ArrayList` with a `for`, `while`, or enhanced `for` loop.

```java
// an ArrayList with several String elements is declared and initialized

// prints all the elements
for (int i = 0; i < myList.size(); i++) {
    System.out.println(myList.get(i));
}
```

```java
// an ArrayList with several Integer elements is declared and initialized

// where each element is e, prints e+1
for (int e : myList) {      // unboxing occurs here to convert Integer to int
    System.out.println(e + 1);
}
```

```java
// an ArrayList with several Double elements is declared and initialized

// prints the first three elements
int i = 0;
while (i < 3) {
    System.out.println(myList.get(i));
    i++;
}
```

Note that just with an array, you shouldn't try to modify an `ArrayList` while traversing it with an enhanced `for` loop. A `ConcurrentModificationException` will be thrown if you do this.

If you're using a `for` or `while` loop, there is an additional consideration you must make. Because `ArrayList`s automatically resize, you must make sure to adjust your `ArrayList` indices properly after you add or remove an element, since you might accidentally access an element twice or skip and element.

For this example, we'll search the `ArrayList` until an `Integer` value of `14` is found. We will also remove any `7` values we come across. Notice how `i` is **only** incremented when we **don't** remove an element. If `i` were to be incremented when an element is removed, we would skip over the next element because that element shifts to the index of the removed element.

```java
// myList: ArrayList of Integers

boolean fourteenFound = false;
int i = 0;
while (!fourteenFound) {
    if (myList.get(i) == 14) {
        fourteenFound = true;
    } else if (myList.get(i) == 7) {
        myList.remove(i);
    } else {
        i++;
    }
}
```

### Searching and sorting

#### Linear search

A linear search, also called a sequential search, is a type of search algorithm that simply traverses an array or `ArrayList` in order until it finds a specific element or until the end of the data structure, whichever comes first.

For example, this implementation returns the index of the first occurrence of `target` in `list`. If `target` cannot be found, `-1` is returned.

```java
public static int linearSearch(ArrayList<Integer> list, int target) {
    for (int i = 0; i < list.size(); i++) {
        if (list.get(i) == target) {
            return i;
        }
    }
    return -1;
}
```

#### Selection sort and insertion sort

These are two iterative sorting algorithms that may be assessed on the AP Exam.

[Khan Academy has some good resources on these two algorithms](https://www.khanacademy.org/computing/computer-science/algorithms#sorting-algorithms) that you can use to familiarize yourself with them. They are a bit in-depth for here.
