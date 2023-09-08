Software
=============

The code we write is in
`/TeamCode/src/main/java/org/firstinspires/ftc/teamcode/ <https://github.com/The-Knights-of-Ni/CenterStage/tree/master/TeamCode/src/main/java/org/firstinspires/ftc/teamcode>`_
and it is divided in to multiple parts for readability.

.. toctree::
   :maxdepth: 1
   :caption: Contents:

   javadoc

Boring Build and Java System Info
_____________________________________

We the highest SDK version we can target is Android SDK version 29,
so if you intend to come onsite, you should have that version installed.
We use Java 1.8 (18) and gradle for building.

.. note::

    If you have to add dependencies, use ``TeamCode/build.gradle``, it is rare that you have to touch another
    gradle or build file.


SDK and Dependency Information
____________________________________

We use the FTC SDK, which is used for controlling the robot and talking to the driver station.

`FTC SDK Documentation <https://javadoc.io/doc/org.firstinspires.ftc>`_

`FTC SDK Examples <ttps://github.com/FIRST-Tech-Challenge/FtcRobotController/tree/master/FtcRobotController/src/main/java/org/firstinspires/ftc/robotcontroller/external/samples>`_

Some FTC SDK APIs, such as the Servo API, are underdeveloped, therefore we use the FTCLib API as a replacement.

`FTCLib Documentation <https://docs.ftclib.org/ftclib/v/v2.0.0/>`_

`FTCLib Examples <https://github.com/FTCLib/FTCLib/tree/master/examples>`_

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
See :ref:`pid_section` and :ref:`move_vector` for more info.

Vision
^^^^^^^^^
The vision subsystem controls all things vision. This includes the vision challenge for the season.
OpenCV is usually used.

**Vision Strategies**

*Contour detection* is a preprocessing vision detection strategy.
It checks the image for edges (with an Open-CV algorithm) and returns a black and white image that thresholds can be applied on.

*Thresholds* simply check a Mat for the amount of a certain color they have. Usually they are paired with contour detection,
but occasionally they can be used effectively by themselves.

*Object Detection* uses ML to detect objects on the field.
It hasn't been implemented successfully by this team and should be reserved for auxiliary vision tasks
due to high resources requirements and low performance as well as unreliable outputs.

*April Tags* are not used by us, but they are a hassle free alternative to most vision challenges.

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
The `target` is the desired end position of the motor, and the `actual` is the current position of the motor.

:math:`p(t)` is the motor power at time t

The actual simply means the current position of the motor, this is unlikely to be inaccurate. Target refers to the
desired end position of the motor. These are measured in ticks.

Calculations are done separately for each motor, find the calculation class in ``Subsystems/Drive/PID.java``.

Feed Forward
^^^^^^^^^^^^^^^^^^^^^
:math:`p(x, y)=K_a a(x, y) + K_v v(x, y)`

Where

:math:`p(x, y)` is the motor power at location (x, y)

:math:`K_a` is a calibrated constant.

:math:`K_v` is a calibrated constant.

:math:`v(x, y)` is the velocity at location (x, y).

:math:`a(x, y)` is the acceleration at location (x, y).

Feedforward gives a faster response than PID when correcting for errors because it doesn't require two iterations to make a desicion.
However it does require predefined paths to follow for velocity and acceleration.
A common implementation splines (roadrunner uses quintic splines) applied on vector field,
which turn the spline into numerical values for velocity and acceleration, while also providing error correction.

.. _move_vector:

Move Vector
____________

The distance and angle are calculated (atan2 is used for angle calculation).
4 separate tick counts are calculated to be passed into ``allMotorPIDControl``.

The front left and rear right motors are calculated by the distance multiplied by :math:`cos(angle)`.
The rear left and front right motors have their tick counts calculated by the distance multiplied by :math:`sin(angle)`.
Currently the angle parameter should be left as 0, and has not been tested.
