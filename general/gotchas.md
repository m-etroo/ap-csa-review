# Conceptual "Gotchas"

This section documents some concepts or methods that can be easily misunderstood **or** forgotten. It is organized by unit for clarity.

## Unit 1: Primitive Types

* The `final` keyword is used to declare a variable whose value cannot be changed **after it is initialized**.
  * Key words: *after it is initialized*

  * ```java
    final int x;
    x = 5;
    ```

    This is legal because the first line only *declares* `x`, not *initializes* it. The second line then initializes it. After that, the value of `x` cannot be changed – that would be illegal and cause the compiler to flag an error.

* Integer math vs. floating-point (double) math: 
  * Performing a mathematical operation on two integers will always result in an **integer**. If the result is not an integer, it is truncated to make it one. (*Truncation* simply means that the decimal portion of the result is removed, i.e. the number is rounded down).
    * For example, `5 / 3` is equal to `1`, since 1.67 is truncated.
  * Performing a mathematical operation that involves any double value will always result in a **double**. This means that even if the result is an integer, like in the case of `5 + 3`, which is 8, Java will report the result as `8.0`.

* Keep in mind that `8` and `8.0` are not the same thing. The former is an integer value, and the latter is a double value (since it has a decimal point). This may seem like a minor detail, but it is important because, for example, a method that accepts an `int` parameter will cause an error if `8.0` is passed to it. (This problem would be corrected with casting.)

* Dividing by zero results in an `ArithmeticException`, which is a runtime exception, not a compile error.

* Don't use the increment (`++`) and decrement (`--`) operators inside of other expressions – for example, an array index: `arr[i++]`. This is out of scope for the AP Exam.

## Unit 2: Using Objects

* There cannot be overloaded constructors with the same name and same order of parameter types, **even if the parameter names are different**. For example, these two constructor signatures (together) are illegal because Java doesn't know which of the constructors to use:

  ```java
  Dog(String name, String breed)
  Dog(String name, String color)
  ```

* *Abstraction*, or *procedural abstraction*, refers to the concept that programmers can use a method just by knowing what it does, even if they don't know *how* it is done.
  * If you press the stop button on a microwave, you know that the microwave stops cooking the food inside of it, but you probably don't know *how* exactly the "stop" signal is sent and how it is processed by the microwave. This same idea can be applied to programming.

* Constructors have no return type, so their signature just consists of the name of the class and the parameter list. However, methods **do** have a return type, so in addition to the method name and parameter list, the signature also includes the return type.

## Unit 4: Iteration

* `while` and `for` loops do **not** have to execute at all! If the Boolean expression evaluates to `false` the first time it is evaluated, the loop will not execute at all.

## Unit 5: Writing Classes

* The `private` keyword only restricts access to the **class**, not the specific **object**. This means that an object can still access the private methods and instance variables of another object **of the same class** without any issue.

  ```java
  public class Cat {
    // Other constructors, methods, and instance variables not shown
    private int age;

    public isOlderThanOtherCat(Cat otherCat) {
        return this.age > otherCat.age; // legal because otherCat is an
                                        // object of the same class
    }
  }
  ```

* A default no-argument constructor is **only** provided when no constructors are written. **If you write a constructor with parameters, Java will not automatically provide a no-argument constructor.**

* When a method returns an object reference, the **reference** is copied, **not** the object. This means that
