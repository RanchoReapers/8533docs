<h1> Updating PDH Firmware </h1>

<h2> What is the PDH? </h2>

The REV Power Distribution Hub (PDH) distributes power from the battery to all robot components while providing current monitoring for each channel. Keeping its firmware updated ensures reliable operation and access to new features.

<h2> When to Update PDH Firmware </h2>

Update PDH firmware:
- At start of build season
- When firmware updates are released
- Before competitions
- If experiencing power issues
- When adding PDH to robot

<h2> Prerequisites </h2>

- REV Hardware Client 2 installed
- Robot powered with 12V battery
- USB or CAN connection to robot
- PDH properly wired and connected

<h2> Update Process </h2>

**1. Connect to Robot**:
- Install charged 12V battery
- Connect main breaker
- Connect computer via USB to SystemCore/RoboRIO
- Ensure PDH is powered (check LEDs)

**2. Launch REV Hardware Client**:
- Open REV Hardware Client 2
- Wait for device discovery
- PDH appears in device list

**3. Select PDH**:
- Click on PDH in device list
- View current firmware version
- Check if update available

**4. Update Firmware**:
- Click firmware version indicator
- Select latest firmware version
- Click "Update Firmware"
- Wait for update (1-2 minutes)
- **Critical: Don't disconnect power!**

**5. Verify Update**:
- Check new firmware version displayed
- Observe PDH status LED
- Test channel monitoring
- Verify robot operates normally

<h2> PDH Configuration Settings </h2>

After firmware update, verify:
- CAN ID (default is 1, usually unchanged)
- Switchable channel states
- Current monitoring working
- Voltage reading accurate

<h2> Testing After Update </h2>

Verify PDH operation:
- Check voltage reading (should be ~12V)
- Monitor current on active channels
- Test switchable channels
- Verify all devices have power
- Check for fault indicators

<h2> PDH Status Indicators </h2>

**Status LED**:
- **Green**: Normal operation
- **Red**: Fault condition
- **Orange/Yellow**: Warning
- **Blinking**: Various states

**Channel LEDs**:
- Individual LEDs show which channels are active
- Useful for troubleshooting power issues

<h2> Common Issues After Update </h2>

**PDH not detected**:
- Check CAN bus connections
- Verify PDH has power
- Check CAN termination
- Try restarting REV Hardware Client

**Update fails**:
- Ensure battery is charged (>11V)
- Check stable USB/CAN connection
- Don't run motors during update
- Try again with less electrical load

**Channels not working**:
- Check breakers (may have tripped)
- Verify wiring connections
- Reset breakers
- Check current limits not exceeded

<h2> Monitoring and Diagnostics </h2>

Use REV Hardware Client to:
- View real-time current draw per channel
- Monitor total current consumption
- Check voltage under load
- Identify high-current devices
- Detect intermittent issues

This data is valuable for:
- Optimizing power distribution
- Identifying electrical problems
- Planning battery management
- Competition preparation

<h2> Best Practices </h2>

- Update PDH first (before other devices)
- Verify update before updating other hardware
- Document firmware version used
- Test thoroughly after updating
- Keep spare PDH configured and ready
- Monitor current draw regularly
- Don't update right before matches

<h2> PDH vs PDP </h2>

The PDH replaces the older CTRE Power Distribution Panel (PDP):
- More channels (20 vs 16 high-current)
- Better current monitoring
- CAN communication
- Switchable channels
- Integrated to REV ecosystem
