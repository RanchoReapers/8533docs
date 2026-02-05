<h1> Updating Auto Routines using Choreo </h1>

<h2> Auto Routine Planning </h2>

Before creating paths in Choreo:
- **Study the game**: Understand scoring and strategy
- **Plan routes**: Sketch paths on field diagram
- **Consider timing**: Calculate cycle times
- **Identify constraints**: Note obstacles and tight spaces
- **Prioritize**: Start with most important autos

<h2> Creating Paths in Choreo </h2>

**1. Open Choreo Project**:
- Launch Choreo
- Ensure robot configuration is correct
- Load field layout for current game

**2. Create New Trajectory**:
- Click "New Trajectory"
- Give descriptive name (e.g., "FourNoteCenter")
- Set starting position

**3. Add Waypoints**:
- Click on field to place waypoints
- Drag to adjust positions
- Add as many as needed for complex paths
- Consider game piece and scoring locations

**4. Set Constraints**:
- **Initial velocity**: Usually 0 (starting from rest)
- **Final velocity**: 0 for stopping, or match next path
- **Max velocity**: Overall or per segment
- **Heading**: Robot orientation at each point
- **Keep out zones**: Avoid obstacles

**5. Tune Path**:
- Adjust waypoints for smooth curves
- Modify constraints for optimal speed
- Preview trajectory timing
- Check for constraint violations

**6. Export Trajectory**:
- Click Export
- Choose WPILib format
- Save to `src/main/deploy/choreo/` directory

<h2> Path Types </h2>

**Scoring Paths**:
- Start from starting zone
- Navigate to scoring location
- Consider approach angle
- Account for mechanism deploy time

**Game Piece Pickup Paths**:
- Navigate to game piece location
- Slow down for intake engagement
- Consider intake mechanism reach

**Return Paths**:
- From game pieces back to scoring
- Can be faster (no precision needed)
- Optimize for time

**Multi-Part Autos**:
- Chain multiple paths together
- Match ending/starting velocities
- Consider robot state between paths

<h2> Integrating with Robot Code </h2>

After exporting from Choreo:

**1. Verify Files Deployed**:
- Check `src/main/deploy/choreo/` contains .traj files
- Ensure files are committed to Git

**2. Load in Autos.java**:
```java
ChoreoTrajectory trajectory = Choreo.getTrajectory("PathName");
```

**3. Create Follow Command**:
```java
Command followPath = Choreo.choreoSwerveCommand(
    trajectory,
    swerve::getPose,
    xPIDController,
    yPIDController,
    rotPIDController,
    swerve::setModuleStates,
    swerve
);
```

**4. Add to Autonomous Selector**:
```java
autoChooser.addOption("4 Note Auto", 
    Autos.fourNoteAuto(swerve, intake, shooter));
```

<h2> Testing Auto Routines </h2>

**Simulation Testing**:
- Test in WPILib simulation first
- Verify path generation correct
- Check timing and velocities
- Identify obvious errors

**Practice Field Testing**:
1. Clear the practice area
2. Place robot at starting position
3. Reset odometry to starting pose
4. Run autonomous
5. Observe and record results
6. Measure end position accuracy

**Iteration Process**:
- Identify issues (overshooting, missed targets)
- Adjust Choreo constraints or waypoints
- Re-export and re-deploy
- Test again
- Repeat until reliable

<h2> Common Auto Patterns </h2>

**Simple Autos (1-2 actions)**:
- Score preload and leave community
- Score preload and pickup one piece

**Medium Autos (3-4 actions)**:
- Score preload, pickup and score 2 more
- Multi-position scoring

**Complex Autos (5+ actions)**:
- Full auto cycle (4-5 game pieces)
- Dynamic path selection
- Vision-assisted pickup

<h2> Strategy Considerations </h2>

**Alliance Color**:
- May need mirrored paths for red vs blue
- Choreo can mirror paths automatically
- Test both configurations

**Starting Position**:
- Create autos for each starting position
- Consider alliance partner selection
- Have backup options

**Reliability vs Speed**:
- Start conservative, optimize later
- Balance cycle time with success rate
- Have reliable fallback autos

<h2> Debugging Auto Issues </h2>

**Robot doesn't follow path**:
- Check odometry accuracy
- Verify PID tuning
- Confirm starting position reset correctly
- Check wheel characterization

**Path generation fails**:
- Reduce max velocity/acceleration
- Adjust waypoint spacing
- Check for impossible constraints
- Verify robot configuration

**Robot overshoots/undershoots**:
- Tune PID controllers
- Adjust look-ahead distance
- Modify path constraints
- Check actual vs theoretical max speed

<h2> Competition Preparation </h2>

Before competition:
- Test all autos multiple times
- Create selection matrix (position + strategy)
- Document auto routines for drive team
- Have simple fallback autos
- Practice autonomous selection process
- Log auto performance data

<h2> Best Practices </h2>

- Start simple, add complexity gradually
- Test frequently during development
- Version control all path files
- Name paths descriptively
- Document auto sequence and timing
- Create visualization for drive team
- Always have a "do nothing" option
- Practice match procedures
