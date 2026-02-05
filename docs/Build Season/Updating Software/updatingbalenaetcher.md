<h1> Updating BalenaEtcher </h1>

<h2> What is BalenaEtcher? </h2>

BalenaEtcher is a free, cross-platform tool for writing disk images to SD cards and USB drives. In FRC, it's used for:
- Imaging SystemCore SD cards
- Creating bootable SD cards for recovery
- Flashing Limelight SD cards
- Backing up and restoring system images

<h2> When to Update </h2>

Update BalenaEtcher:
- At start of build season
- If you encounter imaging errors
- When new version is released
- Before imaging critical hardware

<h2> Installation </h2>

**1. Download**:
- Visit https://www.balena.io/etcher/
- Click "Download" button
- Choose version for your OS:
  - Windows: .exe installer
  - Mac: .dmg installer
  - Linux: AppImage or .deb

**2. Install**:
- **Windows**: Run .exe and follow installer
- **Mac**: Open .dmg and drag to Applications
- **Linux**: Make AppImage executable or install .deb package

**3. Launch**:
- Open BalenaEtcher from applications menu
- May require administrator/sudo permissions

<h2> Using BalenaEtcher </h2>

**Basic Imaging Process**:
1. **Select Image**: Click "Flash from file" and choose image file (.img, .zip, etc.)
2. **Select Target**: Click "Select target" and choose SD card/USB drive
3. **Flash**: Click "Flash!" and wait for completion
4. **Validate**: Etcher automatically validates after writing

**Important Safety Notes**:
- **Double-check target drive**: Etching overwrites all data!
- **Don't interrupt**: Wait for validation to complete
- **Safely eject**: Use OS eject function after completion
- **Keep backup**: Always have spare SD cards ready

<h2> Common Use Cases in FRC </h2>

**SystemCore Imaging**:
- Download SystemCore image from NI
- Flash to microSD card for SystemCore
- Follow WPILib imaging documentation

**Limelight SD Card**:
- Download Limelight image from limelightvision.io
- Flash to microSD card
- Insert into Limelight and power on

**Backup and Recovery**:
- Create image backups of working systems
- Quickly restore if problems occur
- Keep known-good images for competitions

<h2> Troubleshooting </h2>

**Etcher won't detect drive**:
- Try different USB port
- Try different card reader
- Check if card is write-protected
- Format card first (if needed)

**Flash fails**:
- Download image file again (may be corrupted)
- Try different SD card
- Check available disk space
- Run Etcher as administrator/sudo

**Validation fails**:
- Card may be defective
- Try different card reader
- Use slower USB port (USB 2.0)
- Check card compatibility

<h2> Best Practices </h2>

- Use high-quality SD cards (SanDisk, Samsung)
- Keep Etcher updated
- Always validate after flashing
- Label imaged cards clearly
- Keep spare pre-imaged cards
- Document image versions used
- Test imaged devices before competition
