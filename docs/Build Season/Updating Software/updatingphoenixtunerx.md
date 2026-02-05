<h1> Updating Phoenix Tuner X </h1>

<h2> What is Phoenix Tuner X? </h2>

Phoenix Tuner X is CTRE's next-generation configuration tool for Phoenix 6 devices:
- CANCoders (absolute encoders)
- TalonFX motor controllers
- Pigeon 2.0 IMU
- CANdle LED controller
- CANcoder encoders

Phoenix Tuner X replaces the older Phoenix Tuner v1.

<h2> When to Update </h2>

Update Phoenix Tuner X:
- At start of build season
- When new firmware is released
- Before major competitions
- When new features are needed

<h2> Installation </h2>

**Download and Install**:
- Visit https://v6.docs.ctr-electronics.com/
- Navigate to Tuner documentation
- Download for your OS (Windows, Mac, Linux)
- Run installer and follow prompts

**Or via WinGet (Windows)**:
```
winget install CTRE.PhoenixTunerX
```

<h2> Initial Setup </h2>

**1. Launch Phoenix Tuner X**:
- Open from Start Menu or Applications

**2. Connect to Robot**:
- USB connection to SystemCore/RoboRIO
- Or over network (Ethernet/WiFi)
- Robot must be powered

**3. Detect Devices**:
- Click scan or refresh
- All CTRE devices appear in device list

<h2> Updating Firmware </h2>

**Check Current Versions**:
- View firmware version for each device
- Compare to latest available firmware

**Update Process**:
1. Select device to update
2. Click "Update Firmware" button
3. Choose latest version
4. Wait for update to complete
5. Verify new version installed
6. Repeat for all devices

**Important**: 
- Update SystemCore/RoboRIO firmware first
- Then update all other devices
- Test after each update batch

<h2> Configuration Features </h2>

**Swerve Project Generator**:
- Automatically generates swerve drive code
- Configures module constants
- Creates TunerConstants.java file
- Simplifies swerve setup

**Device Configuration**:
- Set CAN IDs
- Configure PID gains
- Set current limits
- Configure feedback sensors
- Save configurations to devices

**Plotting and Diagnostics**:
- Real-time signal plotting
- View CAN bus utilization
- Monitor device status
- Debug control loops

<h2> Phoenix 6 vs Phoenix 5 </h2>

Phoenix 6 (Tuner X) features:
- Better API design
- Improved performance
- More features
- Requires license for some features
- Not compatible with Phoenix 5 devices

Teams should use Phoenix 6 for new projects.

<h2> Licensing </h2>

Phoenix 6 has two tiers:
- **Free tier**: Basic functionality
- **Pro tier**: Advanced features (CANivore, SignalLogging, etc.)
- Purchase season license if needed

<h2> Troubleshooting </h2>

Connection issues:
- Verify robot is on and connected
- Check firewall settings
- Try USB connection if network fails
- Update Tuner X to latest version
- Check CTRE documentation for known issues
