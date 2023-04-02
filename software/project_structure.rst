Project Structure
=========================

The code we write is in
`/TeamCode/src/main/java/org/firstinspires/ftc/teamcode/ <https://github.com/The-Knights-of-Ni/FreightFrenzy/tree/master/TeamCode/src/main/java/org/firstinspires/ftc/teamcode>`_
and it is divided in to multiple parts for readability.

Op Modes
______________

The op modes are the different portions of the game:

Auto or Autonomous refers to the portion of the game the robot drives itself without interaction from the drivers.


Subsystems
___________

Control
^^^^^^^^^^^^^
The control subsystem controls.

Drive
^^^^^^^^
The drive subsystem controls the drive train of the robot.

Vision
^^^^^^^^^
The vision subsystem controls all things vision. This includes the vision challenge for the season. OpenCV is usually used.

**Vision

Robot.java
___________

Contains all hardware setup and most subsystem configuration. Generally you won’t have to touch this file unless you’re adding an extra subsystem.

PID
_____
PID stands for Proportional Integral Derivative and is used by our drive subsystem.

:math:`p(t)=K_p e(t) + K_i \int_{0}^{t} e(t) \,dt + K_d \frac{de(t)}{dt}`

Where
:math:`e(t)=\text{target}-\text{actual}` at time t and
:math:`p(t)` is the motor power at time t

The actual simply means the current position of the motor, this is unlikely to be inaccurate. Target refers to the
desired end position of the motor. These are measured in ticks.

Calculations are done separately for each motor, find the calculation class in ``Subsystems/Drive/PID.java``.


