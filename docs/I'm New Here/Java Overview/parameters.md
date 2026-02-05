<h1> Parameters </h1>

<h2> What are Parameters? </h2>

Parameters (also called arguments) are values passed into methods/functions to provide input data. They allow methods to be flexible and reusable with different inputs.

<h2> Defining Method Parameters </h2>

Parameters are defined in the method signature:
```java
public void setMotorSpeed(double speed) {
    // speed is a parameter
    motor.set(speed);
}

public double calculateDistance(double x1, double y1, double x2, double y2) {
    // Four parameters
    return Math.sqrt((x2-x1)*(x2-x1) + (y2-y1)*(y2-y1));
}
```

<h2> Calling Methods with Arguments </h2>

When calling a method, provide values (arguments) for each parameter:
```java
setMotorSpeed(0.75);                           // One argument
double dist = calculateDistance(0, 0, 3, 4);  // Four arguments
```

Arguments must match the parameter types and order.

<h2> Parameter Types </h2>

Parameters can be:
- **Primitives**: int, double, boolean, etc.
- **Objects**: String, custom classes, etc.
- **Arrays**: collections of values

<h2> Best Practices </h2>

- Use descriptive parameter names
- Keep the number of parameters reasonable (3-4 max when possible)
- Consider using objects to group related parameters
- Document what each parameter represents
