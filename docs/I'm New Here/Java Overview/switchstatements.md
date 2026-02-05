<h1> Switch Statements </h1>

<h2> What are Switch Statements? </h2>

Switch statements provide a clean way to select one of many code blocks to execute based on the value of a variable. They're especially useful when you have many specific values to check.

<h2> Basic Switch Syntax </h2>

```java
int state = 2;

switch (state) {
    case 0:
        // Code for state 0
        initialize();
        break;
    case 1:
        // Code for state 1
        running();
        break;
    case 2:
        // Code for state 2
        stopping();
        break;
    default:
        // Code if no case matches
        error();
        break;
}
```

<h2> The Break Statement </h2>

The `break` statement exits the switch:
- Without `break`, execution "falls through" to the next case
- Fall-through is occasionally useful but usually unintended
- Always use `break` unless intentionally falling through

<h2> Switch with Strings </h2>

Java allows switching on Strings:
```java
String command = "forward";

switch (command) {
    case "forward":
        moveForward();
        break;
    case "backward":
        moveBackward();
        break;
    case "stop":
        stop();
        break;
    default:
        System.out.println("Unknown command");
}
```

<h2> When to Use Switch </h2>

Use switch when:
- Checking a single variable against multiple specific values
- You have 3 or more cases
- Values are constants (not ranges)

Use if-else when:
- Checking complex conditions
- Comparing ranges
- Using relational operators (>, <, etc.)
