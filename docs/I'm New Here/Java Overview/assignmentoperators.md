<h1> Assignment Operators </h1>

<h2> Basic Assignment Operator </h2>

The basic assignment operator `=` assigns a value to a variable:
```java
int speed = 100;        // Assigns 100 to speed
speed = 200;            // Reassigns to 200
```

The left side must be a variable, the right side can be any expression.

<h2> Compound Assignment Operators </h2>

Compound operators combine arithmetic with assignment:
- **+=** Add and assign: `x += 5` is equivalent to `x = x + 5`
- **-=** Subtract and assign: `x -= 3` is equivalent to `x = x - 3`
- **\*=** Multiply and assign: `x *= 2` is equivalent to `x = x * 2`
- **/=** Divide and assign: `x /= 4` is equivalent to `x = x / 4`
- **%=** Modulus and assign: `x %= 10` is equivalent to `x = x % 10`

<h2> Increment and Decrement Operators </h2>

Shortcuts for adding or subtracting 1:
- **++** Increment: `counter++` is equivalent to `counter = counter + 1`
- **--** Decrement: `counter--` is equivalent to `counter = counter - 1`

Pre-increment vs Post-increment:
```java
int x = 5;
int y = ++x;  // Pre-increment: x becomes 6, y is 6
int z = x++;  // Post-increment: z is 6, then x becomes 7
```

<h2> Practical Examples in FRC </h2>

```java
motorSpeed += 10;          // Increase motor speed by 10
loopCounter++;             // Increment loop counter
position -= correction;    // Apply correction to position
```
