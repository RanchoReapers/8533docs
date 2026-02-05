<h1> Breaking Down Commands </h1>

<h2> Command Structure </h2>

A typical command class has this structure:
```java
public class ExampleCommand extends CommandBase {
    private final ExampleSubsystem subsystem;
    
    public ExampleCommand(ExampleSubsystem subsystem) {
        this.subsystem = subsystem;
        addRequirements(subsystem);  // Claim the subsystem
    }
    
    @Override
    public void initialize() {
        // Setup code
    }
    
    @Override
    public void execute() {
        // Repeated action code
    }
    
    @Override
    public void end(boolean interrupted) {
        // Cleanup code
    }
    
    @Override
    public boolean isFinished() {
        // Return true when command should stop
        return false;
    }
}
```

<h2> Command Types </h2>

**Instant Commands**:
- Complete immediately (one-time actions)
- Example: Toggling a solenoid

**Run Commands**:
- Execute continuously until interrupted
- Example: Driving with joysticks

**Timed Commands**:
- Run for a specific duration
- Example: Run intake for 2 seconds

**Sequential/Parallel Command Groups**:
- Combine multiple commands
- Example: Drive forward, then turn, then shoot

<h2> Key Methods Explained </h2>

**initialize()**:
- Set initial states
- Reset variables
- Start timers

**execute()**:
- Called 50 times per second
- Implement main command logic
- Update subsystem outputs

**isFinished()**:
- Return true to end command
- Check sensors, timers, or conditions
- Always returns false for infinite commands

**end(interrupted)**:
- Stop motors
- Reset states
- Handle both normal and interrupted endings
