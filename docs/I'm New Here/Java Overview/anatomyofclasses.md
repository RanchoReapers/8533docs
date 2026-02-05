<h1> Anatomy of Classes </h1>

<h2> What is a Class? </h2>

A class is a blueprint for creating objects. It defines:
- **Fields** (variables): Data the class stores
- **Methods** (functions): Behaviors the class can perform
- **Constructors**: Special methods for creating instances

<h2> Class Structure </h2>

Basic class anatomy:
```java
public class Motor {
    // Fields (instance variables)
    private double speed;
    private int deviceID;
    
    // Constructor
    public Motor(int id) {
        this.deviceID = id;
        this.speed = 0.0;
    }
    
    // Methods
    public void setSpeed(double newSpeed) {
        this.speed = newSpeed;
    }
    
    public double getSpeed() {
        return this.speed;
    }
}
```

<h2> Access Modifiers </h2>

Control visibility of class members:
- **public**: Accessible from anywhere
- **private**: Only accessible within the class
- **protected**: Accessible within package and subclasses
- **default** (no modifier): Accessible within package

<h2> Instance vs Static Members </h2>

- **Instance members**: Belong to each object instance
- **Static members**: Belong to the class itself, shared by all instances
```java
public static final double MAX_SPEED = 1.0;  // Static constant
private double currentSpeed;                  // Instance variable
```
