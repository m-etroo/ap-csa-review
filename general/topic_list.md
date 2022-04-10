<!-- markdownlint-disable MD031 -->
<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD024 -->
# AP Exam Topic List

This is essentially a full, unit-by-unit guide of all the topics covered on the AP Exam. More detailed explanations of each topic are offered in the unit pages (see [table of contents](../table_of_contents.md)).

## Unit 1: Primitive Types

#### Printing and literals

* Printing with `System.out.print` and `System.out.println`
  * The difference between these two methods

* Literals, including string literals

#### Variables and data types

* Concept of a type

* Primitive vs. reference types

* Primitive types for AP CSA: `int`, `double`, `boolean`
  * When each is appropriate
  > `char` is **not** assessed on the AP Exam

* Limitations on `int`
  * 4 byte size
  * Valid range of integers (using the static constants of `Integer`, not the literal values)
  * Integer overflow concept

* Concept of a variable

* Declaring variables

* The `final` keyword

#### Expressions

* Arithmetic operations on `int` and `double` values
  * Arithmetic operators: `+`, `-`, `*`, `/`, `%`
  * Compound expressions using these operators
  
* Operator precedence (i.e. order of operations)

* `ArithmeticException` upon dividing by zero

* Integer math vs. double math and when each is used

#### Using variables and data types

* Assignment operator: `=`
  * Evaluation of any expressions on the right, **then** assignment to the variable

* Compound assignment operators: `+=`, `-=`, `*=`, `/=`, `%=`

* Increment and decrement operators: `++`, `--`

* Casting with `int` and `double`
  * Widening vs. narrowing casting
  * Truncation

* Rounding with the casting operators

## Unit 2: Using Objects

* Object vs. class distinction

#### Class constructors

* Purpose of the constructor: to set the initial state of an object

* Constructor signatures: name and parameter list
  * Parameters have a name and type

* Constructors have the same name as the class

* Formal vs. actual parameters

* "Call by value" as it applies to constructors

* Overloaded constructors

* `new` keyword and calling a constructor
  * Also applies to classes written by other programmers
  * Proper parameter(s) (or none, if there is a no-argument constructor) must be passed in

#### Methods of an object

* Concept of an object's methods (collectively, its behavior)

* Method signatures: method name, parameter list, and return type

* `void` return type

* Overloaded methods

* Call methods with the dot operator (`.`) and parameter(s), if applicable
  * Proper parameter(s), or none (if applicable), must be passed in

* Flow of control when calling a method
  * A method call interrupts the execution of the caller to execute the method
  * Once the method is done executing, the execution of the caller resumes

* Use return values of methods

#### `String`, `Integer`, `Double`, `Math`

* Grouping of classes into packages
  * The above classes (in the heading of this section) are all members of the `java.lang` package
  * `java.lang` does **not** need to be imported

* Basic concept of APIs and libraries: to simplify complex tasks

##### `String`

* Create `String` objects; two methods:
  * String literals
  * String constructor

* Immutability of `String` objects

* Concatenation of `String` objects
  * A new `String` is created because `String`s are immutable
  * Concatenating a primitive to a `String` implicitly converts the primitive to a `String`
  * Concatenating an object to a `String` implicitly calls the object's `toString` method to convert it to a `String`

* Escape sequences: `\"`. `\\`, `\n`

* Valid `String` indices
  * `StringIndexOutOfBoundsException`

* `String` methods on the Java Quick Reference
  * Use of `substring` method of a `String` to retrieve the element at index `i`, i.e. single element substring

##### `Integer` and `Double` wrapper classes

* Distinction between the wrapper classes and the associated primitives

* `Integer` and `Double` methods on the Java Quick Reference

* Autoboxing and unboxing
  * Occurs as needed when passing values to a method or when assigning values to variables

##### `Math` class

* Call static methods with the class name

* `Math` static methods on the Java Quick Reference
  * Generate random values inside a specified range with `Math.random`

#### Miscellaneous

* Abstraction with methods

* `null` keyword
  * Variables of a reference type can hold either `null` **or** a reference to an object
    ```java
    Dog one = null;         // null value
    Dog two = new Dog();    // reference to an object
    ```
  * In the case of the latter, the **reference** is a pointer to the memory location of the actual object
  * `NullPointerException` when trying to perform certain operations with a `null` reference

## Unit 3: Boolean Expressions and `if` Statements

#### Boolean expressions

* Relational equality operators: `==`, `!=`

* Relational comparison operators: `<`, `<=`, `>`, `>=`

* Write/evaluate Boolean expressions with these relational operators

#### Conditional statements

* Purpose behind conditional statements

* Write/use `if` statements (also known as a *one-way selection*)

* Write/use `if-else` statements (also known as a *two-way selection*)

