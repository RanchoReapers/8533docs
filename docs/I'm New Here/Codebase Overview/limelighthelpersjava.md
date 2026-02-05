<h1> LimelightHelpers.java </h1>

<h2> What is LimelightHelpers? </h2>

LimelightHelpers.java is a utility class provided by Limelight that simplifies communication with Limelight cameras. It provides easy-to-use methods for:
- Getting target information
- Retrieving pose estimates
- Configuring pipeline settings
- Accessing neural network results
- Controlling LEDs

<h2> Common Methods </h2>

**Target Information**:
```java
// Check if camera sees a valid target
boolean hasTarget = LimelightHelpers.getTV(limelightName);

// Get horizontal angle to target (degrees)
double tx = LimelightHelpers.getTX(limelightName);

// Get vertical angle to target (degrees)
double ty = LimelightHelpers.getTY(limelightName);

// Get target area (0-100% of image)
double ta = LimelightHelpers.getTA(limelightName);
```

**Pose Estimation**:
```java
// Get robot pose from AprilTags (MegaTag2)
PoseEstimate poseEstimate = LimelightHelpers.getBotPoseEstimate_wpiBlue(limelightName);

// Access pose data
Pose2d robotPose = poseEstimate.pose;
double latency = poseEstimate.timestampSeconds;
```

**LED Control**:
```java
// Set LED mode
LimelightHelpers.setLEDMode_ForceOn(limelightName);
LimelightHelpers.setLEDMode_ForceOff(limelightName);
LimelightHelpers.setLEDMode_ForceBlink(limelightName);
```

**Pipeline Control**:
```java
// Switch to specific pipeline
LimelightHelpers.setPipelineIndex(limelightName, 0);

// Get current pipeline
long currentPipeline = LimelightHelpers.getCurrentPipelineIndex(limelightName);
```

<h2> Using LimelightHelpers </h2>

Typical usage in subsystem:
```java
public class VisionSubsystem extends SubsystemBase {
    private static final String LIMELIGHT_NAME = "limelight";
    
    public Optional<Pose2d> getRobotPose() {
        PoseEstimate estimate = LimelightHelpers.getBotPoseEstimate_wpiBlue(LIMELIGHT_NAME);
        
        if (estimate.tagCount >= 2) {  // Require at least 2 tags
            return Optional.of(estimate.pose);
        }
        return Optional.empty();
    }
    
    public boolean hasTarget() {
        return LimelightHelpers.getTV(LIMELIGHT_NAME);
    }
}
```

<h2> Best Practices </h2>

- Use descriptive Limelight names if you have multiple
- Check for valid targets before using data
- Consider latency when using pose estimates
- Use appropriate pipelines for different tasks
- Don't call Limelight methods too frequently (NetworkTables overhead)
