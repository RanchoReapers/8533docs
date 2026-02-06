<h1> PID Tuning for Swerve Drive </h1>

<h2> What is PID Control? </h2>

<abbr data-title="Proportional Integral Derivative">PID</abbr> (Proportional-Integral-Derivative) control is used to continuously calculate the "value of error" and apply a corresponding correction.

For swerve drive, <abbr data-title="Proportional Integral Derivative">PID</abbr> controllers are used to calculate the correction needed for in:
- Module steering (turning each wheel to desired angle)
- Module drive (controlling wheel velocity)
- Auto path following (X, Y, and rotation)

---

<h2> PID Components Explained </h2>

It is not important to understand how <abbr data-title="Proportional Integral Derivative">PID</abbr> works *exactly*, however, an understanding of how adjusting each value affects the swerve drive is important. Assume the "target" for these cases is a straight line a few feet away from the robot's starting position.

**Proportional (P)**:
Adjust when: Your robot is too slow to reach the target or overshoots wildly.
Increase P: if the robot moves too slowly toward the target.
Decrease P: if it <abbr data-title="(of swerve drive wheels) turning left and right rapidly when attempting to drive straight">oscillates</abbr> back and forth or overshoots.

**Integral (I)**:
Adjust when: The robot never quite reaches the target and gets stuck a little short.
Increase I: if it consistently undershoots.
Decrease I: if the robot starts “wobbling” around the target or <abbr data-title="(of swerve drive wheels) turning left and right rapidly when attempting to drive straight">oscillates</abbr> after reaching it.

**Derivative (D)**:
Adjust when: The robot overshoots or bounces around the target.
Increase D: to smooth motion and reduce overshoot.
Decrease D: if the robot feels too sluggish or doesn’t reach the target fast enough

---

<h2> Tuning Process </h2>
!!! danger
    Tuning is only necessary when your swerve drive <abbr data-title="(of swerve drive wheels) turning left and right rapidly when attempting to drive straight">oscillates</abbr> or overshoots/undershoots your target. If the robot does not drive straight, that is likely related to a swerve offset issue, NOT a <abbr data-title="Proportional Integral Derivative">PID</abbr> one. **ALWAYS set swerve offsets before deciding whether or not <abbr data-title="Proportional Integral Derivative">PID</abbr> tuning is necessary.**

!!! info
    The robot uses 4 <abbr data-title="Proportional Integral Derivative">PID</abbr> controllers: 1 (`turnPidController`) in `SwerveModule.java` which controls <abbr data-title="Proportional Integral Derivative">PID</abbr> in teleop, and 3 (`pathXController, pathYController, pathThetaController`) in `SwerveSubsystem.java` which control <abbr data-title="Proportional Integral Derivative">PID</abbr> in autonomous path following. Other references to <abbr data-title="Proportional Integral Derivative">PID</abbr> controllers in the code are overwritten by these 4 and should not be changed.
    
**Start with All Zeros**:
```java
PIDController controller = new PIDController(0, 0, 0);
```

**Step 1: Tune P**: <br>
1. Set I = 0, D = 0 <br>
2. Increase P gradually (start with 0.1, 0.5, 1.0, etc.) <br>
3. After each increase, deploy your update and test - you are looking for a quick reaction <br>
4. If the wheels begin to <abbr data-title="(of swerve drive wheels) turning left and right rapidly when attempting to drive straight">oscillate</abbr>, reduce your P until the issue goes away. <br>
5. You should now have a good P value (typically 2 digits of precision, ex. 0.12) <br>

**Step 2: Tune D**: <br>
1. Keep P from Step 1, I = 0 <br>
2. Increase D gradually (usually 5-20x smaller than P) <br>
3. After each increase, deploy your update and test - you are looking to reduce overshoot <br>
4. If the wheels begin to <abbr data-title="(of swerve drive wheels) turning left and right rapidly when attempting to drive straight">oscillate</abbr>, reduce your D until the issue goes away. <br>
5. You should now have a good D value (typically 2 digits of precision, ex. 0.12) <br>

!!! note
    Often, I = 0 works fine for swerve.

**Step 3: Tune I (if needed)**: <br>
1. Keep P and D from previous steps <br>
2. Increase I VERY gradually (0.001, 0.01, 0.1) <br>
3. After each increase, deploy your update and test - you are looking to reduce undershoot <br>
4. You should now have a good P value (typically 2-4 digits of precision, ex. 0.12, 0.123 or 0.1234) <br>

---

<h2> Common PID Issues </h2>

**Oscillation**:
- P too high - reduce P
- D too low - increase D
- Check for mechanical issues

**Slow Response**:
- P too low - increase P

**Never Reaches Target**:
- Add I term (carefully)
- Check for mechanical issues

**Overshoots Target**:
- P too high - reduce P
- D too low - increase D