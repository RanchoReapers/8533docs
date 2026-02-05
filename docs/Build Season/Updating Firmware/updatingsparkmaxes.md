<h1> Updating SPARK MAX Firmware </h1>

<h2> When to Update SPARK MAX Firmware </h2>

Update SPARK MAX firmware:
- At start of build season
- When new firmware is released
- Before competitions
- When adding new SPARK MAXes
- If experiencing control issues

<h2> Prerequisites </h2>

- REV Hardware Client 2 installed and updated
- Robot powered with 12V battery
- USB or CAN connection to robot
- All SPARK MAXes have unique CAN IDs

<h2> Update Process </h2>

**1. Connect to Robot**:
- Power robot with 12V battery
- Connect computer via USB or SystemCore/RoboRIO
- Ensure CAN bus is properly terminated

**2. Launch REV Hardware Client**:
- Open REV Hardware Client 2
- Wait for device discovery
- SPARK MAXes appear in device list

**3. Check Current Firmware**:
- Select each SPARK MAX
- Note current firmware version
- Compare to latest available

**4. Update Firmware**:
- Select SPARK MAX to update
- Click firmware version indicator
- Choose latest firmware version
- Click "Update Firmware"
- Wait for update (30-60 seconds per device)
- **Don't disconnect or power off!**

**5. Verify Update**:
- Check new firmware version
- Test motor briefly (if safe)
- Repeat for all SPARK MAXes

<h2> Bulk Update Strategy </h2>

For teams with many SPARK MAXes:
- Update by subsystem (all drive, then intake, etc.)
- Test each subsystem after updating
- Document which devices updated
- Keep one subsystem at old firmware for comparison

<h2> Configuration After Update </h2>

After firmware update, verify:
- CAN ID still correct
- Motor type setting (NEO, NEO 550)
- Current limits appropriate
- Idle mode (brake/coast)
- PID values (may reset)
- Sensor feedback configured

Some settings may reset during firmware update!

<h2> Testing After Update </h2>

Test each SPARK MAX:
- Motor spins in correct direction
- Current draw is reasonable
- No error LEDs (should be cyan/solid)
- Responds to commands properly
- PID control works correctly

<h2> SPARK MAX Status LEDs </h2>

LED color meanings:
- **Cyan/Magenta**: Normal operation
- **Blinking Red**: Fault condition
- **Blinking Cyan/Magenta**: Updating firmware
- **No LED**: No power or dead device

<h2> Troubleshooting </h2>

**Can't see SPARK MAX**:
- Check power (green power LED)
- Verify CAN wiring
- Check CAN termination
- Try different device first
- Restart REV Hardware Client

**Update fails**:
- Ensure stable power (battery charged)
- Check USB/CAN connection
- Try updating one at a time
- Update REV Hardware Client
- Contact REV support if persistent

**Motor doesn't work after update**:
- Re-configure motor type
- Check current limits
- Restore PID values
- Verify CAN ID
- Check motor connections
- Try rolling back firmware

<h2> Version Compatibility </h2>

Ensure compatibility between:
- SPARK MAX firmware
- REV Hardware Client version
- REVLib version in robot code
- SystemCore/RoboRIO firmware

Mismatched versions can cause issues!

<h2> Best Practices </h2>

- Update all devices at same time
- Keep spare SPARK MAX with current firmware
- Document firmware versions used
- Test thoroughly after updating
- Don't update right before competition
- Back up configurations before updating
