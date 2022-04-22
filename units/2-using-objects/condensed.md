---
permalink: /units/2-using-objects
---

# Unit 2: Using Objects

<!-- View the [in-depth version](in-depth.md) -->

## Unit Overview

Unit 2 introduces the concept of an object, including calling methods of an object. This includes the methods of `String` objects, as well as the `Math` class methods.

## Essential Knowledge

### Classes vs. Objects

* Distinction between objects and classes
  * Classes are formal implementations of (blueprints for) objects. They can include:
    * *Methods*, which execute instructions
    * *Instance variables* (attributes), which store data related to the object
    * *Constructors*, which are special methods that *instantiate*, or create, an object from the class declaration
  * Objects are specific *instances* of a class that are *instantiated* from that class.
    * Each instance can have separate instance data from other objects of the same class. For example, a `Dog` class can define instance variables related to the dog's characteristics (like its name, breed, and color). Then, multiple instances of the `Dog` class can be created, each with different names, breeds, and colors.

### Constructors

* *Constructors* are special methods used to *instantiate* classes

* Parts of a constructor

  ```java
  Dog(String name, String breed, String color)
  ```

  * *Constructor name*: `Dog`. The same as the class name.
  * *Parameter list*: `String name, String breed, String color`. Specifies the values that can be passed into the constructor, which are *parameters*. Parameters are used by the newly-created object to set its initial state, including its instance variables.
    * For example, the `name` parameter would be used to set an instance variable for the `Dog`'s name.
  * These two elements, the *constructor name* and *parameter list*, are together referred to as the *signature*.

* Calling a constructor
  * To actually create a new object, use the `new` keyword and call the class' constructor with the appropriate parameters.

  ```java
  new Dog("Fido", "Golden Retriever", "brown");
  ```

  * Just as primitive values can be stored in variables, objects can too. The type of the variable must be declared as the class, and then an object can be assigned to the variable.

  ```java
  Dog myDog = new Dog("Fido", "Golden Retriever", "brown");
  ```

* Actual vs. formal parameters
  * *Formal parameters* are the parameters that are specified in the constructor's signature. They include a type and a useful name for the parameter.
  * *Actual parameters* are the actual values that are passed into the constructor.
  * For example, with the `Dog` example, `String name, String breed, String color` is the formal parameter list, and `"Fido"`, `"Golden Retriever"`, `"brown"` are the actual parameters.

* Overloaded constructors and parameter compatability
  * *Overloaded constructors* are a group of constructors for a class with the same constructor name but a different parameter list. For example:

  ```java
  // Overloaded constructor signatures
  Dog(String name)
  Dog(String name, String breed, String color)
  ```

  * There can't be multiple constructors with the same name and same exact order of parameter types, **even if the names are different**.

  ```java
  // Illegal because Java doesn't know which to use
  Dog(String name, String breed)
  Dog(String name, String color)
  ```

  * The actual parameters that are passed to the constructor must match up by type to the formal parameter list of one of the constructors.

  ```java
  // Constructors
  Dog(String name)
  Dog(String name, String breed, String color)
  Dog(int age, String name)
  ```

  ```java
  new Dog("Fido"); // ok
  new Dog("Fido", "Golden Retriever", "brown"); // ok
  new Dog("Fido", "Golden Retriever"); // not ok
                                       // no matching constructor
  new Dog(10, "Fido"); // ok
  ```

* "Call by value"
  * In Java, actual parameters that are passed into a constructor are copied. Then, these copies are received by the constructor and used to create the new object.
  * This means that the variable passed into the constructor can safely be modified afterwards **without** changing the instance data of the object that is created.

* Constructors can be used to instantiate any class, including classes written by others.
  * For example, the `String` class can be instantiated with its constructor.
  * Classes can also be imported and then instantiated. This is discussed within [Unit 7](../7-arraylist/condensed.md).

### Object Methods

* Objects have *methods*, which are groups of code that are used to perform a specific task. The set of methods available to an object is called its *behavior*.

* Method signatures are similar to constructor signatures. They include the method's name and the method's parameter list. However, method signatures also have a *return type*, which specifies the type of the value that the method returns.
  * The `void` return type means that the object returns no value.

```java
// Example method signatures for Dog
void birthday()
void bark()
String getName()            // return type of String
int getAge()                // return type of int
void setName(String name)
```

### About `null`

* In Java, `null` is a special keyword that represents an empty object reference, i.e. an object reference that does not point to any actual object.

* A variable declared with its type as the name of a class is said to have a *reference type*.
  
  ```java
  Dog myDog;    // myDog's type is a reference type
                // as opposed to a primitive type
  ```

* A variable of a reference type has two possibilities as to what it can hold:
  * A *reference* to, or a *pointer* to, an actual object in memory. This reference is a computer memory address that "points" to where the object is actually stored in memory. So, when this variable is accessed, the computer goes to the specified memory address stored in the variable and finds the object.
  * A `null` value, indicating that the variable does not currently point towards any object.

* Trying to call any method or access any instance variable of a variable storing a `null` value will result in a `NullPointerException` at runtime, since the `null` value is not an object and has no methods or instance data.
  
  ```java
  Dog aDog = null;  // this dog hasn't been created yet

  aDog.getName();   // throws a NullPointerException since
                    // there is no dog to get a name for
  ```

### Miscellaneous

* *Abstraction*, or *procedural abstraction*, refers to the concept that programmers can use a method just by knowing what it does, even if they don't know *how* it is done.
  * If you press the stop button on a microwave, you know that the microwave stops cooking the food inside of it, but you probably don't know *how* exactly the "stop" signal is sent and how it is processed by the microwave. This same idea can be applied to programming.
