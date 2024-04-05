FTC API Cheatsheet {#ftc_api_cheatsheet}
====================

Make an OpMode {#make_an_opmode}
----------------------------------
Annotate the class with `@TeleOp` or `@Autonomous` and ensure the class extends `LinearOpMode` or similar.

Use a Motor {#use_a_motor}
-----------------------------

```java
DcMotor motor = hardwareMap.get(DcMotor.class, "motor");
motor.setMode(DcMotor.RunMode.RUN_WITHOUT_ENCODER);
motor.setPower(1); // Without the encoder, set all the raw motor powers you'd like (between -1 and 1).
motor.setMode(DcMotor.RunMode.RUN_TO_POSITION); // Now you can set the target position.
motor.setTargetPosition(1000); // Set the target position (in ticks).
motor.setMode(DcMotor.RunMode.RUN_USING_ENCODER); // Now you can set the target velocity.
motor.setVelocity(25.0); // Set the target velocity (in ticks per second).
var currentPos = motor.getCurrentPosition(); // Get the current position of the motor (in ticks).
var currentVel = motor.getVelocity(); // Get the current velocity of the motor (in ticks per second).
```

Use a Servo {#use_a_servo}
-----------------------------

Coming Soon!



Use a Servo (FTCLib) {#use_a_servo_ftclib}
-----------------------------

Coming Soon!
