<h1> Tuning Swerve Drive Systems </h1>

<h2> What is Swerve Tuning? </h2>

Swerve drive tuning is the process of optimizing your swerve drive system for best performance. This includes:
- Calibrating absolute encoder offsets
- Tuning PID controllers
- Characterizing drive motors
- Optimizing motion profiles
- Testing and validating performance

<h2> Tuning Overview </h2>

The complete swerve tuning process involves several steps performed in order:

**1. Module Calibration**:
- Align modules to zero position
- Record CANCoder absolute positions
- Calculate and apply offsets
- Verify physical alignment

**2. PID Tuning**:
- Tune steering PID (module angle control)
- Tune drive PID (wheel velocity control)
- Tune holonomic PID (path following X, Y, theta)

**3. Drive Characterization**:
- Measure feedforward gains
- Test maximum velocities and accelerations
- Validate against theoretical calculations

**4. Path Following Optimization**:
- Test simple autonomous paths
- Tune trajectory following parameters
- Optimize look-ahead and correction gains

**5. Field Testing**:
- Test under realistic conditions
- Verify odometry accuracy
- Validate autonomous performance
- Make final adjustments

<h2> Required Tools and Setup </h2>

**Hardware**:
- Fully assembled swerve robot
- Charged battery
- Laptop with driver station
- Measuring tape or field markers
- Blocks or lift to suspend robot (for some tests)

**Software**:
- Latest robot code deployed
- Dashboard (Shuffleboard, Elastic, etc.)
- Phoenix Tuner X (for CANCoders)
- REV Hardware Client (for SPARK MAXes)

<h2> Safety First </h2>

During tuning:
- Keep robot in safe area with space to move
- Have emergency stop ready
- Start with low speeds
- Gradually increase as confidence grows
- Never tune with robot near people or fragile items
- Be ready to disable immediately

<h2> Recommended Tuning Order </h2>

**Week 1-2 (Basic Function)**:
1. Module calibration (offsets)
2. Basic steering PID
3. Basic drive control
4. Test teleoperated drive

**Week 3-4 (Optimization)**:
1. Fine-tune steering PID
2. Tune drive velocity PID
3. Drive characterization
4. Simple autonomous paths

**Week 5-6 (Path Following)**:
1. Tune holonomic PID for path following
2. Test autonomous routines
3. Optimize trajectory generation
4. Field testing

**Week 7-8 (Competition Ready)**:
1. Final validation and testing
2. Competition-specific tuning
3. Backup configurations
4. Driver practice

<h2> Documentation During Tuning </h2>

Keep a tuning log:
- Date and who performed tuning
- What was changed
- Before and after values
- Test results
- Issues encountered
- Final working values

Update Constants.java with final values:
```java
public static final class ModuleConstants {
    // Offsets (date calibrated: 2025-01-15)
    public static final double FL_OFFSET = 0.237;
    
    // Steering PID (tuned: 2025-01-18)
    public static final double STEERING_P = 5.0;
    public static final double STEERING_I = 0.0;
    public static final double STEERING_D = 0.1;
    
    // Drive PID (tuned: 2025-01-20)
    public static final double DRIVE_P = 0.2;
    // ...
}
```

<h2> Common Issues and Solutions </h2>

**Robot doesn't drive straight**:
- Check module offsets
- Verify motor inversions
- Check wheel tread condition
- Verify module positions in code

**Modules oscillate**:
- Reduce steering P gain
- Increase steering D gain
- Check for mechanical binding
- Verify CANCoder magnet alignment

**Poor path following**:
- Tune holonomic PID
- Check odometry accuracy
- Verify gyro not drifting
- Reduce maximum velocities

**Inconsistent performance**:
- Check battery voltage
- Verify current limits
- Test on charged battery
- Check for loose connections

<h2> Performance Validation </h2>

After tuning, validate performance:
- Drive test: Smooth, responsive control
- Straight line: < 5cm deviation over 5m
- Rotation: < 2° error in 360° rotation
- Path following: < 10cm error on complex paths
- Repeatability: Consistent performance over multiple runs

<h2> Resources </h2>

See detailed guides:
- PID Tuning (pidtuning.md)
- Testing and Calibration (testingcalibration.md)
- WPILib Swerve Documentation
- Team 364 Swerve Code (BaseFalconSwerve)
- Chief Delphi tuning discussions
