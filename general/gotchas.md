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

* Object references can be `null`! Make sure to use short circuiting or take other appropriate steps to prevent a `NullPointerException` in cases where you call a method or access an instance variable of a reference that could be `null`.

* Make sure to familiarize yourself with the `Math` class methods on the Java Quick Reference to ensure you aren't tripped up. All of these methods, except for `static int abs(int x)`, return doubles, even if you pass integers as parameters (which are implicitly casted to doubles). Also, note that all `Math` methods are static.

## Unit 3: Boolean Expressions and `if` Statements

* Make sure to be able to distinguish between a series of `if` statements and the use of `else if` statements. For example:

  ```java
  int x = 5;

  if (x <= 5) {
    System.out.println("<= 5"); // this executes
  } else if (x <= 6) {
    System.out.println("<= 6"); // this does NOT execute
  } else {
    System.out.println("> 6");  // this does not execute
  }
  ```

  ```java
  int x = 5;

  if (x <= 5) {
    System.out.println("<= 5"); // this executes
  }
  if (x <= 6) {
    System.out.println("<= 6"); // this ALSO executes
  }
  ```

* The operator precedence for the logical operators: `!`, then `&&`, then `||`. You can artificially "alter" this precedence by using parentheses.

* Short-circuited evaluation allows the evaluation of a compound Boolean expression to terminate early if one sub-expression determines the result of the entire expression.

* Make sure to brush up on De Morgan's logic laws and truth tables! They may come in handy when you need to evaluate complex expressions.

* *Aliases* are object references that point to the exact same object. This indicates *equality*, which can be tested with the relational equality operators, and is distinct from *equivalency*, which can be tested with the `equals` method.

## Unit 4: Iteration

* `while` and `for` loops do **not** have to execute at all! If the Boolean expression evaluates to `false` the first time it is evaluated, the loop will not execute at all. Similarly, loops can execute infinitely if the Boolean expression is always `true`.

* When you declare a variable with a `for` loop, you can use the variable in the loop body, but not outside of it. This is known as *block scope*. Once the loop is finished, the variable is sent to the garbage collector.

* The increment statement in the header of a `for` loop does not necessarily have to use the `++` operator. It could be `--`, `+=`, or another similar operator.

* Using return statements inside loops can be odd because they immediately terminate the execution of the loop (and the enclosing function, for that matter).

## Unit 5: Writing Classes

* Don't forget about the "has-a" relationship between an object and its methods/instance variables.

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

* For the purposes of AP Computer Science A, all instance variables should **always** be designated as `private` to enforce data encapsulation.

* A default no-argument constructor is **only** provided when no constructors are written. **If you write a constructor with parameters, Java will not automatically provide a no-argument constructor.**

