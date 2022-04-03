# Unit 1: Primitive Types

View the [condensed version](condensed)

## Unit Overview

Unit 1 serves as an introduction to the AP Computer Science A course and the Java programming language.

## Essential Knowledge

### Printing and String Literals

* Use `System.out.print` and `System.out.println` to print to the console without and with a newline at the **end** of the string argument, respectively.

  * ```java
    System.out.print("Hello, ");
    System.out.println("world!");
    System.out.print("This is Java!");
    ```

    > ```text
    > Hello, world!
    > This is Java!
    > ```

* A *string literal* is a sequence of characters surrounded by double quotes. It is known as a string *literal* because it is a literal value that is defined directly within the code, rather than being obtained from some outside source.
  * `"Hello, "`, `"world!"`, and `"This is Java!"` (from the above example) are all string literals.

### Data Types

* *Data types* are a set of related (thus, why they are a *type*) values. Each type has a set of operations that can be performed on values of that type.
  * *Primitive types*, discussed in this unit, are the most basic types of data from which all other data structures are built.
* There are only **three** primitive types assessed on the AP Exam:
  * `int`: represents an integer value, i.e. one without a decimal point
    * `30`, `0`, `-560`
  * `double`: represents a floating-point value, i.e. a real number with a decimal point
    * `3.14`, `0.0`, `-1.62`
  * `boolean`: has two possible states: `true` or `false`
  * Note that the `char` type is **not** assessed on the AP Exam.
* Just as *string literals* are literal string values declared in the code, these primitive data types can also have literal values that are declared in the code.

  * ```java
    int x = 5;
    double y = 3.14;
    boolean z = true;
    ```

    `5`, `3.14`, and `true` are all literal values of the `int`, `double`, and `boolean` types, respectively.

* Variables of primitive types have memory associated with them, in which the primitive value is stored.
* When the `final` keyword is used to declare a variable, its value cannot be changed **after it is initialized**.

  * ```java
    final int x = 5;
    x = 10; // Compile-time error: x cannot be changed
    ```

### Operations on Data and Variables

* *Operators* are symbols used in the code to perform certain tasks, like adding two `int`s.

### The Arithmetic Operators

* `+`: the addition operator; adds two numbers
* `-`: the subtraction operator; subtracts one number from another
* `*`: the multiplication operator; multiplies two numbers
* `/`: the division operator; divides one number by another
* `%`: the modulus operator; returns the remainder of one number divided by another

```java
5 + 3; // 8
5 - 3; // 2
5 * 3; // 15
5 / 3; // 1
5 % 3; // 2

5.0 + 3.0; // 8.0
5.0 - 3; // 2.0
5 / 3.0; // 1.6666666666666667
```

Note how, in the above code block, the `5 / 3` expression evaluates to `1`. This comes with a very important distinction to make: that between *integer math* and *double math*.

When a mathematical operation, such as division, is performed on two **integer** values, the result is **ALWAYS** an **integer**. So, what happens if we try to divide `5` by `3`? Mathematically, we know that this does not result in an integer value – it is equal to about 1.67. Java needs to convert this to an integer value, so it always *truncates* the value, meaning it removes the decimal point and whatever follows it. So, the result is `1`.

However, when a mathematical operation is performed with at least one **double** value, the result is **ALWAYS** a **double**. This can be seen if we try to divide `5` by `3.0`. As you would expect, the result is about `1.67`.

Keep in mind that `8` and `8.0` are not the same thing. The former is an integer value, and the latter is a double value (since it has a decimal point). This distinction will become more important later.

One other thing to note is that trying to divide by zero will result in a runtime *exception*, which is an error that stops the program's execution from continuing. The name of this specific exception is an `ArithmeticException`. If you try to divide by zero, your code will stop executing at that point.

#### Operator Precedence

Recall that mathematical expressions are evaluated in a certain order, i.e. PEMDAS. In Java, the same is true.

The *multiplicative* operators (`*`, `/`, `%`) have higher *operator precedence* than the *additive* operators (`+`, `-`). This means that all multiplication, division, and use of the modulus operator is evaluated first, from left to right. Then, all addition and subtraction is evaluated, from left to right. As in mathematics, parentheses can be used to change the order of evaluation.

```java
5 + 3 * 2; // 11
(5 + 3) * 2; // 14
2 + 5 * 10 / 2; // 27
```

### Declaration and the Assignment Operator

The concept of variables has been discussed. This is put into practice with the *assignment operator*, `=`. The assignment operator *assigns* a value to a variable, essentially "storing" it in that variable.

First, a variable must be *declared* with the type that it will hold, as in line 1. Then, the variable can be *initialized*, or assigned a value for the first time, as in line 2.

```java
int x;  // line 1
x = 5;  // line 2
```

This can also be done in one line:

```java
int x = 5;
```

If a compound expression exists to the right of the assignment operator, that expression is evaluated first, then the result is assigned to the variable:

```java
int x = 5 + 3;  // x = 8
```

<details>
<summary>A technical note on why exactly this occurs</summary>

> Why is everything to the right of the equals sign evaluated first? This goes back to the idea of operator precedence. The assignment operator actually has the lowest precedence of any Java operator, so all of the mathematical (and other) operators are evaluated first. Then, the assignment operator is evaluated, and the result is assigned to the variable.

</details>

### Compound Assignment / Increment and Decrement

Consider a code segment like:

```java
int x = 5;
x = x + 3; // 8
```

Here, the value of `x` is first added to `3`, and the result (`8`) is then assigned to `x`.

The second line of this segment can be shortened with the use of *compound assignment operators*. In Java, these compound assignment operators are `+=`, `-=`, `*=`, `/=`, and `%=`. Compound assignment operators work by performing the appropriate arithmetic operation using the current variable value as the first operand and the value to the right of the operator as the second operand. Then, the result is assigned to the variable.

So, the following two lines are equivalent:

```java
x = x + 3;
x += 3;
```

As are these:

```java
x = x / 3;
x /= 3;
```

There is also a shorthand for incrementing and decrementing a variable by 1.

```java
x++; // is equivalent to
x += 1;
```

```java
x--; // is equivalent to
x -= 1;
```

---
View the [condensed version](condensed)

Advance to [Unit 2](../2-using-objects/in-depth.md)

To the [table of contents](../../table_of_contents.md)