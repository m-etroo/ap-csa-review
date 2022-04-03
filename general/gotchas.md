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
  * Performing a mathematical operation that involves any double value will always result in a **double**. This means that even if the result is an integer, like in the case of `5 + 3`, which is 8, Java will report the result as `8.0`.

* Keep in mind that `8` and `8.0` are not the same thing. The former is an integer value, and the latter is a double value (since it has a decimal point). This may seem like a minor detail, but it is important because, for example, a method that accepts an `int` parameter will cause an error if `8.0` is passed to it. (This problem would be corrected with casting.)

* Dividing by zero results in an `ArithmeticException`, which is a runtime exception, not a compile error.

