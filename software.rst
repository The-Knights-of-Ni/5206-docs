Software
=============

The code we write is in
`/TeamCode/src/main/java/org/firstinspires/ftc/teamcode/ <https://github.com/The-Knights-of-Ni/CenterStage/tree/master/TeamCode/src/main/java/org/firstinspires/ftc/teamcode>`_
and it is divided into multiple files for readability and usability.

.. toctree::
   :maxdepth: 1
   :caption: Contents:

   javadoc

Boring Build and Java System Info
_____________________________________

We the highest SDK version we can use is Android SDK version 25 (because the control hub runs that)
so the minimum sdk version is limited to that.
The compile SDK version can be as high as you'd like it to, as can gradle, java and, AGP.

.. note::

    If you want to add dependencies, use ``TeamCode/build.gradle``, it is rare that you have to touch another
    gradle or build file
    (unless you are upgrading FIRST dependencies, which sometimes have mid-season updates, or upgrading sdk versions/gradle/AGP).


SDK and Dependency Information
____________________________________

We use the FTC SDK, which is used for controlling the robot and talking to the driver station.

`FTC SDK Documentation <https://javadoc.io/doc/org.firstinspires.ftc>`_

`FTC SDK Examples <ttps://github.com/FIRST-Tech-Challenge/FtcRobotController/tree/master/FtcRobotController/src/main/java/org/firstinspires/ftc/robotcontroller/external/samples>`_

Some FTC SDK APIs, such as the Servo API, are underdeveloped, therefore we use the FTCLib API as a replacement.

`FTCLib Documentation <https://docs.ftclib.org/ftclib/v/v2.0.0/>`_

`FTCLib Examples <https://github.com/FTCLib/FTCLib/tree/master/examples>`_

.. note::

        We use ftclib mainly for the servo API, so we copied the class out and it is now located in the util folder as ``ServoEx``.


Op Modes
______________

The op modes (short for Operational Modes) are the different portions of the game:

Auto or Autonomous refers to the portion of the game the robot drives itself without interaction from the drivers,
this usually lasts 30 seconds.

The Teleop period starts directly after that, and lasts 2:30, drivers use 2 gamepads to send instructions to the robot.


Subsystems
___________

Control
^^^^^^^^^^^^^
The control subsystem controls.

Drive
^^^^^^^^
The drive subsystem controls the drive train of the robot.
See :ref:`pid_section` and :ref:`move_vector` for more info.

Vision
^^^^^^^^^
The vision subsystem controls all things vision. This includes the vision challenge for the season.
OpenCV is used, as there is no viable alternative (Vuforia is no longer supported and see below for tensorflow-lite).

**Vision Strategies**

*Contour detection* is a vision detection strategy.
It checks the image for edges (with an Open-CV algorithm) and returns a list of edges that can be summed up.
To eliminate noise, thresholds are used as a preprocessing strategy.

*Thresholds* simply check a Mat (the matrix representation of an image) for the amount of a certain color they have.
Usually they are paired with contour detection, but occasionally they can be used effectively by themselves.

*Object Detection* uses ML to detect objects on the field.
It hasn't been implemented successfully by this team and should be reserved for auxiliary vision tasks
due to high resources requirements and low performance as well as unreliable outputs.

*April Tags* are used for robot position correction, and target detection, as FIRST uses them.

Robot.java
___________

Contains all hardware setup and most subsystem configuration.

Drive Systems
_______________


.. note::

    We currently rely on a PID system.

.. _pid_section:

PID
^^^^^^
`PID <https://medium.com/autonomous-robotics/pid-control-85596db59f35>`_ stands for
`Proportional Integral Derivative <https://en.wikipedia.org/wiki/PID_controller>`_
and is used by our drive subsystem to maintain consistent speed
and ensure that slippage does not affect the movement of the robot.

:math:`p(t)=K_p e(t) + K_i \int_{0}^{t} e(t) \,dt + K_d \frac{de(t)}{dt}`

Where:

:math:`e(t)=\text{target}-\text{actual}` at time t.
The `target` is the desired value of the attribute, and the `actual` is the current value of the attribute.

:math:`p(t)` is the power (whether it be physical motor power or theoretical velocity) at time t.

The actual simply means the current state of the attribute, this is unlikely to be inaccurate. Target refers to the
desired state of the attribute. The attribute is an int/float that represents a physical quantity, the robot's angle, or even motor tick counts.
These can be measured in any unit, but millimeters, tick counts, or degrees are preferred by the team.

See Also: https://gm0.org/en/latest/docs/software/concepts/control-loops.html?highlight=PID#pid

Feed Forward
^^^^^^^^^^^^^^^^^^^^^
:math:`p(x, y)=K_a a(x, y) + K_v v(x, y)`

Where

:math:`p(x, y)` is the attribute value at location (x, y)

:math:`K_a` is a calibrated constant.

:math:`K_v` is a calibrated constant.

:math:`v(x, y)` is the velocity at location (x, y).

:math:`a(x, y)` is the acceleration at location (x, y).

Feedforward gives a faster response than PID when correcting for errors because it doesn't require an iteration to make a desicion.
However it does require predefined paths to follow for velocity and acceleration.
Such paths can be generated by motion profiles, which return a position, velocity, and acceleration.

Holonomic Control
^^^^^^^^^^^^^^^^^^^^^^^^
PIDs needs a way to talk to the motors. The holonomic controller calculates the motor speeds using 3 PIDs.
One for x movement, one for y movement, and one for theta movement.
The conversion from robot velocities to motor powers uses these formulas: https://gm0.org/en/latest/docs/software/tutorials/mecanum-drive.html

See also: https://www.ctrlaltftc.com/practical-examples/drivetrain-control#mecanum-drivetrain-controller


Motion Profiling
^^^^^^^^^^^^^^^^^^

Motion Profiles define a target velocity and acceleration.
The advantage of doing this is a reduction of slippage, as acceleration can be limited.
The simplest type of motion profile is a trapezoidal motion profile, which has a constant acceleration and deceleration.
More complex motion profiles, such as quintic splines, can be used to follow a curved path.

See also: https://www.ctrlaltftc.com/advanced/motion-profiling
