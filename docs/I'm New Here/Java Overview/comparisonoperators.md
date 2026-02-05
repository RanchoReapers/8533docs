<h1> Comparison Operators </h1>

<h2> What are Comparison Operators? </h2>

Comparison operators compare two values and return a boolean result (true or false). They are essential for making decisions in your code.

<h2> Relational Operators </h2>

Java provides six comparison operators:
- **==** Equal to: `x == 5` (true if x equals 5)
- **!=** Not equal to: `x != 0` (true if x is not 0)
- **>** Greater than: `speed > 100` (true if speed exceeds 100)
- **<** Less than: `angle < 90` (true if angle is below 90)
- **>=** Greater than or equal: `voltage >= 12.0`
- **<=** Less than or equal: `current <= 40`

<h2> Common Mistakes </h2>

Avoid these pitfalls:
- **Using = instead of ==**: `x = 5` assigns, `x == 5` compares
- **Comparing objects incorrectly**: Use `.equals()` for Strings and objects
```java
String name = "Test";
if (name == "Test") { }      // Wrong for Strings
if (name.equals("Test")) { } // Correct
```

<h2> Logical Operators </h2>

Combine multiple comparisons:
- **&&** AND: Both conditions must be true
- **||** OR: At least one condition must be true
- **!** NOT: Inverts the boolean value

Examples:
```java
if (speed > 0 && speed < 100) { }     // Speed between 0 and 100
if (isRed || isBlue) { }              // Either red or blue
if (!isDisabled) { }                  // Robot is enabled
```
