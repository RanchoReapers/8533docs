<h1> Updating Limelight Hardware Manager </h1>

<h2> What is Limelight Hardware Manager? </h2>

Limelight Hardware Manager is a desktop application for managing Limelight smart cameras. It provides:
- Firmware updates
- SD card imaging
- Network configuration
- Device discovery
- Configuration backup/restore

<h2> When to Update </h2>

Update Limelight Hardware Manager:
- At start of build season
- Before updating Limelight firmware
- When troubleshooting Limelight issues
- When new features are released

<h2> Installation </h2>

**1. Download**:
- Visit https://limelightvision.io/pages/downloads
- Scroll to "Limelight Hardware Manager"
- Download for your OS:
  - Windows: `.exe` installer
  - Mac: `.dmg` installer
  - Linux: `.AppImage`

**2. Install**:
- **Windows**: Run .exe installer
- **Mac**: Open .dmg, drag to Applications
- **Linux**: Make AppImage executable

**3. Launch**:
- Open Limelight Hardware Manager
- Allow network permissions if prompted

<h2> Connecting to Limelight </h2>

**Discovery Methods**:
- **USB-C**: Direct connection to computer
- **Ethernet**: Connect via robot network
- **WiFi**: Connect to Limelight's WiFi hotspot

**Connection Steps**:
1. Power on Limelight (via PoE, USB-C, or barrel jack)
2. Connect computer to same network
3. Launch Hardware Manager
4. Click "Scan" or "Refresh"
5. Limelight appears in device list

<h2> Updating Limelight Firmware </h2>

**Check Current Version**:
- Select Limelight in device list
- View current firmware version
- Compare to latest available

**Update Process**:
1. Ensure stable power and connection
2. Click "Update Firmware"
3. Select latest firmware version
4. Wait for download and installation (5-10 minutes)
5. Limelight will reboot automatically
6. Verify new firmware version

**Important Notes**:
- **Don't disconnect** during update
- **Stable internet required** for download
- **Update may take several minutes**
- **Limelight reboots** automatically when complete

<h2> SD Card Imaging </h2>

If Limelight needs complete re-imaging:
1. Download latest Limelight image from website
2. Use BalenaEtcher to flash image to SD card
3. Insert SD card into Limelight
4. Power on Limelight
5. Wait for boot (LED will pulse)
6. Connect and verify operation

<h2> Configuration Management </h2>

**Backup Configuration**:
- Select Limelight
- Click "Backup Configuration"
- Save file to safe location
- Include in version control

**Restore Configuration**:
- Select Limelight
- Click "Restore Configuration"
- Choose backup file
- Wait for restoration

**Use Cases**:
- Before major changes
- When replacing Limelight
- Sharing configurations between cameras
- Disaster recovery

<h2> Network Configuration </h2>

Hardware Manager can configure:
- Static IP address
- Team number
- Network mode (DHCP vs Static)
- WiFi hotspot settings

<h2> Troubleshooting </h2>

**Can't find Limelight**:
- Check power (green status LED)
- Verify network connection
- Try USB-C direct connection
- Check firewall settings
- Restart Hardware Manager

**Firmware update fails**:
- Check internet connection
- Try direct USB-C connection
- Ensure stable power
- Wait and retry
- Try SD card re-imaging if persistent

**Connection drops during update**:
- Don't panic - Limelight may recover
- Wait 5 minutes
- Power cycle if unresponsive
- May need SD card re-imaging