* Incorporate `else if` statements into `if` and `if-else` statements (*multi-way selection*)

* Difference between and when to use `if` vs. `if-else` statements, as well as when to incorporate `else if` statements

* Nested `if` statements

#### Compound Boolean expressions

* Logical operators: `!`, `&&`, `||`
  * Operator precedence for logical operators (which is the same as the order in which they are listed above)

* Write/evaluate compound Boolean expressions with these logical operators

* Short-circuited evaluation

* De Morgan's logic laws

* Truth tables

* Understand the concept of equivalent Boolean expressions

#### Object comparison

* Aliases (in the context of object references)
  * Use of the relational equality operators to determine if two object references are aliases

* Use of the relational equality operators and `null` to determine if a variable of a reference type points to an actual object

* `.equals` methods to check for equivalency

* Equivalency vs. equality for objects

## Unit 4: Iteration

#### Iteration statements

* Understand the purpose behind iteration

* Write/use `while` loops
  * Boolean expression inside the loop header

* Write/use `for` loops
  * Three parts of the loop header

* Flow of control for these loops
  * `while` loop: Repetition until the Boolean expression evaluates to `false`
  * `for` loop: Initialization statement, then repetition until the Boolean expression evaluates to `false`, with the increment statement after each iteration

* Rewrite `for` loops as `while` loops and vice versa

* Infinite loops

* Loops that never execute

* Return statements inside loops

* Off by one errors

#### Iterative algorithms

* Identify, modify, and develop the following algorithms:
  * Check for divisibility
  * List the digits of an integer
  * Determine how often a specific criterion is met
  * Determine a minimum or maximum value
  * Determine a sum
  * Determine an average
  * Determine a mode
  * Determine if and how many substrings meet a certain criterion
  * Reverse a string

#### Nested iteration

* Write/use nested loops

* Flow of control for these loops
  * Inner loop must finish executing **before** outer loop continues

#### Miscellaneous

* Determine how many times a specific statement executes

* Compare two loops

## Unit 5: Writing Classes

#### About classes and objects

* Access modifiers (`public` and `private` only)
  * Classes: `public`
  * Instance variables: `private`
  * Constructors: `public`
  * Methods: `public` **or** `private`

* Data encapsulation
  * `private` access modifier and accessor/mutator methods to achieve this

* Object state and the "has-a" relationship

#### Constructors

* Write constructors to establish initial object state

* Purpose and use of constructor parameters to set state

* Not destroying/modifying objects provided as parameters to the constructor – store a copy of the object in an instance variable instead
  > Destroying persistent data on the AP Exam FRQs **will** result in a score penalty.

* Default no-argument constructor

#### Comments, documentation, and pre/postconditions

* Describe code with comments and understand their purpose

* The three types of Java comments (single-line, block, Javadoc)

* Preconditions
  > There is no expectation that you check input against the preconditions when writing FRQs, and it will result in a score penalty if you write an incorrect check.

* Postconditions

#### Writing methods

* The concept of methods – input is usually passed in, something is done, and sometimes a value is returned

* Write methods to perform tasks with input/return values

* Void vs. non-void methods

* Declaring return types

* "Return by value"
  * With object references as return values, the **reference** is copied, **not** the object

* `private` access modifier rules apply to parameters

* Not destroying/modifying objects provided as parameters to methods unless required
  > Destroying persistent data on the AP Exam FRQs **will** result in a score penalty.

* Formal parameter initialization
  * Primitive actual parameters are copied
  * Reference actual parameters are copied – the **reference**, not the object
    * Formal and actual parameter become aliases

#### Static members

* The concept that static members are associated with a class, not an object
  * Static methods cannot change instance data or use non-static methods – only static variables and methods

* Write static methods and declare static variables

* Call static methods and use static variables
  * Class name and dot operator

* `static` keyword

* No `this` reference

#### Accessor and mutator methods

* Write/understand the purpose of accessor (getter) methods

* Write/understand the purpose of mutator (setter) methods

#### Scope, access, and `this`

* Local scope
  * Cannot be declared with access modifiers
  * Can only be accessed within the defining method (or constructor)

* Local variables have precedence over instance variables when they have the same name

* `this` keyword
  * Use as a method parameter

#### Miscellaneous

* The `toString` method, its purpose, and how to override it

* Understand that the `toString` method is implicitly called when an object is passed to one of the print methods

* Method decomposition

> The ethical and social implications of computing are not assessed on the AP Exam.

## Unit 6: Array

#### Creating and accessing arrays

* Concept and purpose of an array
  * Can store primitive or reference data

* Array creation syntax with `new`

* Array access syntax with square brackets

* Create and modify arrays

* Array size is fixed

* Default values for array elements
  * For arrays of `int`, `double`, `boolean`, and reference types

* Initializer lists

