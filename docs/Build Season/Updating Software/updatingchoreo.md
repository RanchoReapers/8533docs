<h1> Updating Choreo </h1>

<h2> What is Choreo? </h2>

Choreo is a trajectory optimization and path planning tool for FRC autonomous routines. It helps create smooth, fast, and collision-free paths for swerve drive robots.

<h2> When to Update </h2>

Update Choreo:
- At start of build season
- When new features are released
- If experiencing bugs
- Before finalizing autonomous routines

<h2> Installation/Update Process </h2>

**1. Download Latest Version**:
- Visit https://github.com/SleipnirGroup/Choreo/releases
- Find latest release
- Download appropriate installer:
  - Windows: `.exe` or `.msi`
  - Mac: `.dmg`
  - Linux: `.AppImage` or `.deb`

**2. Install**:
- **Windows**: Run installer, follow prompts
- **Mac**: Open .dmg, drag to Applications
- **Linux**: Install package or run AppImage

**3. Verify Installation**:
- Launch Choreo
- Check Help → About for version number
- Open existing project to test

<h2> Updating Project Files </h2>

When updating Choreo:
- **Backup projects** before updating
- **Test projects** after update
- **Regenerate trajectory exports** if file format changed
- **Update robot code** if API changed

<h2> Choreo Project Structure </h2>

Choreo projects contain:
- Robot configuration (dimensions, constraints)
- Multiple trajectories
- Waypoints and control points
- Export settings

Projects are stored as files you can version control.

<h2> Key Features to Configure </h2>

**Robot Configuration**:
- Robot width and length
- Module positions
- Max velocity and acceleration
- Max angular velocity
- Wheel radius and gear ratios

**Path Configuration**:
- Waypoints with constraints
- Starting/ending velocities
- Maximum velocity zones
- Obstacle avoidance

**Export Settings**:
- File format (WPILib compatible)
- Output directory
- Coordinate system

<h2> Integration with Robot Code </h2>

After creating paths in Choreo:
1. Export trajectories
2. Place in `src/main/deploy/choreo/` directory
3. Load in robot code using `Choreo.getTrajectory(name)`
4. Create command to follow trajectory
5. Test in simulation first

<h2> Best Practices </h2>

- **Version control** Choreo project files
- **Use descriptive names** for paths
- **Test paths in simulation** before robot
- **Document constraints** used
- **Keep backup** of working configurations
- **Share project files** with team

<h2> Troubleshooting </h2>

**Paths won't generate**:
- Check robot configuration
- Reduce max velocity/acceleration
- Adjust waypoint constraints
- Check for impossible paths

**Export fails**:
- Verify output directory exists
- Check file permissions
- Update to latest Choreo version

**Robot doesn't follow path**:
- Verify odometry is accurate
- Check PID tuning
- Confirm trajectory file loaded correctly
- Validate starting position
