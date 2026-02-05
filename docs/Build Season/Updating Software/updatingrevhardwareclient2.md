<h1> Updating REV Hardware Client 2 </h1>

<h2> What is REV Hardware Client? </h2>

REV Hardware Client is a desktop application for configuring, updating, and testing REV Robotics hardware including:
- SPARK MAX motor controllers
- Power Distribution Hub (PDH)
- Pneumatic Hub
- Color Sensor V3
- Through Bore Encoders

<h2> When to Update </h2>

Update REV Hardware Client:
- At the start of build season
- When firmware updates are released
- Before competitions
- When troubleshooting hardware issues

<h2> Downloading and Installing </h2>

**1. Download**:
- Visit https://docs.revrobotics.com/rev-hardware-client/
- Click "Download" button
- Choose version for your OS (Windows, Mac, Linux)

**2. Install**:
- Run downloaded installer
- Follow installation wizard
- Launch REV Hardware Client 2

**3. Check for Updates**:
- Open REV Hardware Client
- Check Help menu for software updates
- Install any available updates

<h2> Using REV Hardware Client </h2>

**Connect to Devices**:
- Connect robot via USB or CAN
- Power on robot (12V battery)
- Devices appear in left sidebar

**Update Firmware**:
- Select device from list
- Click firmware version indicator
- Choose latest firmware
- Click "Update Firmware"
- Wait for completion (don't disconnect!)

**Configure Devices**:
- Set CAN IDs
- Configure motor parameters
- Set current limits
- Test motors safely
- Save configurations

<h2> Firmware Update Best Practices </h2>

- **Update all devices** at start of season
- **Verify firmware versions** match across all devices
- **Test after updating** to ensure proper operation
- **Document firmware versions** used
- **Don't update right before competition** unless critical fix
- **One device at a time** to prevent issues

<h2> Troubleshooting Connection Issues </h2>

If devices don't appear:
- Check robot is powered on
- Verify USB or CAN connection
- Try different USB port or cable
- Check device has power (green LED)
- Restart REV Hardware Client
- Check CAN termination resistor
- Verify CAN bus wiring

<h2> Important Features </h2>

**Network Tab**:
- View all devices on CAN bus
- Identify conflicts (duplicate IDs)
- Check device health

**Motor Test Tab**:
- Safely test motors
- Verify proper direction
- Check current draw
- Identify mechanical issues

**Firmware Recovery**:
- Recover bricked devices
- Force firmware update mode
- Contact REV support if needed
