<h1> Refactoring Code </h1>

<h2> What is Refactoring? </h2>

Refactoring is restructuring existing code without changing its external behavior. The goals are to:
- Improve code readability
- Reduce complexity
- Eliminate duplication
- Make code easier to maintain
- Prepare for new features

**Important**: Refactoring is NOT adding features or fixing bugs. It's improving the code structure.

<h2> When to Refactor </h2>

Good times to refactor:
- After getting last year's code working
- Before adding major new features
- When code becomes hard to understand
- When finding duplicated code
- When tests are passing

**Don't refactor**:
- Right before competition
- When code is unstable
- Without tests or backup
- When you don't understand the code

<h2> Common Refactoring Patterns </h2>

**Extract Method**:
Replace duplicated or complex code with a method:
```java
// Before
double xSpeed = -driverController.getLeftY();
xSpeed = Math.abs(xSpeed) < 0.1 ? 0 : xSpeed;
xSpeed = Math.copySign(xSpeed * xSpeed, xSpeed);

// After
double xSpeed = processJoystickInput(-driverController.getLeftY());

private double processJoystickInput(double value) {
    value = Math.abs(value) < 0.1 ? 0 : value;  // Deadband
    return Math.copySign(value * value, value);  // Square input
}
```

**Rename Variables/Methods**:
Use descriptive names:
```java
// Before
double m = motor.get();
double v = 5.0;

// After
double motorOutput = motor.get();
double maxVelocityMPS = 5.0;
```

**Extract Constants**:
Replace magic numbers:
```java
// Before
if (speed > 0.8) { ... }

// After
private static final double MAX_SAFE_SPEED = 0.8;
if (speed > MAX_SAFE_SPEED) { ... }
```

**Consolidate Duplicate Code**:
```java
// Before
frontLeft.setSpeed(0.5);
frontRight.setSpeed(0.5);
rearLeft.setSpeed(0.5);
rearRight.setSpeed(0.5);

// After
setAllModuleSpeeds(0.5);

private void setAllModuleSpeeds(double speed) {
    for (SwerveModule module : modules) {
        module.setSpeed(speed);
    }
}
```

**Simplify Conditionals**:
```java
// Before
if (isEnabled == true && hasTarget == true && inRange == true) { ... }

// After
if (isEnabled && hasTarget && inRange) { ... }

// Even better
if (canShoot()) { ... }

private boolean canShoot() {
    return isEnabled && hasTarget && inRange;
}
```

<h2> Refactoring Subsystems </h2>

**Improve Organization**:
- Group related methods together
- Separate hardware initialization
- Extract complex logic to helper methods
- Add clear section comments

**Reduce Coupling**:
- Avoid accessing other subsystems directly
- Use commands to coordinate subsystems
- Pass required objects as parameters
- Use interfaces for flexibility

**Improve Encapsulation**:
- Make fields private
- Provide getters/setters only as needed
- Hide implementation details
- Expose simple, clear methods

<h2> Refactoring Commands </h2>

**Command Composition**:
Replace complex commands with composed ones:
```java
// Instead of one monolithic command
public class ComplexAutoCommand extends CommandBase {
    // 200 lines of sequential logic
}

// Use composition
public static Command complexAuto(subsystems...) {
    return Commands.sequence(
        new DriveToPosition(swerve, position1),
        new IntakeGamePiece(intake),
        new DriveToPosition(swerve, position2),
        new ScoreGamePiece(scorer)
    );
}
```

**Extract Reusable Commands**:
- Create small, focused commands
- Make them reusable across autos
- Use command decorators (withTimeout, andThen, etc.)

<h2> Refactoring RobotContainer </h2>

**Extract Configuration Methods**:
```java
// Instead of giant constructor
public RobotContainer() {
    initializeSubsystems();
    configureDefaultCommands();
    configureButtonBindings();
    configureAutonomousSelector();
}
```

**Group Related Bindings**:
```java
private void configureDriverControls() {
    // All driver controller bindings
}

private void configureOperatorControls() {
    // All operator controller bindings
}
```

<h2> Refactoring Constants </h2>

**Organize by Category**:
```java
public static final class DriveConstants {
    // All drive-related constants
}

public static final class IntakeConstants {
    // All intake-related constants
}
```

**Calculate Related Constants**:
```java
public static final double WHEEL_DIAMETER_METERS = 0.1016;
public static final double WHEEL_CIRCUMFERENCE_METERS = 
    WHEEL_DIAMETER_METERS * Math.PI;
```

<h2> Safe Refactoring Process </h2>

**1. Ensure Tests Pass** (or code works):
- Test functionality before refactoring
- Document current behavior

**2. Make Small Changes**:
- One refactoring at a time
- Commit after each successful change

**3. Test After Each Change**:
- Verify behavior unchanged
- Run on robot if possible

**4. Use IDE Tools**:
- Automated refactoring tools (rename, extract method)
- Less error-prone than manual
- Faster and safer

**5. Get Code Review**:
- Have teammate review changes
- Explain improvements made
- Ensure clarity improved

<h2> IDE Refactoring Tools (VS Code)</h2>

**Rename**:
- Right-click variable/method
- Select "Rename Symbol"
- Updates all references

**Extract Method**:
- Select code block
- Right-click -> "Refactor"
- Choose "Extract to method"

**Extract Variable**:
- Select expression
- Right-click -> "Refactor"
- Choose "Extract to constant"

<h2> Red Flags to Refactor </h2>

Watch for these code smells:
- Methods longer than 30-40 lines
- Deeply nested conditionals (>3 levels)
- Duplicated code
- Unclear variable names (x, temp, data)
- Many parameters (>4)
- Large classes (>500 lines)
- Commented-out code

<h2> When Not to Refactor </h2>

Avoid refactoring when:
- Code works and no one needs to modify it
- You don't understand what it does
- No tests or way to verify
- Right before competition
- Working on critical bugs
- Time is limited

<h2> Best Practices </h2>

- Refactor continuously, not all at once
- Test after each refactoring
- Use version control (easy to revert)
- Focus on readability
- Don't over-engineer
- Keep it simple
- Get feedback from team
- Document why, not just what
