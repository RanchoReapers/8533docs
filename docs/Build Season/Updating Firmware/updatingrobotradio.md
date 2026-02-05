<h1> Updating Robot Radio Firmware </h1>

<h2> What is the Robot Radio? </h2>

The robot radio is the OpenMesh OM5P-AN or OM5P-AC wireless access point that provides communication between the driver station and robot. It must be properly configured and updated for FRC use.

<h2> When to Update Radio </h2>

Update/configure radio:
- At start of build season
- When bringing new radio into service
- If radio firmware is outdated
- Before competition (verify configuration)
- After radio factory reset

<h2> Required Tools </h2>

- **FRC Radio Configuration Utility** (part of FRC Game Tools)
- **Ethernet cable**
- **Robot radio** with power supply or PoE
- **12V power supply** or robot battery

<h2> Radio Programming Steps </h2>

**1. Connect Radio**:
- Connect radio to 12V power or PoE injector
- Connect Ethernet from computer to radio's 18-24v PoE port
- Wait for radio to boot (about 30 seconds)

**2. Launch FRC Radio Configuration Utility**:
- Open from Start Menu
- Should detect radio automatically

**3. Configure Radio**:
- Select radio from list
- Enter team number (e.g., 8533)
- Choose firmware version:
  - **FRC Configuration**: Competition use (5 GHz only)
  - **2.4 GHz AP**: Practice/pit use
- Click "Configure"

**4. Wait for Programming**:
- Process takes 3-5 minutes
- Don't disconnect during programming
- Radio will reboot when complete

**5. Verify Configuration**:
- Radio status LEDs should be solid
- Can connect to robot network
- Team number appears in SSID

<h2> Radio LED Status </h2>

Understanding LED patterns:
- **Solid LEDs**: Radio configured and working
- **Blinking LEDs**: Radio booting or updating
- **No LEDs**: Check power connection

<h2> Radio Network Settings </h2>

After configuration:
- **SSID**: FRC_XXXX (XXXX = team number)
- **Robot IP**: 10.TE.AM.2 (e.g., 10.85.33.2)
- **Driver Station**: 10.TE.AM.5
- **5 GHz band**: For competition
- **2.4 GHz band**: For practice (if configured)

<h2> Troubleshooting </h2>

**Can't detect radio**:
- Check power (LEDs should be on)
- Verify Ethernet connection
- Try different Ethernet port
- Disable WiFi on computer
- Check firewall settings

**Programming fails**:
- Try different Ethernet cable
- Ensure stable power
- Close other networking programs
- Try factory reset first
- Use different computer

**Radio not working after programming**:
- Verify correct team number entered
- Check robot IP addressing
- Try 2.4 GHz mode for testing
- Re-program radio
- Contact FTA if at competition

<h2> Best Practices </h2>

- Program radios well before competition
- Label radios with team number
- Keep spare programmed radio
- Document radio settings
- Test radio range before comp
- Secure radio mounting on robot
