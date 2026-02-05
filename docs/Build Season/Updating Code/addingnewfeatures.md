<h1> Adding New Features </h1>

<h2> Feature Planning </h2>

Before coding, plan the feature:
- **Define requirements**: What should it do?
- **Design interface**: How will drivers use it?
- **Identify dependencies**: What subsystems/hardware needed?
- **Estimate complexity**: How long will it take?
- **Consider alternatives**: Is there a simpler approach?

<h2> Feature Development Process </h2>

**1. Create GitHub Issue**:
- Describe the feature
- List acceptance criteria
- Assign to team member
- Add labels and milestone

**2. Create Feature Branch**:
```bash
git checkout -b feature/new-auto-align
```

**3. Design Before Coding**:
- Sketch class structure
- Identify needed methods
- Plan command composition
- Discuss with team

**4. Implement Incrementally**:
- Start with simplest version
- Test frequently
- Add complexity gradually
- Keep commits small

**5. Test Thoroughly**:
- Unit test if possible
- Test on practice robot
- Verify edge cases
- Get driver feedback

**6. Code Review**:
- Create pull request
- Explain changes
- Address feedback
- Get approval

**7. Merge and Deploy**:
- Merge to main branch
- Deploy to robot
- Final testing
- Close issue

<h2> Adding New Subsystems </h2>

**Step 1: Create Subsystem Class**:
```java
public class ExampleSubsystem extends SubsystemBase {
    // Hardware declarations
    private final CANSparkMax motor;
    
    public ExampleSubsystem() {
        // Initialize hardware
        motor = new CANSparkMax(
            Constants.ExampleConstants.MOTOR_ID,
            MotorType.kBrushless
        );
        configureMotor();
    }
    
    private void configureMotor() {
        // Configuration
    }
    
    @Override
    public void periodic() {
        // Telemetry
    }
}
```

**Step 2: Add Constants**:
```java
public static final class ExampleConstants {
    public static final int MOTOR_ID = 10;
    public static final double MAX_SPEED = 1.0;
}
```

**Step 3: Create in RobotContainer**:
```java
private final ExampleSubsystem exampleSubsystem = new ExampleSubsystem();
```

**Step 4: Test Subsystem**:
- Deploy and verify hardware responds
- Check telemetry displays correctly
- Test basic operations

<h2> Adding New Commands </h2>

**Step 1: Create Command Class**:
```java
public class ExampleCommand extends CommandBase {
    private final ExampleSubsystem subsystem;
    
    public ExampleCommand(ExampleSubsystem subsystem) {
        this.subsystem = subsystem;
        addRequirements(subsystem);
    }
    
    @Override
    public void initialize() {
        // Setup
    }
    
    @Override
    public void execute() {
        // Main logic
    }
    
    @Override
    public void end(boolean interrupted) {
        // Cleanup
    }
    
    @Override
    public boolean isFinished() {
        return false;
    }
}
```

**Step 2: Bind to Controller**:
```java
driverController.a().onTrue(new ExampleCommand(exampleSubsystem));
```

**Step 3: Test Command**:
- Test button binding
- Verify command executes
- Check end behavior
- Test interruption

<h2> Adding Autonomous Features </h2>

**Create Auto Command**:
```java
public static Command newAuto(
        SwerveSubsystem swerve,
        ExampleSubsystem example) {
    return Commands.sequence(
        Commands.runOnce(() -> 
            swerve.resetOdometry(startPose)),
        followPath(swerve, "Path1"),
        new ExampleCommand(example),
        followPath(swerve, "Path2")
    );
}
```

**Add to Selector**:
```java
autoChooser.addOption("New Auto", Autos.newAuto(swerve, example));
```

<h2> Adding Vision Features </h2>

**Integration Steps**:
1. Configure Limelight pipeline
2. Create vision subsystem or add to existing
3. Add commands for vision-assisted operations
4. Test with AprilTags
5. Tune for accuracy and speed

**Example Vision Alignment**:
```java
public class AlignToTarget extends CommandBase {
    private final SwerveSubsystem swerve;
    private final PIDController rotController;
    
    public AlignToTarget(SwerveSubsystem swerve) {
        this.swerve = swerve;
        this.rotController = new PIDController(0.1, 0, 0);
        addRequirements(swerve);
    }
    
    @Override
    public void execute() {
        double tx = LimelightHelpers.getTX("limelight");
        double rotSpeed = rotController.calculate(tx, 0);
        swerve.drive(0, 0, rotSpeed, false);
    }
    
    @Override
    public boolean isFinished() {
        return Math.abs(LimelightHelpers.getTX("limelight")) < 2.0;
    }
}
```

<h2> Adding Safety Features </h2>

**Limit Switches**:
```java
public void setSpeed(double speed) {
    if (speed > 0 && upperLimitSwitch.get()) {
        speed = 0;  // Stop at upper limit
    }
    if (speed < 0 && lowerLimitSwitch.get()) {
        speed = 0;  // Stop at lower limit
    }
    motor.set(speed);
}
```

**Soft Limits**:
```java
public void setPosition(double targetPosition) {
    targetPosition = MathUtil.clamp(
        targetPosition,
        Constants.MIN_POSITION,
        Constants.MAX_POSITION
    );
    // Set position
}
```

**Current Monitoring**:
```java
@Override
public void periodic() {
    double current = motor.getOutputCurrent();
    if (current > Constants.MAX_CURRENT) {
        motor.set(0);
        System.err.println("Motor current limit exceeded!");
    }
}
```

<h2> Testing New Features </h2>

**Simulation Testing**:
- Test basic logic without hardware
- Verify command scheduling
- Check for exceptions

**Practice Robot Testing**:
- Test on practice robot first
- Verify hardware interactions
- Test edge cases

**Competition Robot Testing**:
- Test after verifying on practice bot
- Have someone watch closely
- Be ready to disable
- Test in safe conditions

<h2> Documenting New Features </h2>

**Code Comments**:
- Explain why, not just what
- Document assumptions
- Note limitations

**README Updates**:
- List new features added
- Explain how to use
- Document any configuration

**Driver Documentation**:
- Update control mapping
- Explain new button functions
- Note any behavior changes

<h2> Common Mistakes to Avoid </h2>

- Adding too many features at once
- Not testing incrementally
- Skipping code review
- Ignoring driver feedback
- Over-engineering solutions
- Not considering robot constraints
- Adding features too close to competition
- Forgetting to update documentation

<h2> Best Practices </h2>

- Start simple, add complexity as needed
- Test each feature independently
- Get driver feedback early
- Use version control properly
- Write self-documenting code
- Consider failure modes
- Plan for competition conditions
- Have disable/fallback options
