<h1> Updating SystemCore Firmware </h1>

<h2> What is SystemCore? </h2>

SystemCore is the next-generation FRC robot controller that will replace the NI RoboRIO starting in 2027. It features more processing power, modern interfaces, and improved capabilities.

<h2> When to Update SystemCore Firmware </h2>

Update firmware:
- At start of build season
- When FRC releases firmware updates
- Before competitions
- When troubleshooting issues
- After SD card re-imaging

<h2> Prerequisites </h2>

Before updating:
- Download latest SystemCore firmware from NI/FRC
- Have working SD card (or backup)
- SystemCore powered and connected
- Stable internet connection
- Latest WPILib installed

<h2> Update Methods </h2>

**Method 1: WPILib Imaging Tool**:
1. Launch FRC VS Code
2. Press Ctrl+Shift+P
3. Type "WPILib: Imaging Tool"
4. Select SystemCore
5. Choose latest firmware
6. Follow prompts to update

**Method 2: Web Interface**:
1. Connect to SystemCore via Ethernet
2. Navigate to http://systemcore-XXXX.local/ (XXXX = team number)
3. Go to firmware update page
4. Upload firmware file
5. Wait for update and reboot

**Method 3: SD Card Re-imaging**:
1. Download SystemCore image
2. Use BalenaEtcher to flash SD card
3. Insert SD card into SystemCore
4. Power on and wait for boot

<h2> Verification </h2>

After updating:
- Check firmware version in web interface
- Test robot code deployment
- Verify all devices detected
- Test basic robot functions
- Check for error messages

<h2> Important Notes </h2>

- SystemCore replaces RoboRIO in 2027
- Requires updated robot code
- Different pinout than RoboRIO
- New features and capabilities
- Backward compatibility considerations

<h2> Troubleshooting </h2>

**Update fails**:
- Check power supply (stable 12V)
- Verify network connection
- Try different update method
- Re-image SD card if persistent

**SystemCore won't boot**:
- Check SD card is inserted
- Try known-good SD card
- Check power connections
- Look for status LED patterns
