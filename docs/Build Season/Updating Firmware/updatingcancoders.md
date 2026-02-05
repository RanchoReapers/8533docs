<h1> Updating CANCoder Firmware </h1>

<h2> What are CANCoders? </h2>

CANCoders are CTRE absolute magnetic encoders used to measure rotational position. They're critical for swerve drive steering and other mechanisms that need to know their exact angle.

<h2> When to Update CANCoder Firmware </h2>

Update CANCoder firmware:
- At start of build season
- When Phoenix 6 firmware is released
- Before competitions
- When adding new CANCoders
- If experiencing position reading issues

<h2> Prerequisites </h2>

- Phoenix Tuner X installed and updated
- Robot powered with 12V battery
- USB or CAN connection to robot
- All CANCoders have unique CAN IDs
- Magnets properly positioned near CANCoders

<h2> Update Process </h2>

**1. Connect to Robot**:
- Power robot with 12V battery
- Connect computer via USB or network
- Launch Phoenix Tuner X

**2. Discover Devices**:
- Click scan/refresh in Tuner X
- All CANCoders appear in device list
- Note current firmware versions

**3. Update Firmware**:
- Select CANCoder to update
- Click "Update Firmware" button
- Choose latest Phoenix 6 firmware
- Confirm update
- Wait for completion (30-60 seconds)
- **Don't disconnect during update!**

**4. Repeat for All CANCoders**:
- Update one device at a time
- Verify each update before moving to next
- Test position reading after each update

**5. Verify Updates**:
- Check firmware versions match
- Test position readings
- Verify configurations retained

<h2> CANCoder Configuration </h2>

After firmware update, verify:
- CAN ID is correct
- Magnet offset configured
- Update rate appropriate
- Direction correct (clockwise/counter-clockwise)
- Units set (degrees/radians/rotations)
- Absolute vs relative mode

**Important**: Firmware updates may reset some configurations!

<h2> Testing CANCoder Position </h2>

After updating, test each CANCoder:
- Rotate mechanism slowly
- Watch position value change
- Verify 0-360° range (or 0-1 rotation)
- Check position stays consistent
- Test at different speeds
- Verify absolute position retained after power cycle

<h2> Phoenix 6 vs Phoenix 5 </h2>

CANCoders work with both:
- **Phoenix 5**: Older API, stable
- **Phoenix 6**: New API, better features

Choose based on your codebase. Phoenix 6 recommended for new projects.

<h2> Magnet Alignment </h2>

For accurate readings:
- Magnet must be centered over CANCoder
- Distance: 2-5mm ideal
- Magnet must be diametrically polarized
- Check LED on CANCoder:
  - **Green**: Good magnet strength
  - **Orange**: Marginal
  - **Red**: Bad alignment or no magnet

<h2> Troubleshooting </h2>

**Can't detect CANCoder**:
- Check power (LED should light)
- Verify CAN wiring
- Check CAN termination resistor
- Try different device first
- Ensure magnet present (LED should be green/orange)

**Update fails**:
- Ensure stable 12V power
- Check CAN bus connections
- Update Tuner X first
- Try one device at a time
- Check for CAN bus errors

**Position reading wrong**:
- Verify magnet alignment (green LED)
- Re-calibrate offset
- Check configuration (direction, units)
- Verify position source in code
- Test with known good magnet

**Position drifts or jumps**:
- Check magnet distance and alignment
- Verify CAN bus not overloaded
- Check for electrical interference
- Test at lower update rates
- Ensure firmware versions match

<h2> Swerve Drive Considerations </h2>

For swerve modules:
- Update all CANCoders before tuning offsets
- Document offset values (in case reset)
- Test wheel straight position after update
- Re-run offset calibration if needed
- Verify all modules report correct angles

<h2> Best Practices </h2>

- Update all CANCoders to same firmware
- Test magnet alignment before updating
- Document offset values before updating
- Update during robot development, not at competition
- Keep spare CANCoder configured
- Label CANCoders with CAN ID
