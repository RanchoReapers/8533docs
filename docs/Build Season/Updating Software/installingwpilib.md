<h1> Installing WPILib </h1>

<h2> What is WPILib? </h2>

WPILib is the complete software package for FRC robot programming. It includes:
- Visual Studio Code configured for FRC
- Java Development Kit (JDK)
- WPILib libraries and tools
- Vendor library management
- Robot simulation tools
- Documentation and examples

<h2> When to Install/Update </h2>

Install WPILib:
- At the start of build season (early January)
- When joining the programming team
- After major updates are released

Always use the version released for the current season.

<h2> Installation Steps </h2>

**1. Download Installer**:
- Go to https://docs.wpilib.org/
- Navigate to "Zero to Robot" → "Installation"
- Download the appropriate installer for your OS (Windows, Mac, Linux)

**2. Run Installer**:
- Extract the downloaded file
- Run `WPILibInstaller.exe` (Windows) or appropriate installer
- Choose "Install for this User" (recommended)
- Select components to install (use defaults)
- Choose installation directory
- Click Install

**3. Verify Installation**:
- Launch "FRC VS Code 2024" (or current year)
- Press Ctrl+Shift+P
- Type "WPILib" - should see WPILib commands
- Create a test project to verify everything works

<h2> Important Notes </h2>

- **Don't uninstall old versions** until new season code is stable
- **Each year has separate installation** (e.g., FRC VS Code 2024, 2025)
- **Installation is per-user**, not system-wide
- **Offline installer available** for competitions without internet
- **Document which version you're using** for team consistency

<h2> Post-Installation Setup </h2>

After installing:
- Set up vendor dependencies (REV, CTRE, etc.)
- Configure Git in VS Code
- Clone team repositories
- Verify robot deployment works
- Test simulation

<h2> Troubleshooting </h2>

Common installation issues:
- Antivirus blocking installer: Add exception
- Insufficient permissions: Run as administrator
- Previous incomplete installation: Manually remove old files first
- Wrong Java version: WPILib includes correct JDK
