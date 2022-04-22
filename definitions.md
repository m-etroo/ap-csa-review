# Definitions

This page just has a few definitions that are widely used in this guide but that might not be entirely clear.

* **pointer** / **reference** – A pointer is a value in memory that "points" to another value in memory. In AP CSA, this usually refers to how a variable of a reference type doesn't actually store an object; rather, it stores a *pointer* to an object, which is located somewhere else in memory. This way, multiple variables can point to the exact same object. When you access a variable of a reference point, Java automatically points you to the object and performs whatever action you want on it.

* **[of a] reference type** – A reference type is a type of an object. So, for example, `String` is a reference type, while `int` is not (it is a primitive type). A variable of a reference type is just a variable that has its type declared as a reference type, e.g. `String myString;`.
