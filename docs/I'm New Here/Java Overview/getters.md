<h1> Getters </h1>

<h2> What are Getters? </h2>

Getters (accessor methods) are methods that return the value of a private field. They provide controlled read access to an object's internal data.

<h2> Why Use Getters? </h2>

Getters promote encapsulation:
- Protect internal data from direct access
- Allow validation or computation before returning values
- Enable changing internal implementation without affecting external code
- Provide read-only access when needed

<h2> Getter Syntax </h2>

Standard getter pattern:
```java
public class Robot {
    private double speed;
    private boolean isEnabled;
    
    // Getter for speed
    public double getSpeed() {
        return speed;
    }
    
    // Getter for boolean (use 'is' prefix)
    public boolean isEnabled() {
        return isEnabled;
    }
}
```

<h2> Using Getters </h2>

Call getters to access private fields:
```java
Robot robot = new Robot();
double currentSpeed = robot.getSpeed();
if (robot.isEnabled()) {
    // Do something
}
```

<h2> Naming Conventions </h2>

Follow Java naming conventions:
- Use `get` prefix: `getSpeed()`, `getPosition()`
- For booleans, use `is` prefix: `isEnabled()`, `isMoving()`
- Name should clearly indicate what is returned
