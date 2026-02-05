<h1> PID Tuning for Swerve Drive </h1>

<h2> What is PID Control? </h2>

PID (Proportional-Integral-Derivative) control is a feedback mechanism that continuously calculates an error value and applies a correction. For swerve drive, PID controllers are used for:
- Module steering (turning each wheel to desired angle)
- Module drive (controlling wheel velocity)
- Auto path following (X, Y, and rotation)

<h2> PID Components Explained </h2>

**Proportional (P)**:
- Correction proportional to current error
- Larger error = larger correction
- Can overshoot and oscillate

**Integral (I)**:
- Accumulates error over time
- Eliminates steady-state error
- Can cause windup problems

**Derivative (D)**:
- Responds to rate of error change
- Reduces overshoot
- Sensitive to noise

<h2> Tuning Process </h2>

**Start with All Zeros**:
```java
PIDController controller = new PIDController(0, 0, 0);
```

**Step 1: Tune P**:
1. Set I = 0, D = 0
2. Increase P gradually (start with 0.1, 0.5, 1.0, etc.)
3. Test response - looking for quick reaction
4. Stop when oscillation becomes consistent
5. Reduce P by 20-30% from oscillation point

**Step 2: Tune D**:
1. Keep P from Step 1, I = 0
2. Increase D gradually (usually 5-20x smaller than P)
3. Test response - should reduce overshoot
4. Stop when response is smooth without oscillation

**Step 3: Tune I (if needed)**:
1. Keep P and D from previous steps
2. Increase I very gradually (0.001, 0.01, 0.1)
3. Look for elimination of steady-state error
4. Watch for oscillation or instability
5. Often I = 0 works fine for swerve

<h2> Tuning Module Steering </h2>

**Goal**: Wheel turns to target angle quickly without overshoot.

**Typical Values**:
- P: 3.0 - 8.0
- I: 0.0 - 0.1
- D: 0.0 - 0.5

**Tuning Procedure**:
1. Disable drive motors (only tune steering)
2. Command module to rotate 90 degrees
3. Observe response time and oscillation
4. Adjust P for speed, D for smoothness
5. Repeat for different angle changes

**Testing**:
```java
// In module class or test command
public void testSteeringPID(double targetAngleDegrees) {
    setTargetAngle(targetAngleDegrees);
    // Observe how quickly and smoothly it reaches target
}
```

<h2> Tuning Module Drive </h2>

**Goal**: Wheel velocity matches commanded velocity.

**Typical Values**:
- P: 0.1 - 0.5
- I: 0.0
- D: 0.0 - 0.05
- FF: 0.1 - 0.3 (feedforward)

**Tuning Procedure**:
1. Use velocity control mode on SPARK MAX
2. Command various speeds
3. Monitor actual vs target velocity
4. Adjust P for tracking
5. Add FF to reduce steady-state error

**Feedforward**:
```java
// Simple feedforward
double ffOutput = targetVelocity * kF;
double pidOutput = pidController.calculate(currentVelocity, targetVelocity);
double output = ffOutput + pidOutput;
```

<h2> Tuning Path Following </h2>

**Holonomic (X, Y, Rotation) Controllers**:

Each has its own PID controller:

**Translation Controllers (X and Y)**:
- P: 3.0 - 8.0
- I: 0.0 - 0.5
- D: 0.0 - 0.5

**Rotation Controller (Theta)**:
- P: 2.0 - 6.0
- I: 0.0
- D: 0.0 - 0.3

**Tuning Process**:
1. Create simple test path (straight line)
2. Deploy and run autonomous
3. Log actual vs target positions
4. Tune X and Y together first
5. Then tune rotation separately

<h2> Measuring PID Performance </h2>

**What to Monitor**:
- Settling time (how long to reach target)
- Overshoot (how much beyond target)
- Steady-state error (final error)
- Oscillation (constant back-and-forth)
- Rise time (initial response speed)

**Logging for Analysis**:
```java
@Override
public void periodic() {
    SmartDashboard.putNumber("Target Angle", targetAngle);
    SmartDashboard.putNumber("Current Angle", getCurrentAngle());
    SmartDashboard.putNumber("Error", targetAngle - getCurrentAngle());
    SmartDashboard.putNumber("PID Output", pidController.calculate(...));
}
```

<h2> Common PID Issues </h2>

**Oscillation**:
- P too high - reduce P
- D too low - increase D
- Check for mechanical slop

**Slow Response**:
- P too low - increase P
- Check for friction/binding
- Verify max output not limiting

**Never Reaches Target**:
- Add I term (carefully)
- Check for mechanical issues
- Verify sensor accuracy

**Overshoots Target**:
- P too high - reduce P
- D too low - increase D
- Add rate limiting

**Integral Windup**:
- Limit integral accumulation
- Reset integral when far from target
- Use integral zone

<h2> Advanced PID Techniques </h2>

**Integral Zone**:
```java
if (Math.abs(error) < INTEGRAL_ZONE) {
    integral += error;
} else {
    integral = 0;
}
```

**Output Limiting**:
```java
double output = MathUtil.clamp(pidOutput, -maxOutput, maxOutput);
```

**Derivative Filtering**:
```java
// Use filtered derivative to reduce noise
filteredDerivative = 0.8 * filteredDerivative + 0.2 * rawDerivative;
```

<h2> Testing Best Practices </h2>

- Tune one controller at a time
- Make small adjustments
- Test with different commands
- Record values that work
- Test under match conditions
- Have robot safely suspended or limited space
- Be ready to disable quickly
- Document final values in Constants.java

<h2> Tools for Tuning </h2>

**REV Hardware Client**:
- Tune SPARK MAX PID directly
- Real-time plotting
- Quick iteration

**SmartDashboard/Shuffleboard**:
- Display PID values
- Live tuning without redeploying
- Graph error and output

**Advantage Kit/DataLog**:
- Record PID performance
- Analyze after the fact
- Compare different tunings

<h2> Final PID Values Documentation </h2>

Document final tuned values:
```java
public static final class ModuleConstants {
    // Steering PID
    public static final double STEERING_P = 5.0;
    public static final double STEERING_I = 0.0;
    public static final double STEERING_D = 0.1;
    
    // Drive PID
    public static final double DRIVE_P = 0.2;
    public static final double DRIVE_I = 0.0;
    public static final double DRIVE_D = 0.0;
    public static final double DRIVE_FF = 0.25;
}
```

Save these values in Constants.java and commit to version control!
