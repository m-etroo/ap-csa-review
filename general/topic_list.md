<!-- markdownlint-disable MD031 -->
<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD024 -->
# AP Exam Topic List

This is essentially a full, unit-by-unit guide of all the topics covered on the AP Exam. More detailed explanations of each topic are offered in the unit pages (see [table of contents](../table_of_contents.md)).

## Unit 1: Primitive Types

* Printing with `System.out.print` and `System.out.println`
  * The difference between these two methods
* String literals and literals for other types of values (e.g. integer literals)
* The concept of a data type
  * Primitive vs. reference (object) types
  * Operations that can be performed on values of a type
* The primitive types for AP CSA: `int`, `double`, `boolean`
  > `char` is **not** assessed on the AP Exam
* Variables are declared of a specific type and have associated memory to store values
  * Variables of primitive types can store primitive values
* The `final` keyword
* Arithmetic operations on `int` and `double` values
  * Arithmetic operators: `+`, `-`, `*`, `/`, `%`
  * Compound expressions using these operators
  * Operator precedence (i.e. order of operations)
  * `ArithmeticException` upon dividing by zero
* Integer math vs. double math and when each is used
* Assignment operator: `=`
  * Anything to the right of the operator (e.g. a mathematical expression) is evaluated **first** and then assigned to the variable on the left
* Compound assignment operators: `+=`, `-=`, `*=`, `/=`, `%=`
* Increment and decrement operators: `++`, `--`
  > The use of these within other expressions, e.g. `arr[i++]`, is **not** assessed on the AP Exam
* Casting with `int` and `double`
  * Automatic widening casting from `int` to `double`
  * Narrowing casting from `double` to `int` is **not** automatic
    * Narrowing casting results in the truncation of the `double` value
* Rounding with the casting operators
  ```java
  (int) (x + 0.5);  // positive x
  (int) (x - 0.5);  // negative x
  ```
* Size of an `int`
  * 4 bytes
  * Range of `Integer.MIN_VALUE` to `Integer.MAX_VALUE`, inclusive
  * Integer overflow may result in an incorrect value inside that range

## Unit 2: Using Objects

* Object vs. class distinction
* Constructor signatures: name and parameter list
  * Parameter list specifies parameter type and parameter name
  * Constructors have the same name as the class
* Formal vs. actual parameters
  * Parameters that are passed in set the initial state of the object (i.e. set the instance variables)
* "Call by value"
* Overloaded constructors
* `new` keyword and calling a constructor
  * Classes written by other programmers and as part of class libraries can be instantiated in this same manner
  * The types of the actual parameters passed in **must** match the order of the formal parameter list of one of the class' constructors
    * i.e. passing in an `int` and a `String` requires a constructor with a `int` and `String` as formal parameters, in that order
* `null` keyword
  * Two possible values for a variable of a reference (object) type: `null` **or** a reference to an object
    ```java
    Dog one = null;         // null value
    Dog two = new Dog();    // reference to an object
    ```
  * In the case of the latter, the reference is actually a pointer to a memory location where the object is stored in memory
  * Calling a method or accessing an instance variable on something that is `null` results in a `NullPointerException`
* Concept of an object's methods (collectively, its behavior)
  * Methods allow objects to do things or things to be done to it
* Method signatures: method name, parameter list, and return type
  * Return type of `void` means the method returns nothing
* Non-static methods must be called through objects with the dot operator (`.`), with the parameters (if any) in parentheses
  * i.e. `dog.bark()`
  * The types of the actual parameters passed in **must** match the order of one of the method's formal parameter lists
* Overloaded methods
* Flow of control when calling a method
  * A method call interrupts the execution of the caller to execute the method
  * Once the method is done executing, the execution of the caller resumes
* The return value of a non-`void` method can be stored in a variable or used in an expression
* Abstraction with methods
* Creating `String` objects
  * Using string literals
  * Using the `String` constructor: `String(String str)`
* Immutability of `String`s
* Concatenation of `String`s with `+` or `+=`
  * A new `String` is created because `String`s are immutable
  * Concatenating primitive(s) to a `String` implicitly converts the primitive(s) to `String`(s)
  * Concatenating an object to a `String` implicitly calls the object's `toString` method to convert it to a `String`
* Escape sequences: `\"`. `\\`, `\n`
* Basic concept of APIs and libraries: to simplify complex tasks
* Grouping of classes into packages
  * `String` is a member of the `java.lang` package
  * The `java.lang` package does not need to be imported
* Valid `String` indices
  * `StringIndexOutOfBoundsException`
* Use of `String` methods on the Java Quick Reference
* Use of `substring` method of a `String` to retrieve the element at index `i`: `substring(i, i+1)`
* `Integer` and `Double` wrapper classes are members of the `java.lang` package
* Use of the `Integer` and `Double` methods on the Java Quick Reference
* Autoboxing and unboxing
  * The necessary conversion is applied when passing values to a method or when assigning values to variables
* Calling static methods with the class name
* Use of the `Math` static methods on the Java Quick Reference
  * Generate random values

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

* Not destroying/modifying objects provided as parameters to the constructor, i.e. storing a copy of the object in an instance variable
  > Destroying persistent data on the AP Exam FRQs **will** result in a score penalty.

* Default no-argument constructor

#### Comments, documentation, and pre/postconditions

* Describe code with comments and understand their purpose

* The three types of Java comments (single-line, block, Javadoc)

* Preconditions
  > There is no expectation that you check input against the preconditions when writing FRQs, and it will result in a score penalty if you write an incorrect check.

* Postconditions

#### Accessor and mutator methods

* Write/understand the purpose of accessor (getter) methods

* Write/understand the purpose of mutator (setter) methods

#### Writing methods

* Void vs. non-void methods

* Declaring return types

* "Return by value"
  * With object references as return values, the **reference** is copied, **not** the object

#### Miscellaneous

* The `toString` method, its purpose, and how to override it

* Understand that the `toString` method is implicitly called when an object is passed to one of the print methods
