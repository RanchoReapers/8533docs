<h1>Deploying Robot Code</h1>

<h2>Why Deploy Code?</h2>

Deploying code to the robot is a critical step in the development process:
- Allows testing of new features
- Verifies hardware and software integration
- Ensures the robot is competition-ready
- Provides a feedback loop for debugging

<h2>Before Deploying</h2>

**Preparation Steps**:
1. Verify code compiles without errors
2. Ensure all dependencies are up-to-date
3. Check team number in project settings
4. Confirm RoboRIO firmware is current
5. Test in simulation (if applicable)

**Robot Setup**:
- Ensure RoboRIO is powered on
- Connect to the robot via USB or Wi-Fi
- Verify all hardware connections are secure
- Check battery voltage is sufficient

<h2>Deployment Methods</h2>

**Method 1: Deploy via VS Code** (Recommended):
1. Open the project in VS Code
2. Press `Ctrl+Shift+P`
3. Select "WPILib: Deploy Robot Code"
4. Monitor the terminal for deployment status

**Method 2: Deploy via Command Line**:
```bash
# Navigate to project directory
cd /path/to/project

# Deploy code to robot
./gradlew deploy
```

**Method 3: Offline Deployment**:
1. Build the project locally
2. Transfer the build files to the RoboRIO
3. Use SSH to manually deploy the code

<h2>Post-Deployment Checks</h2>

After deploying, verify the following:
1. **Code Runs Successfully**: Check Driver Station logs for errors
2. **Subsystems Respond**: Test basic functionality (e.g., drive, intake)
3. **Dashboard Updates**: Ensure telemetry data is visible
4. **Network Stability**: Verify no connection drops

<h2>Debugging Deployment Issues</h2>

**Common Issues**:
- **Deployment Fails**: Check team number, network connection, and RoboRIO firmware
- **Code Crashes**: Review logs for stack traces and fix errors
- **Subsystems Unresponsive**: Verify CAN IDs, wiring, and hardware status

**Troubleshooting Steps**:
1. Rebuild the project: `./gradlew clean build`
2. Restart the RoboRIO
3. Check Driver Station logs for detailed error messages
4. Test individual subsystems to isolate issues

<h2>Best Practices</h2>

- Deploy frequently during development
- Test on a practice robot before competition
- Keep a backup of the last working code
- Document changes and deployment steps
- Use version control to track code history

<h2>Team Onboarding</h2>

Help team members understand the deployment process:
- Provide a walkthrough of deployment steps
- Share troubleshooting tips
- Assign deployment tasks during testing
- Encourage documenting deployment issues and resolutions
