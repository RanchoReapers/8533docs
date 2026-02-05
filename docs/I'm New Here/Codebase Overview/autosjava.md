<h1> Autos.java </h1>

<h2> What is Autos.java? </h2>

Autos.java is a utility class that organizes and creates autonomous routines. It typically:
- Imports trajectories from Choreo or PathPlanner
- Creates auto command groups
- Provides methods for RobotContainer to access autos
- Defines named commands for path following

<h2> Typical Structure </h2>

```java
public class Autos {
    // Private constructor - only static methods
    private Autos() {}
    
    // Create autonomous commands
    public static Command exampleAuto(SwerveSubsystem swerve, IntakeSubsystem intake) {
        return Commands.sequence(
            // Reset odometry to starting position
            Commands.runOnce(() -> swerve.resetOdometry(startingPose)),
            
            // Follow path
            followChoreoPath(swerve, "ExamplePath"),
            
            // Run intake
            new IntakeCommand(intake).withTimeout(2.0),
            
            // Follow another path
            followChoreoPath(swerve, "ReturnPath")
        );
    }
    
    // Helper method for Choreo paths
    private static Command followChoreoPath(SwerveSubsystem swerve, String pathName) {
        ChoreoTrajectory traj = Choreo.getTrajectory(pathName);
        return Choreo.choreoSwerveCommand(
            traj,
            swerve::getPose,
            // PID controllers
            new PIDController(5.0, 0.0, 0.0),  // X
            new PIDController(5.0, 0.0, 0.0),  // Y
            new PIDController(3.0, 0.0, 0.0),  // Rotation
            swerve::setModuleStates,
            swerve
        );
    }
}
```

<h2> Organizing Autonomous Routines </h2>

**Simple Autos**:
- Single path following
- Basic sequences (drive, shoot, drive back)

**Complex Autos**:
- Multiple paths
- Parallel command groups (intake while driving)
- Conditional logic (if see target, then...)
- Dynamic path selection

<h2> Integration with Choreo </h2>

Choreo trajectories are loaded by name:
```java
ChoreoTrajectory trajectory = Choreo.getTrajectory("FourNoteAuto");
```

Path files are stored in `src/main/deploy/choreo/` directory.

<h2> Named Commands </h2>

For PathPlanner integration, register named commands:
```java
NamedCommands.registerCommand("Intake", new IntakeCommand(intake));
NamedCommands.registerCommand("Shoot", new ShootCommand(shooter));
```

These can be triggered at waypoints in paths.

<h2> SendableChooser Integration </h2>

In RobotContainer, create a chooser:
```java
private final SendableChooser<Command> autoChooser = new SendableChooser<>();

autoChooser.setDefaultOption("Do Nothing", Commands.none());
autoChooser.addOption("Simple Auto", Autos.simpleAuto(swerve));
autoChooser.addOption("4 Note Auto", Autos.fourNoteAuto(swerve, intake, shooter));

SmartDashboard.putData("Auto Chooser", autoChooser);
```

<h2> Testing Autos </h2>

- Use simulation to verify paths
- Test odometry reset at start
- Verify end positions match expectations
- Practice mode for timing validation
- Log trajectory following errors
