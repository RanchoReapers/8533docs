<h1> Constants.java </h1>

<h2> What is Constants.java? </h2>

Constants.java is a central file that stores all robot configuration values in one place. This includes:
- CAN IDs for motors and sensors
- Physical measurements (wheel diameter, track width)
- PID gains
- Speed limits
- Game-specific values

<h2> Why Use Constants.java? </h2>

Benefits of centralizing constants:
- **Easy to find and modify**: All values in one file
- **Prevents magic numbers**: Named constants explain meaning
- **Reduces errors**: Change once, affects everywhere
- **Type safety**: Compile-time checking
- **Version control**: Track configuration changes

<h2> Typical Structure </h2>

```java
public final class Constants {
    // Prevent instantiation
    private Constants() {}
    
    public static final class DriveConstants {
        public static final int FRONT_LEFT_DRIVE_ID = 1;
        public static final int FRONT_LEFT_TURN_ID = 2;
        
        public static final double WHEEL_DIAMETER_METERS = 0.1016;
        public static final double TRACK_WIDTH_METERS = 0.635;
        
        public static final double MAX_SPEED_MPS = 4.5;
        public static final double MAX_ANGULAR_SPEED = 2 * Math.PI;
    }
    
    public static final class IntakeConstants {
        public static final int MOTOR_ID = 10;
        public static final double INTAKE_SPEED = 0.75;
    }
    
    public static final class OIConstants {
        public static final int DRIVER_CONTROLLER_PORT = 0;
        public static final int OPERATOR_CONTROLLER_PORT = 1;
        public static final double DEADBAND = 0.1;
    }
}
```

<h2> Naming Conventions </h2>

Follow these conventions:
- Class name: `Constants` (plural)
- Use UPPER_SNAKE_CASE for constant names
- Group related constants in nested classes
- Use descriptive names that explain purpose
- Include units in names when applicable (SPEED_MPS, DISTANCE_METERS)

<h2> Accessing Constants </h2>

```java
motor.set(Constants.IntakeConstants.INTAKE_SPEED);
double maxSpeed = Constants.DriveConstants.MAX_SPEED_MPS;
```
