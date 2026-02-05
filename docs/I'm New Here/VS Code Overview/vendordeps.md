<h1> Vendor Dependencies </h1>

<h2> What are Vendor Dependencies? </h2>

Vendor dependencies (vendordeps) are libraries provided by hardware manufacturers and third parties that add support for their devices in WPILib. Examples include:
- REV Robotics (SPARK MAX, PDH)
- CTRE Phoenix (CANCoders, Talons, Pigeons)
- Kauai Labs (NavX)
- PhotonVision
- PathPlanner

<h2> Managing Vendor Dependencies </h2>

To add a vendor dependency:
1. Press Ctrl+Shift+P (Cmd+Shift+P on Mac)
2. Type "WPILib: Manage Vendor Libraries"
3. Select "Install new library (online)"
4. Enter the JSON URL from the vendor's website
5. The library will be downloaded and configured

Common vendordep URLs are typically found on:
- Vendor documentation websites
- GitHub release pages
- FRC documentation

<h2> The vendordeps Folder </h2>

Vendor dependencies are stored as JSON files in the `vendordeps` folder. Each JSON file:
- Specifies library version
- Lists required Java dependencies
- Defines native libraries for different platforms
- Configures Maven repository URLs

<h2> Updating Vendor Dependencies </h2>

To update vendordeps:
1. Open WPILib Command Palette
2. Select "WPILib: Manage Vendor Libraries"
3. Choose "Check for updates (online)"
4. Select which libraries to update
5. Rebuild the project after updating
