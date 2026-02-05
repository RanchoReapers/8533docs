<h1> SwerveJoystickCommand.java </h1>

<h2> What is SwerveJoystickCommand? </h2>

SwerveJoystickCommand is typically the default command for the SwerveSubsystem. It:
- Reads input from driver's controller
- Applies deadband and scaling to joystick inputs
- Converts joystick values to robot velocities
- Enables field-centric or robot-centric drive
- Handles drive speed limiting

<h2> Command Structure </h2>

```java
public class SwerveJoystickCommand extends CommandBase {
    private final SwerveSubsystem swerveSubsystem;
    private final Supplier<Double> xSpeedSupplier;
    private final Supplier<Double> ySpeedSupplier;
    private final Supplier<Double> rotSpeedSupplier;
    private final Supplier<Boolean> fieldCentricSupplier;
    
    public SwerveJoystickCommand(
            SwerveSubsystem swerveSubsystem,
            Supplier<Double> xSpeed,
            Supplier<Double> ySpeed,
            Supplier<Double> rotSpeed,
            Supplier<Boolean> fieldCentric) {
        
        this.swerveSubsystem = swerveSubsystem;
        this.xSpeedSupplier = xSpeed;
        this.ySpeedSupplier = ySpeed;
        this.rotSpeedSupplier = rotSpeed;
        this.fieldCentricSupplier = fieldCentric;
        
        addRequirements(swerveSubsystem);
    }
}
```

<h2> Execute Method </h2>

The execute() method:
1. Gets current joystick values from suppliers
2. Applies deadband to eliminate drift
3. Applies scaling curves for better control
4. Converts to field-centric if enabled
5. Passes velocities to swerve subsystem

<h2> Input Processing </h2>

**Deadband**:
- Ignores small joystick movements
- Prevents unintended robot movement
- Typical value: 0.05 to 0.1

**Scaling**:
- Square or cube inputs for finer control at low speeds
- Maintains sign (positive/negative direction)
- `scaled = Math.copySign(value * value, value)`

**Speed Limiting**:
- Multiply by max speed constants
- Allow slow mode for precise positioning
- Example: 50% speed for cargo alignment

<h2> Why Use Suppliers? </h2>

Suppliers (functional interfaces) allow:
- Late binding of joystick values
- Command reusability
- Easier testing and simulation
- Flexibility in input sources
