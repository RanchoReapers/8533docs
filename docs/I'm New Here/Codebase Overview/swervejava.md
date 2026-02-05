<h1> SwerveSubsystem.java </h1>

<h2> What is SwerveSubsystem? </h2>

SwerveSubsystem is the main subsystem that controls the swerve drive system. It manages:
- Four swerve modules (one per wheel)
- Odometry (tracking robot position on field)
- Gyroscope for heading
- Field-centric drive control
- Integration with PathPlanner/Choreo for autonomous

<h2> Key Components </h2>

The SwerveSubsystem typically includes:
```java
public class SwerveSubsystem extends SubsystemBase {
    // Swerve modules
    private final SwerveModule frontLeft;
    private final SwerveModule frontRight;
    private final SwerveModule rearLeft;
    private final SwerveModule rearRight;
    
    // Gyroscope for robot heading
    private final Gyro gyro;
    
    // Odometry for position tracking
    private final SwerveDriveOdometry odometry;
    
    // Kinematics for coordinate conversions
    private final SwerveDriveKinematics kinematics;
}
```

<h2> Core Methods </h2>

**drive()**:
- Takes desired velocities (vx, vy, omega)
- Converts to module states using kinematics
- Commands each module to desired state

**periodic()**:
- Updates odometry with current module states
- Publishes telemetry (position, heading, speeds)
- Safety monitoring

**resetOdometry()**:
- Sets robot's known position on field
- Called at start of autonomous

**getPosition()**:
- Returns current robot pose (x, y, rotation)
- Used by PathPlanner and pose estimation

<h2> Swerve Drive Modes </h2>

**Robot-Centric**:
- Forward is always robot's forward direction
- Simpler for beginners

**Field-Centric**:
- Forward is always away from driver
- Uses gyro to adjust for robot rotation
- Preferred for competition driving

<h2> Integration with Autonomous </h2>

The SwerveSubsystem integrates with path following:
- Implements methods for PathPlanner
- Provides current pose to trajectory following
- Executes commanded velocities from path
- Uses vision (Limelight) for pose correction
