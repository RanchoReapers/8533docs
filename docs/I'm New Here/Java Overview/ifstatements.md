<h1> If, If-Else, and Else-If Statements </h1>

<h2> What are Conditional Statements? </h2>

Conditional statements allow your program to make decisions and execute different code based on conditions. They are fundamental to controlling program flow.

<h2> If Statements </h2>

Execute code only if a condition is true:
```java
if (temperature > 80) {
    turnOnCooling();
}
```

<h2> If-Else Statements </h2>

Execute one block if condition is true, another if false:
```java
if (batteryVoltage > 12.0) {
    enableRobot();
} else {
    disableRobot();
    showWarning();
}
```

<h2> Else-If Statements </h2>

Check multiple conditions in sequence:
```java
if (distance < 10) {
    setSpeed(0.2);
} else if (distance < 50) {
    setSpeed(0.5);
} else if (distance < 100) {
    setSpeed(0.8);
} else {
    setSpeed(1.0);
}
```

<h2> Best Practices </h2>

- Use clear, readable conditions
- Consider the order of else-if conditions (most specific first)
- Use braces even for single-line blocks
- Avoid deep nesting (consider extracting to methods)
- Handle all possible cases

<h2> Common Patterns in FRC </h2>

```java
// Safety check
if (isEnabled && !isInDangerZone()) {
    runMotors();
}

// State-based control
if (gamepad.getAButton()) {
    shootGamePiece();
} else if (gamepad.getBButton()) {
    intakeGamePiece();
}
```
