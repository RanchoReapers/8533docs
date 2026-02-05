<h1> Command Based Programming </h1>

<h2> What is Command Based Programming? </h2>

Command Based Programming is the official WPILib framework for organizing robot code. It structures your code around two main concepts:
- **Subsystems**: Represent robot mechanisms (drivetrain, arm, intake)
- **Commands**: Represent actions the robot can perform

<h2> Why Use Command Based? </h2>

Benefits of the framework:
- Clear separation of mechanism control (subsystems) and behavior (commands)
- Automatic handling of resource conflicts (one command per subsystem)
- Built-in support for sequential and parallel command groups
- Easier testing and debugging
- Standard structure across FRC teams
- Integration with FRC tools (PathPlanner, Choreo, etc.)

<h2> Core Concepts </h2>

**Subsystems**:
- Own hardware components (motors, sensors)
- Define low-level operations
- Have default commands that run when no other command is using them
- Example: DrivetrainSubsystem, IntakeSubsystem

**Commands**:
- Define high-level robot behaviors
- Require specific subsystems
- Have lifecycle methods (initialize, execute, end, isFinished)
- Can be bound to buttons or triggers
- Example: DriveWithJoystick, ShootGamePiece

<h2> Command Lifecycle </h2>

Commands follow this lifecycle:
1. **initialize()**: Called once when command starts
2. **execute()**: Called repeatedly while command runs (50Hz)
3. **isFinished()**: Returns true when command should end
4. **end(interrupted)**: Called once when command ends

<h2> CommandScheduler </h2>

The CommandScheduler:
- Runs during robot periodic methods
- Manages which commands are active
- Handles subsystem requirements
- Cancels conflicting commands automatically
