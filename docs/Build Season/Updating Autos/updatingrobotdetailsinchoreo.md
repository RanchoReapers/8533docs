<h1> Updating Robot Details in Choreo </h1>

<h2> Why Update Robot Details? </h2>

Accurate robot configuration in Choreo is critical for generating trajectories that:
- Match your robot's physical capabilities
- Don't violate motion constraints
- Execute reliably on the actual robot
- Optimize for speed without sacrificing control

<h2> When to Update Robot Details </h2>

Update robot details when:
- Starting a new season
- Robot design changes (dimensions, weight)
- Changing drivetrain motors or gearing
- Modifying wheel size
- After tuning PID or motion profiling
- Swerve module configuration changes

<h2> Robot Configuration Parameters </h2>

**Physical Dimensions**:
- **Robot Width**: Bumper-to-bumper width (meters)
- **Robot Length**: Bumper-to-bumper length (meters)
- **Mass**: Total robot weight with battery (kg)
- **Moment of Inertia**: Rotational inertia (kg⋅m²)

**Swerve Module Configuration**:
- **Module Positions**: X and Y coordinates from robot center
- **Wheel Radius**: Actual measured radius (meters)
- **Drive Gearing**: Gear ratio from motor to wheel
- **Steering Gearing**: Gear ratio for module rotation

**Performance Limits**:
- **Max Velocity**: Maximum linear speed (m/s)
- **Max Acceleration**: Maximum linear acceleration (m/s²)
- **Max Angular Velocity**: Maximum rotation speed (rad/s)
- **Max Angular Acceleration**: Maximum rotational acceleration (rad/s²)

**Motor Configuration**:
- **Motor Type**: NEO, Falcon 500, etc.
- **Number of Motors**: Per drive module
- **Current Limit**: Sustained and peak current

<h2> Measuring Robot Parameters </h2>

**Dimensions**:
- Measure with tape measure (outside of bumpers)
- Convert to meters
- Be precise - affects collision detection

**Mass**:
- Weigh complete robot with battery
- Convert to kilograms
- Update if adding/removing components

**Wheel Radius**:
- Measure actual wheel diameter
- Account for compression under load
- Test empirically (drive known distance)

**Maximum Velocities**:
- Test on field with full power
- Measure using odometry or external tracking
- Use conservative values for safety

**Module Positions**:
- Measure from robot center to wheel contact points
- Use CAD measurements if available
- Verify orientation (X forward, Y left)

<h2> Configuring in Choreo </h2>

**1. Open Choreo Project**:
- Launch Choreo
- Open your project or create new

**2. Access Robot Configuration**:
- Go to Settings or Robot Config menu
- Select robot configuration tab

**3. Enter Parameters**:
- Input all measured/calculated values
- Double-check units (meters, kg, radians)
- Verify module positions correct

**4. Save Configuration**:
- Save project file
- Version control changes
- Document parameter sources

<h2> Validating Configuration </h2>

After updating parameters:
- **Generate test path**: Simple straight line or circle
- **Check velocities**: Should match robot capabilities
- **Export and test**: Run on real robot
- **Compare results**: Does robot follow path accurately?
- **Adjust if needed**: Iterate on parameters

<h2> Common Configuration Mistakes </h2>

- **Wrong units**: Mixing inches and meters
- **Module positions**: Incorrect sign or orientation
- **Unrealistic limits**: Too high causes unstable paths
- **Gear ratios**: Using wrong ratio calculation
- **Wheel radius**: Not accounting for compression
- **Mass**: Forgetting battery weight

<h2> Configuration Templates </h2>

Save proven configurations:
- Create template for your robot type
- Share with team members
- Document changes between seasons
- Keep in version control

<h2> Testing and Iteration </h2>

Validate configuration through testing:
1. Create simple test paths (straight, circle, square)
2. Deploy to robot and execute
3. Measure actual vs expected performance
4. Adjust parameters based on results
5. Re-generate paths with new config
6. Repeat until accurate

<h2> Best Practices </h2>

- Measure carefully and document
- Use conservative performance limits initially
- Test simple paths before complex autos
- Update configuration when robot changes
- Keep configuration in version control
- Share configuration with team
- Revalidate after mechanical changes
