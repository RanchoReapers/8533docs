<h1> Understanding Class Members & Methods </h1>

<h2> What are Class Members? </h2>

Class members are the components that make up a class:
- **Fields**: Variables that store object state
- **Methods**: Functions that define object behavior
- **Constructors**: Special methods for object initialization
- **Nested classes**: Classes defined within another class

<h2> Instance vs Static Members </h2>

**Instance Members** (non-static):
- Belong to each object instance
- Access with object reference: `robot.getSpeed()`
- Each object has its own copy
```java
public class Robot {
    private double speed;  // Instance field
    
    public void setSpeed(double s) {  // Instance method
        speed = s;
    }
}
```

**Static Members**:
- Belong to the class itself, not individual objects
- Shared by all instances
- Access with class name: `Math.PI`, `Constants.MAX_SPEED`
```java
public class Constants {
    public static final double MAX_SPEED = 1.0;  // Static field
    
    public static double convertToMeters(double inches) {  // Static method
        return inches * 0.0254;
    }
}
```

<h2> Method Signatures </h2>

A method signature includes:
- Access modifier (public, private, etc.)
- Return type (void, int, double, etc.)
- Method name
- Parameters (if any)

```java
public double calculateDistance(double x, double y) {
    return Math.sqrt(x*x + y*y);
}
```

<h2> The 'this' Keyword </h2>

`this` refers to the current object instance:
```java
public void setSpeed(double speed) {
    this.speed = speed;  // Distinguish field from parameter
}
```
