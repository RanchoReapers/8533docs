<h1> Updating Last Year's Robot Code </h1>

<h2> Why Update Instead of Rewrite? </h2>

Updating existing code is usually better than starting from scratch:
- Faster development
- Proven architecture
- Known working patterns
- Less risk of introducing new bugs
- Team familiarity

<h2> Update Strategy </h2>

**Phase 1: Infrastructure Updates** (Week 1-2):
- Update WPILib and vendor dependencies
- Fix compilation errors
- Update deprecated API calls
- Modernize code patterns if needed

**Phase 2: Robot-Specific Updates** (Week 2-3):
- Update Constants for new robot
- Modify drive code for new dimensions
- Adapt odometry for new robot

**Phase 3: Game-Specific Features** (Week 3-6):
- Add new subsystems for game mechanisms
- Create commands for game actions
- Implement autonomous routines

**Phase 4: Testing and Polish** (Week 6-8):
- Tune PID controllers
- Optimize autonomous
- Fix bugs
- Add safety features

<h2> Updating Dependencies </h2>

**WPILib Update**:
- Install new year's WPILib
- Open project in new year's VS Code
- Build project
- Fix any API changes

**Vendor Library Updates**:
```
Ctrl+Shift+P -> WPILib: Manage Vendor Libraries
-> Check for updates (online)
-> Update all libraries
```

**Common API Changes to Address**:
- Method name changes
- Parameter changes
- Deprecated functionality
- New required imports

<h2> Updating Constants.java </h2>

**Physical Constants**:
- Robot dimensions (width, length, mass)
- Wheel diameter and track width
- Module positions for swerve
- Mechanism reach and limits

**CAN IDs**:
- Verify all device IDs match wiring
- Update for new devices
- Maintain consistent numbering scheme

**Performance Limits**:
- Max speeds and accelerations
- Current limits
- Position/velocity limits for mechanisms

**Control Constants**:
- PID gains (will need re-tuning)
- Feedforward values
- Motion profile constraints

<h2> Updating Subsystems </h2>

**Drivetrain Subsystem**:
- Update module positions if changed
- Adjust gear ratios if different
- Verify motor inversions
- Update odometry parameters

**Existing Mechanism Subsystems**:
- Remove if not on new robot
- Keep structure if similar mechanism planned
- Archive for reference

**New Mechanism Subsystems**:
- Create based on existing patterns
- Follow same structure as drive subsystem
- Use proven initialization patterns

<h2> Updating Commands </h2>

**Drive Commands**:
- Update joystick scaling if needed
- Adjust field-centric behavior
- Modify any auto-align features

**Auto Commands**:
- Create new auto routines for new game
- Keep framework and structure
- Reuse path following logic

**Mechanism Commands**:
- Create new commands for new mechanisms
- Follow existing command patterns
- Use command composition

<h2> Updating RobotContainer </h2>

**Controller Bindings**:
- Map new commands to buttons
- Remove old game-specific bindings
- Keep drive controls consistent
- Add bindings for new mechanisms

**Autonomous Selection**:
- Update SendableChooser options
- Add new auto routines
- Remove old game-specific autos
- Keep simple fallback options

<h2> Updating Autonomous </h2>

**Path Following**:
- Keep existing framework
- Update for new game field
- Create new paths in Choreo
- Test with new robot dimensions

**Auto Commands**:
- Create sequences for game tasks
- Combine with new mechanism commands
- Add decision logic if needed
- Keep modular and reusable

<h2> Code Quality Improvements </h2>

While updating, also improve:
- Add missing comments
- Fix naming inconsistencies
- Remove dead code
- Improve error handling
- Add logging where useful
- Update unit tests

<h2> Testing Strategy </h2>

**Incremental Testing**:
1. Test after each major update
2. Verify basic functionality before moving on
3. Use simulation for initial testing
4. Test on practice robot when available
5. Validate on competition robot

**Test Checklist**:
- [ ] Code builds without errors
- [ ] Drive system operates correctly
- [ ] All motors spin correct direction
- [ ] Sensors read correctly
- [ ] Commands execute as expected
- [ ] Autonomous routines work
- [ ] Safety limits function
- [ ] Dashboard displays data

<h2> Version Control Best Practices </h2>

**Branching Strategy**:
- Create feature branches for major changes
- Use pull requests for code review
- Keep main branch stable
- Tag important milestones

**Commit Messages**:
- Describe what and why
- Reference issues if applicable
- Use consistent format
- Make commits atomic

<h2> Documentation Updates </h2>

Update documentation to reflect changes:
- README with new features
- Code comments for complex logic
- Setup instructions
- Known issues
- Testing procedures

<h2> Common Pitfalls </h2>

**Scope Creep**:
- Resist urge to rewrite everything
- Focus on necessary updates first
- Add features incrementally
- Keep it simple initially

**Breaking Changes**:
- Test thoroughly after updates
- Don't update everything at once
- Keep working backup
- Document what changed

**Premature Optimization**:
- Get it working first
- Optimize based on actual needs
- Don't over-engineer early
- Profile before optimizing

<h2> Best Practices </h2>

- Update incrementally, test frequently
- Keep team informed of changes
- Use code reviews
- Maintain backward compatibility when possible
- Document breaking changes
- Keep old code as reference
- Plan updates before starting
- Communicate with other subteams
