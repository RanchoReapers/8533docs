<h1> RobotContainer.java </h1>

<h2> What is RobotContainer? </h2>

RobotContainer is where the bulk of your robot's structure is defined. It:
- Creates all subsystems
- Creates controllers and buttons
- Binds commands to buttons
- Defines autonomous routines
- Configures default commands

This keeps Robot.java clean and organizes robot configuration in one place.

<h2> Typical Structure </h2>

```java
public class RobotContainer {
    // Subsystems
    private final SwerveSubsystem swerveSubsystem;
    private final IntakeSubsystem intakeSubsystem;
    private final ShooterSubsystem shooterSubsystem;
    
    // Controllers
    private final CommandXboxController driverController;
    private final CommandXboxController operatorController;
    
    // Constructor
    public RobotContainer() {
        // Create subsystems
        swerveSubsystem = new SwerveSubsystem();
        intakeSubsystem = new IntakeSubsystem();
        shooterSubsystem = new ShooterSubsystem();
        
        // Create controllers
        driverController = new CommandXboxController(Constants.DRIVER_PORT);
        operatorController = new CommandXboxController(Constants.OPERATOR_PORT);
        
        // Configure button bindings
        configureButtonBindings();
        
        // Set default commands
        configureDefaultCommands();
    }
    
    public Command getAutonomousCommand() {
        return autoChooser.getSelected();
    }
}
```

<h2> Key Methods </h2>

**configureButtonBindings()**:
- Binds commands to controller buttons
- Uses CommandXboxController for trigger-based binding
```java
private void configureButtonBindings() {
    driverController.a().onTrue(new IntakeCommand(intakeSubsystem));
    driverController.b().onTrue(new ShootCommand(shooterSubsystem));
    operatorController.rightBumper().whileTrue(new OuttakeCommand(intakeSubsystem));
}
```

**configureDefaultCommands()**:
- Sets commands that run when subsystem is not being used
```java
private void configureDefaultCommands() {
    swerveSubsystem.setDefaultCommand(
        new SwerveJoystickCommand(
            swerveSubsystem,
            () -> -driverController.getLeftY(),
            () -> -driverController.getLeftX(),
            () -> -driverController.getRightX(),
            () -> true  // Field-centric
        )
    );
}
```

**getAutonomousCommand()**:
- Returns the selected autonomous command
- Often uses SendableChooser for dashboard selection

<h2> Organization Tips </h2>

- Group related subsystem creation
- Use descriptive variable names
- Comment complex button binding logic
- Consider splitting very large RobotContainer into multiple classes
