<h1> Testing and Calibrating Swerve Modules </h1>

<h2> Why Calibrate Swerve Modules? </h2>

Each swerve module needs calibration to:
- Establish absolute zero position for steering
- Ensure wheels point in correct directions
- Account for mechanical variations between modules
- Enable accurate odometry and path following

Without proper calibration, the robot will drive incorrectly and autonomous will fail.

<h2> Understanding Absolute Encoders </h2>

CANCoders are absolute encoders:
- Report position from 0-360 degrees (or 0-1 rotation)
- Position maintained through power cycles
- Each module's "zero" is at a different absolute position
- We use offsets to align all modules to same reference

<h2> Calibration Procedure </h2>

**Step 1: Physical Alignment**:
1. Place robot on blocks or with wheels off ground
2. Manually rotate each module to "zero position"
   - Wheel bevel gears facing inward (toward robot center)
   - Or all wheels pointing forward (parallel to robot length)
3. Lock modules in this position (or have helper hold)

**Step 2: Read Absolute Positions**:
For each module, read the CANCoder position:

```java
// In module class or test code
public double getAbsolutePosition() {
    return canCoder.getAbsolutePosition();  // Returns 0-1 rotation
}
```

Or use Phoenix Tuner X:
1. Connect to robot
2. Select each CANCoder
3. Note "Absolute Position" value
4. Record for each module

**Step 3: Calculate Offsets**:
The offset is the reading when module is at zero:

```java
// If module reads 0.237 when physically at zero
public static final double FRONT_LEFT_OFFSET = 0.237;
```

Convert to degrees if needed:
```java
double offsetDegrees = offsetRotations * 360.0;
```

**Step 4: Apply Offsets in Code**:
```java
public class SwerveModule {
    private final CANCoder canCoder;
    private final double offset;
    
    public SwerveModule(..., double offset) {
        this.offset = offset;
        // ...
    }
    
    public double getAngle() {
        // Get position and subtract offset
        double position = canCoder.getAbsolutePosition();
        return (position - offset) * 360.0;  // Convert to degrees
    }
}
```

**Step 5: Verify Calibration**:
1. Deploy updated code
2. Manually rotate modules to zero position
3. Check that getAngle() reports close to 0°
4. Repeat for all modules
5. Test drive - robot should drive straight

<h2> Testing Module Operation </h2>

**Individual Module Test**:
Create a test command that exercises one module:

```java
public class TestSwerveModule extends CommandBase {
    private final SwerveModule module;
    private final int testNumber;
    
    @Override
    public void initialize() {
        testNumber = 0;
    }
    
    @Override
    public void execute() {
        switch (testNumber) {
            case 0:
                module.setState(new SwerveModuleState(0.5, Rotation2d.fromDegrees(0)));
                break;
            case 1:
                module.setState(new SwerveModuleState(0.5, Rotation2d.fromDegrees(90)));
                break;
            case 2:
                module.setState(new SwerveModuleState(0.5, Rotation2d.fromDegrees(180)));
                break;
            case 3:
                module.setState(new SwerveModuleState(0.5, Rotation2d.fromDegrees(270)));
                break;
        }
    }
}
```

**All Modules Test**:
Test all modules together:
1. Command 0° - all wheels forward
2. Command 90° - all wheels left
3. Command 180° - all wheels backward
4. Command 270° - all wheels right

**Verify**:
- All modules rotate to correct angle
- Wheel direction matches commanded direction
- No excessive delay or oscillation
- Modules return to same position repeatedly

<h2> Drive Direction Testing </h2>

**Test Forward Drive**:
```java
// All modules at 0°, positive speed
swerveSubsystem.drive(0.3, 0, 0, false);
```
- Robot should drive straight forward
- If drifts, check module steering offsets
- If drives wrong direction, check motor inversions

**Test Strafe**:
```java
// Test left strafe
swerveSubsystem.drive(0, 0.3, 0, false);
```
- Robot should strafe left
- Wheels should point 90° left
- Check coordination between modules

**Test Rotation**:
```java
// Test counter-clockwise rotation
swerveSubsystem.drive(0, 0, 0.3, false);
```
- Robot should spin in place
- All wheels should point tangent to circle
- Check module positions and inversions

<h2> Odometry Verification </h2>

After calibration, test odometry accuracy:

**Straight Line Test**:
1. Place robot at known position
2. Reset odometry to (0, 0)
3. Drive straight for measured distance (e.g., 3 meters)
4. Check odometry reports close to expected distance
5. Error should be < 5%

**Square Pattern Test**:
1. Reset odometry
2. Drive square pattern (1m each side)
3. Return to start
4. Check if odometry returns close to (0, 0)
5. Measure drift over time

**Rotation Test**:
1. Reset odometry heading
2. Rotate 360° (one full rotation)
3. Check heading returns close to 0°
4. Verify gyro integration with encoders

<h2> Common Calibration Issues </h2>

**Robot Drives in Wrong Direction**:
- Check motor inversions
- Verify module position configuration
- Check drive encoder phase

**Modules Don't Align Correctly**:
- Recheck offsets
- Verify CANCoder wiring and configuration
- Check for mechanical slop

**Inconsistent Module Angles**:
- Check CANCoder magnet alignment (should be green LED)
- Verify no interference with encoder
- Check for loose mounting

**Odometry Drifts Over Time**:
- Wheel slippage (use proper wheels for surface)
- Incorrect wheel radius in constants
- Module positions incorrect
- Gyro drift (verify NavX calibration)

<h2> Field-Centric Drive Test </h2>

After calibration, test field-centric drive:
1. Enable field-centric mode
2. Rotate robot 90° clockwise
3. Push joystick forward
4. Robot should still drive toward the front of the field
5. Verify gyro integration working

<h2> Autonomous Path Test </h2>

Final calibration test with autonomous:
1. Create simple straight-line path
2. Place robot at starting position
3. Reset odometry
4. Run autonomous
5. Measure actual vs expected end position
6. Iterate on calibration if needed

<h2> Maintenance and Recalibration </h2>

Recalibrate when:
- Changing swerve module components
- CANCoder gets bumped or remounted
- After significant impact/damage
- Odometry becomes inaccurate
- Before major competitions

<h2> Documentation </h2>

Document your calibration:
```java
// ModuleConstants.java
public static final double FL_OFFSET = 0.237;  // Measured 2025-01-15
public static final double FR_OFFSET = 0.891;  // Measured 2025-01-15  
public static final double RL_OFFSET = 0.445;  // Measured 2025-01-15
public static final double RR_OFFSET = 0.672;  // Measured 2025-01-15
```

Keep a calibration log:
- Date calibrated
- Who performed calibration
- What changes were made
- Test results
