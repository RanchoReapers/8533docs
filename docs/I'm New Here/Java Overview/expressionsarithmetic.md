<h1> Expressions & Arithmetic </h1>

<h2> What are Expressions? </h2>

An expression is a combination of variables, operators, and values that evaluates to a single value. Expressions are fundamental building blocks in programming.

Examples:
```java
5 + 3              // Evaluates to 8
motorSpeed * 2     // Evaluates to double the motor speed
x > 10             // Evaluates to true or false
```

<h2> Arithmetic Operators </h2>

Java provides standard arithmetic operators:
- **+** Addition: `5 + 3` equals 8
- **-** Subtraction: `10 - 4` equals 6
- **\*** Multiplication: `6 * 7` equals 42
- **/** Division: `15 / 3` equals 5
- **%** Modulus (remainder): `17 % 5` equals 2

<h2> Order of Operations </h2>

Java follows standard mathematical order (PEMDAS):
1. Parentheses
2. Multiplication, Division, Modulus (left to right)
3. Addition, Subtraction (left to right)

Examples:
```java
int result = 5 + 3 * 2;        // result = 11 (not 16)
int result = (5 + 3) * 2;      // result = 16
```

<h2> Integer vs Floating-Point Division </h2>

Be careful with integer division:
```java
int a = 7 / 2;        // a = 3 (integer division, truncates)
double b = 7.0 / 2;   // b = 3.5 (floating-point division)
double c = 7 / 2.0;   // c = 3.5
```
