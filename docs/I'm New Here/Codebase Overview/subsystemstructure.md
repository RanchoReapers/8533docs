<h1> Breaking Down Subsystems </h1>

<h2> Subsystem Structure </h2>

A typical subsystem class structure:
```java
public class ExampleSubsystem extends SubsystemBase {
    // Hardware components
    private final CANSparkMax motor;
    private final Encoder encoder;
    
    // Constructor - initialize hardware
    public ExampleSubsystem() {
        motor = new CANSparkMax(Constants.MOTOR_ID, MotorType.kBrushless);
        encoder = motor.getEncoder();
        
        // Configure hardware
        motor.setIdleMode(IdleMode.kBrake);
        motor.setSmartCurrentLimit(40);
    }
    
    // Methods to control the subsystem
    public void setSpeed(double speed) {
        motor.set(speed);
    }
    
    public double getPosition() {
        return encoder.getPosition();
    }
    
    // Periodic runs 50 times per second
    @Override
    public void periodic() {
        // Update telemetry, safety checks, etc.
        SmartDashboard.putNumber("Motor Speed", motor.get());
    }
}
```

<h2> Subsystem Responsibilities </h2>

Subsystems should:
- **Own hardware**: Create and configure motor controllers, sensors
- **Provide control methods**: Simple, reusable operations
- **Handle safety**: Limit checks, fault detection
- **Publish telemetry**: Send data to dashboard
- **Maintain state**: Track mechanism position/status

<h2> Important Methods </h2>

**Constructor**:
- Initialize hardware objects
- Configure device settings
- Set default values

**periodic()**:
- Called automatically 50 times per second
- Update telemetry
- Safety monitoring
- State machine updates

**Control Methods**:
- Simple operations (setSpeed, getPosition)
- Keep logic in commands when possible
- Return useful information

<h2> Default Commands </h2>

Subsystems can have a default command that runs when no other command requires them:
```java
setDefaultCommand(new DefaultDriveCommand(this));
```
Common default commands:
- Drivetrain: Joystick control
- Arm: Hold position
- Intake: Do nothing (motors off)
