<h1> Importing Last Year's Robot Code </h1>

<h2> Why Import Last Year's Code? </h2>

Starting with previous year's code:
- Saves weeks of development time
- Proven, tested codebase
- Familiar structure for returning members
- Working examples of subsystems
- Established patterns and practices

<h2> Before Importing </h2>

**Preparation Steps**:
1. Review last year's code and identify what worked
2. Document known bugs or issues to fix
3. Check for pending pull requests
4. Note any season-specific code to remove
5. Plan which components are reusable

**Create New Repository**:
- Don't modify last year's repo directly
- Create new repo for current season (e.g., "2025-RobotCode")
- Use descriptive name with year
- Initialize with README and .gitignore

<h2> Import Methods </h2>

**Method 1: Clone and Reset** (Recommended):
```bash
# Clone last year's repo
git clone https://github.com/YourTeam/2024-RobotCode.git 2025-RobotCode

# Navigate into directory
cd 2025-RobotCode

# Change remote to new repo
git remote set-url origin https://github.com/YourTeam/2025-RobotCode.git

# Push to new repository
git push -u origin main
```

**Method 2: Copy Files**:
1. Download last year's code as ZIP
2. Create new WPILib project
3. Copy relevant files into new project
4. Commit to new repository
5. Note: Loses Git history

**Method 3: Template Repository**:
1. Make last year's repo a template on GitHub
2. Create new repo from template
3. Maintains structure without full history

<h2> Initial Cleanup </h2>

After importing, clean up the code:

**Update Project Information**:
- Robot name and year in README
- Team number verification in Constants
- Remove old season references
- Update year in comments

**Remove Game-Specific Code**:
- Season-specific subsystems (2024 intake, etc.)
- Game piece specific logic
- Old auto routines (keep for reference)
- Scoring mechanism code

**Update Dependencies**:
- Update WPILib to current year
- Update vendor dependencies (REV, CTRE, etc.)
- Remove unused vendordeps
- Verify compatibility

**Clean Up Build Files**:
```bash
# In project directory
./gradlew clean
```

Remove build artifacts:
- `build/` directory
- `.gradle/` directory  
- Compiled class files

<h2> What to Keep </h2>

**Core Framework**:
- RobotContainer structure
- Command-based architecture
- Constants organization
- Utility classes

**Drive Subsystem**:
- Swerve drive code (if using swerve)
- Odometry implementation
- Field-centric drive
- Auto-align commands

**Infrastructure**:
- Logging utilities
- Dashboard integration
- Auto command framework
- Simulation support

**Proven Patterns**:
- PID implementations
- State machines
- Command compositions
- Testing utilities

<h2> What to Modify/Remove </h2>

**Remove**:
- Game-specific subsystems
- Old auto routines (or move to archive)
- Hardcoded game field positions
- Season-specific utilities

**Modify**:
- CAN IDs (hardware may change)
- Physical constants (new robot dimensions)
- Control mappings (keep same, or update)
- PID values (re-tune for new mechanisms)

<h2> Update Vendor Dependencies </h2>

In VS Code:
1. Press Ctrl+Shift+P
2. "WPILib: Manage Vendor Libraries"
3. "Check for updates (online)"
4. Update all libraries
5. Build project to verify

<h2> Initial Testing </h2>

After import and cleanup:
1. **Build Project**: Verify no compilation errors
2. **Simulate**: Test basic drive functions
3. **Deploy to Practice Robot**: If available
4. **Test Drive System**: Verify basic control
5. **Check Constants**: Verify all values appropriate

<h2> Documentation Updates </h2>

Update documentation:
- README with new season info
- Architecture diagram if changed
- Contributing guidelines
- Setup instructions
- Known issues list

<h2> Team Onboarding </h2>

Help team members get started:
- Share new repository link
- Provide setup instructions
- Schedule code walkthrough
- Assign initial tasks
- Create issues for planned work

<h2> Best Practices </h2>

- Import early in build season
- Test thoroughly before modifying
- Keep last year's repo as reference
- Document what changed and why
- Create branch for import/cleanup
- Get code review before merging
- Version control everything
- Test on practice robot first

<h2> Common Issues </h2>

**Build Errors After Import**:
- Update vendor dependencies
- Check WPILib year is correct
- Clean and rebuild
- Verify Java version

**Deploy Fails**:
- Update SystemCore/RoboRIO firmware
- Check team number in settings
- Verify USB/network connection
- Update robot configuration

**Code Doesn't Work**:
- Verify CAN IDs match hardware
- Check wiring matches expectations
- Re-tune PID values
- Test each subsystem individually