* Valid array indices
  * Arrays are zero-indexed
  * `ArrayIndexOutOfBoundsException`

#### Traversing arrays

* Meaning of "traversing an array"

* Use `for` or `while` loops to traverse arrays with indices

* Use enhanced `for` loops to traverse arrays with the enhanced `for` loop variable
  * Values stored in the enhanced `for` loop variable are **copies** of the array elements
  * Enhanced `for` loop cannot be used to edit the array values

* Awareness of and avoidance of off by one errors

#### Array algorithms

* Identify, modify, and develop the following algorithms:
  * Determine a minimum or maximum value
  * Determine a sum
  * Determine an average
  * Determine a mode
  * Determine if and how many elements meet a certain criterion
  * Determine the consecutive pairs of elements that exist within the array
  * Determine if duplicate elements exist in the array
  * Shift elements in one direction
  * Reverse the array elements

## Unit 7: `ArrayList`

#### Understanding and creating `ArrayList`s

* Differences between arrays and `ArrayList`

* Properties of an `ArrayList`
  * Stores reference types only
  * Mutable data of a dynamic size

* `ArrayList` creation syntax with constructor

* Generic typing vs. non-generic typing
  * Advantages of using generic typing

* Importing `ArrayList` from the `java.util` package

#### Manipulating and traversing `ArrayList`s

* `ArrayList` methods in the Java Quick Reference

* Utilize the `ArrayList` methods to modify `ArrayList`s

* Traverse an `ArrayList` with `for`, `while`, and enhanced `for` loops
  * Properly handle indices that change when an element is removed

* Valid indices for `ArrayList`s
  * `ArrayList`s are zero-indexed
  * `IndexOutOfBoundsException`

* `ConcurrentModificationException` when modifying an `ArrayList` while traversing it with an enhanced `for` loop

#### `ArrayList` algorithms

* Identify, modify, and develop the following algorithms:
  * Insert elements while traversing the `ArrayList`
  * Remove elements while traversing the `ArrayList`
  * \+ all algorithms for [arrays](#array-algorithms)

* Be able to traverse multiple objects simultaneously to execute these algorithms

#### Searching and sorting

> These topics are applicable to both arrays and `ArrayList`s.

* Understand and apply the following algorithms:
  * Sequential search (also called linear search)
  * Selection sort
  * Insertion sort

* Compare these algorithms based on the number of times specified statements execute

> The ethical issues regarding data collection are not assessed on the AP Exam.

## Unit 8: 2D Array

#### Creating and accessing 2D arrays

* "Array of arrays" concept

* 2D array creation syntax with `new`

* 2D array access syntax with sets of square brackets

* Create and modify 2D arrays

* Initializer lists for 2D arrays

* Row-major vs. column-major order
  > The AP Exam uses **row-major order**.

#### Traversing 2D arrays

* Nested loops

* Use nested `for` and nested enhanced `for` loops to traverse 2D arrays

* Traversing the 2D array in row-major vs. column-major order

#### 2D array algorithms

* Identify, modify, and develop all [array algorithms](#array-algorithms) with 2D arrays

* Sequential/linear search

## Unit 9: Inheritance

#### Superclass-subclass relationship

* Concept of a superclass and subclass
  * Extension of superclass data and functionality with subclass

* Concept of class hierarchy

* "is-a" relationship between subclass and superclass

* `extends` keyword to define a subclass

* Subclasses may only have one superclass

#### Applying inheritance

* Call superclass constructors and methods with `super` and parameters, if applicable

* Implicit call to no-argument superclass constructor when there is no explicit call

* Execution order of constructors in the class hierarchy
  * Constructor calls from bottom (subclass) to top (`Object`), then constructor execution from top (`Object`) to bottom (subclass)

* Method overriding in subclasses

* Additional methods and instance variables in subclasses

* The subclass inherits public methods but **not** constructors

* Understand and apply polymorphism
  * Reference of a superclass may refer to an object of the superclass or subclass(es)
  * Reference of a superclass cannot call any subclass methods unless they are also defined in the superclass
  * If a method is declared in a superclass and subclass, a method call on an object of the subclass stored in a variable declared with the superclass type executes the method in the subclass, not the superclass

* `Object` class (`java.lang` package) as a superclass of all classes
  * `Object` methods in the Java Quick Reference

## Unit 10: Recursion

#### Recursion as a concept

* Concept of recursion and its applications

* Components of a recursive method, i.e. base case and recursive method call

* Unique local variables for each recursive method call, including parameters, which indicate the progress of the recursion

* Recursion vs. iteration

* Understand traversal of various objects and data structures with recursion

* Determine the result of a recursive method

> Writing recursive code is not assessed on the AP Exam.

#### Searching and sorting with recursion

* Binary search

* Merge sort
