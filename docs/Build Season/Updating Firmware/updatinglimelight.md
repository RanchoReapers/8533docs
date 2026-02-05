<h1> Updating Limelight Firmware </h1>

<h2> When to Update Limelight Firmware </h2>

Update Limelight firmware:
- At start of build season
- When new features are released
- Before major competitions
- If experiencing vision issues
- When updating Google Coral neural networks

<h2> Prerequisites </h2>

- Limelight Hardware Manager installed
- Limelight powered and connected
- Stable internet connection (for firmware download)
- Backup of current pipeline configurations

<h2> Checking Current Firmware </h2>

**Method 1: Web Interface**:
- Navigate to http://limelight.local:5801/
- Check firmware version on homepage
- Note version number

**Method 2: Hardware Manager**:
- Launch Limelight Hardware Manager
- Connect to Limelight
- View firmware version in device info

<h2> Update Process </h2>

**1. Backup Configuration**:
- Open Limelight web interface
- Go to Settings tab
- Download pipeline backup
- Save to safe location

**2. Connect to Limelight**:
- Ensure Limelight has stable power
- Connect via USB-C, Ethernet, or WiFi
- Launch Limelight Hardware Manager

**3. Start Update**:
- Select Limelight in device list
- Click "Update Firmware"
- Select latest available version
- Confirm update

**4. Wait for Update**:
- Download and installation (5-10 minutes)
- Limelight will reboot automatically
- Status LED will indicate progress
- **Don't disconnect power or network!**

**5. Verify Update**:
- Limelight reboots and shows new version
- Check web interface accessible
- Verify pipelines still configured
- Test vision processing

<h2> Restore Configuration </h2>

If settings were reset:
- Open web interface
- Go to Settings tab
- Upload pipeline backup
- Verify pipeline settings
- Test with targets

<h2> Testing After Update </h2>

Verify Limelight operation:
- **AprilTag detection**: Point at tags, check detection
- **Neural network**: Test game piece detection (if using)
- **LED control**: Test LED modes
- **Streaming**: Check video stream
- **NetworkTables**: Verify data publishing
- **Pose estimation**: Test MegaTag/MegaTag2

<h2> Limelight 3 Specific Features </h2>

After updating, check new features:
- Dual camera support
- MegaTag2 improvements
- Python scripting updates
- New neural network capabilities
- Improved pose estimation

<h2> Google Coral Compatibility </h2>

If using Google Coral:
- Verify neural network models still load
- Re-train/re-upload if model format changed
- Test detection accuracy
- Check inference speed

<h2> Common Issues After Update </h2>

**Web interface not loading**:
- Wait longer (Limelight may still be booting)
- Check network connection
- Try http://10.TE.AM.11/ (team number based)
- Power cycle Limelight
- Check Ethernet cable

**Pipelines reset**:
- Restore from backup
- Recreate pipelines if no backup
- Document pipeline settings going forward

**Vision not working**:
- Check camera focused
- Verify correct pipeline selected
- Test with known targets
- Check LED control
- Review pipeline settings

**NetworkTables data missing**:
- Verify robot code compatible with firmware
- Check NetworkTables connection
- Update LimelightHelpers.java if needed
- Restart robot code

<h2> Multiple Limelights </h2>

If running multiple Limelights:
- Update one at a time
- Test each before updating next
- Use descriptive names (limelight-front, limelight-back)
- Verify network configuration for each
- Update LimelightHelpers calls in code

<h2> Firmware Version Selection </h2>

Limelight firmware options:
- **Latest Release**: Stable, recommended
- **Beta**: New features, may be unstable
- **Specific versions**: For known-good configurations

For competitions, use latest release version.

<h2> Best Practices </h2>

- Update early in build season
- Always backup pipelines first
- Test thoroughly after updating
- Don't update right before competition
- Document firmware version used
- Keep spare Limelight with old firmware (if needed)
- Update all Limelights to same version
- Test in competition-like conditions

<h2> SD Card Re-imaging </h2>

If update fails completely:
- Download latest Limelight image
- Use BalenaEtcher to flash SD card
- Insert into Limelight
- Power on and configure from scratch
- Restore pipelines from backup
