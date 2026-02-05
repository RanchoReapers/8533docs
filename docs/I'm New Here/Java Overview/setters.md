<h1> Setters </h1>

<h2> What are Setters? </h2>

Setters (mutator methods) are methods that modify the value of a private field. They provide controlled write access to an object's internal data.

<h2> Why Use Setters? </h2>

Setters enable:
- Input validation before changing values
- Triggering side effects when values change
- Logging or debugging when fields are modified
- Maintaining object invariants
- Protecting internal state consistency

<h2> Setter Syntax </h2>

Standard setter pattern:
```java
public class Motor {
    private double speed;
    private int deviceID;
    
    // Setter with validation
    public void setSpeed(double newSpeed) {
        // Validate input
        if (newSpeed >= -1.0 && newSpeed <= 1.0) {
            speed = newSpeed;
        } else {
            speed = 0.0;  // Default safe value
        }
    }
    
    // Simple setter
    public void setDeviceID(int id) {
        deviceID = id;
    }
}
```

<h2> Using Setters </h2>

Call setters to modify private fields:
```java
Motor motor = new Motor();
motor.setSpeed(0.75);
motor.setDeviceID(5);
```

<h2> Best Practices </h2>

- Always validate input in setters
- Use descriptive parameter names
- Consider what side effects should occur
- Don't always need both getter and setter for every field
