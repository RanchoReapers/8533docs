<h1> Robot.java </h1>

<h2> What is Robot.java? </h2>

Robot.java is the main entry point of your robot code. It extends `TimedRobot` and contains methods that are called automatically at different stages of robot operation.

<h2> Robot Lifecycle Methods </h2>

**robotInit()**:
- Called once when robot code starts
- Typically creates RobotContainer
- Initializes any global systems
```java
@Override
public void robotInit() {
    robotContainer = new RobotContainer();
}
```

**robotPeriodic()**:
- Called every 20ms (50Hz) regardless of mode
- Runs CommandScheduler
- Updates dashboards
```java
@Override
public void robotPeriodic() {
    CommandScheduler.getInstance().run();
}
```

<h2> Mode-Specific Methods </h2>

**Disabled Mode**:
```java
@Override
public void disabledInit() {
    // Called when robot is disabled
}

@Override
public void disabledPeriodic() {
    // Called periodically while disabled
}
```

**Autonomous Mode**:
```java
@Override
public void autonomousInit() {
    // Get and schedule autonomous command
    autonomousCommand = robotContainer.getAutonomousCommand();
    if (autonomousCommand != null) {
        autonomousCommand.schedule();
    }
}

@Override
public void autonomousPeriodic() {
    // No code needed - CommandScheduler handles it
}
```

**Teleop Mode**:
```java
@Override
public void teleopInit() {
    // Cancel autonomous command when teleop starts
    if (autonomousCommand != null) {
        autonomousCommand.cancel();
    }
}

@Override
public void teleopPeriodic() {
    // No code needed - CommandScheduler handles it
}
```

**Test Mode**:
```java
@Override
public void testInit() {
    CommandScheduler.getInstance().cancelAll();
}

@Override
public void testPeriodic() {
    // Used for testing specific subsystems
}
```

<h2> Best Practices </h2>

- Keep Robot.java minimal - put logic in RobotContainer
- Always run CommandScheduler in robotPeriodic()
- Don't create subsystems in Robot.java
- Use mode init methods for mode-specific setup