* Unless explicitly directed to, remember not to destroy persistent data! More on this on the [exam preparation](exam_preparation.md#free-response-questions) page.

* Be aware of the different types of Java comments – single-line, block, and Javadoc.

* Preconditions don't need to be checked. It is assumed that they are satisfied. Postconditions must be met, in all cases, after the method executes.

* Just as with `null` values stored in variables of a reference type, methods with a return type that is a reference type may return a `null` value.

* Remember that methods are "pass by value" and "return by value", meaning that a copy of the primitive value or object reference (but not the object itself) is made.

* Static methods must be called with the class name and the dot operator, not an object reference and the dot operator.

* The `this` keyword itself refers to a method's associated object. So, the object can be passed as a parameter to a method call (for example: `System.out.println(this)`), or the `this` keyword can be used to access the object's instance variables (for example: `this.age`).

* When an object is passed to a print method, the `toString` method is implicitly called, as in the example in the previous list item.

* Static methods, by their nature, do not have a `this` reference, since they aren't associated with any object.

* *Method decomposition* refers to the breaking down of a solution to a problem into multiple methods that each perform a specific task to solve part of the larger problem.

## Unit 6: Array

* Arrays, unlike `ArrayList`s, can store primitive **or** reference data. They are also of a fixed size, meaning it cannot be changed after instantiation.

* The size of the array is declared when it is instantiated with the `new` keyword, not when its variable is declared. For example:

  ```java
  int[] myArray = new int[10];  // declaration declares the type
                                // instantiation sets the size
  ```

* **Arrays are zero-indexed**. Their indices start from `0`, not `1`. Therefore, the last index is at `length - 1`. Do not forget this!

* Make sure to be familiar with the default values for array elements, which is what all elements are set to upon instantiation unless an initializer list (with `{}`) is used.
  * `int`: 0
  * `double`: 0.0
  * `boolean`: `false` &nbsp;&nbsp;&nbsp;(This one may be particularly easy to forget).
  * Any reference type: `null`

* There is a separate out-of-bounds exception for arrays: `ArrayIndexOutOfBoundsException`.

* You can't modify the array element with an enhanced `for` loop, i.e. change its primitive value or object reference. The enhanced for loop variable is only available in the body of the loop, and changing it does not change the value stored in the array. Be careful not to destroy any object data though, since the object reference is copied to the enhanced for loop variable, not the object itself.

## Unit 7: `ArrayList`

* `ArrayList`s, unlike arrays, can **only** store reference data. Wrapper classes can be used as a way to store primitives. `ArrayList`s also automatically resize as elements are added and removed.

* There is no equivalent to the array initializer list (that is within the scope of AP CSA) for `ArrayList`s. Any default state must be set with the `add` method.

* Remember that a `ConcurrentModificationException` is thrown when you try to modify an `ArrayList` while it is being traversed with an enhanced `for` loop.

* Note that an `IndexOutOfBoundsException`, not an `ArrayIndexOutOfBoundsException`, is thrown when you try to access an out-of-bounds index in an `ArrayList`.

## Unit 8: 2D Array

* For AP CSA, all 2D arrays will utilize *row-major order*. This means that the first access index refers to the row and the second access index refers to the column.

  ```java
  // 7 will be set at the 6th row and 2nd column
  myArray[5][1] = 7;
  ```

* Functionally, a 2D array is stored as an array of arrays of a specific type. Therefore, special attention must be given when traversing a 2D array with an enhanced `for` loop.
  * The type of the **outer** enhanced `for` loop must be an **array** of the type that is stored in the 2D array. For example:

    ```java
    int[][] myArray = new int[10][10];

    for (int[] row : myArray) {
        for (int col : row) {
          // prints each value in the 2D array
          System.out.println(col);
        }
    }
    ```

## Unit 9: Inheritance

* There is an "is-a" relationship between the subclass and the superclass. The thing represented by the subclass "should be" a thing represented by the superclass, e.g. cheddar "is a" cheese, where `Cheddar` is the subclass and `Cheese` is the superclass.

* While any given class can only **directly** extend one class, a longer inheritance hierarchy can be built, i.e. the superclass can be the subclass to another superclass, and so on.
  * Proof? All classes in Java that do not extend another class automatically extend the `Object` class. So, the inheritance hierarchy for the cheeses looks like:

  ```text
  (highest)     Object > Cheese > Cheddar     (lowest)
  ```

* Constructors are **not** inherited by the subclass, but `public` methods and instance variables **are**. (Note that, in the context of AP CSA [where all instance variables should be `private`], the subclass can't actually access the superclass's instance variables. The same is true of the superclass's `private` methods.)

* If the superclass constructor is not explicitly called on the first line of the subclass constructor (with `super`), the no-argument superclass constructor is implicitly called in this place.

* Because of the way in which constructor calls are resolved, the body (excluding the implicit or explicit superclass call)[^1] of the highest constructor in the hierarchy is executed first. Then, the body of the next highest constructor is executed, and so on. So, for example, the `Object` constructor would be executed first, then the `Cheese` constructor, then the `Cheddar` constructor.

* Make sure to know the difference between overloading and overriding. You don't have to override any methods in the subclass, but you can. Similarly, you don't have to add any new methods in the subclass, but you can.

* References of a superclass type can contain pointers to objects that are actually of that type **or** a subclass of it.
  * For example, a variable declared as the `Cheese` type can hold a `Cheese` object or a `Cheddar` object.
  * In a case like this, **only** methods of `Cheese` can be called on the object. Methods that are defined exclusively in `Cheddar` cannot be used. However, if the variable (of type `Cheese`) stores a `Cheddar` and the `Cheddar` class overrides a method of `Cheese`, the method defined in the `Cheddar` class (not the `Cheese` method) will be executed.

    ```java
    public class Cheese {
        // constructor not shown
        public void printMessage() {
            System.out.println("Cheese is tasty!");
        }
    }

    public class Cheddar extends Cheese {
        // constructor and instance vars not shown
        public void printMessage() {
            System.out.println("Cheddar is better!");
        }

        public void getColor() {
            System.out.println(color);
        }
    }
    ```

    ```java
    Cheese c = new Cheddar();
    c.printMessage();  // prints "Cheddar is better!"
    c.getColor();      // error
    ```

## Unit 10: Recursion

* Make sure to be familiar with how to use base cases and recursive calls properly.

* Remember that each and every call to the recursive method, including the initial call and all subsequent recursive calls, has its own local variables that are specific to that call and are not shared by any other call.

[^1]: "Executed" here refers to the execution of everything after the superclass constructor call. Of course, the lowest constructor in the hierarchy is *actually* called first, but nothing happens beyond the superclass call until **all** of the higher constructors finish executing. So, a more accurate thing to say is that the highest constructor in the hierarchy *finishes* executing first.
