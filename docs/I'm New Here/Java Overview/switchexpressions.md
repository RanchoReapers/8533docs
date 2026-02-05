<h1> Switch Expressions (Condensed Switch Statements) </h1>

<h2> What are Switch Expressions? </h2>

Switch expressions (Java 14+) are a modern, concise alternative to traditional switch statements. They can return values directly and use arrow syntax for cleaner code.

<h2> Arrow Syntax </h2>

Modern switch expressions use arrows (->):
```java
int state = 2;
String status = switch (state) {
    case 0 -> "Initializing";
    case 1 -> "Running";
    case 2 -> "Stopping";
    default -> "Unknown";
};
```

<h2> Advantages Over Traditional Switch </h2>

Switch expressions provide:
- **No break needed**: Each case is automatically isolated
- **Return values**: Entire switch evaluates to a value
- **Exhaustiveness checking**: Compiler ensures all cases covered
- **More concise**: Less boilerplate code
- **Safer**: No fall-through bugs

<h2> Multi-line Case Blocks </h2>

Use curly braces with `yield` for complex cases:
```java
String result = switch (mode) {
    case 0 -> "Simple case";
    case 1 -> {
        // Multiple statements
        doSetup();
        yield "Complex case";  // Use yield to return value
    }
    default -> "Default";
};
```

<h2> Multiple Case Labels </h2>

Handle multiple values in one case:
```java
String dayType = switch (day) {
    case "Monday", "Tuesday", "Wednesday", "Thursday", "Friday" -> "Weekday";
    case "Saturday", "Sunday" -> "Weekend";
    default -> "Invalid day";
};
```

<h2> Practical FRC Example </h2>

```java
double speed = switch (driveMode) {
    case SLOW -> 0.3;
    case MEDIUM -> 0.6;
    case FAST -> 1.0;
    default -> 0.5;
};
```
