Drivetrain {#drivetrain}
=============

There are three conventional types of drivetrains.

## Tank Drive

A tank drive uses wheels driven by motors, with varying motor speeds to turn. Usually, we use four motors for drive,
so there are different ways to implement wheels.

1. Pusher: uses two wheels at the back to drive the front two wheels (kinda like a 2wd car)
2. 4WD: Uses 4 wheels, each with their own motor.
3. More wheel drive: Basically the same but with more wheels linked by chains or belts or gears.

**Pros:**

1. Good Traction
2. Simplest to build

**Cons:**

1. Can only move forward and backwards quickly
2. Needs more time and space to turn

## Mecanum / Holonomic Drive

A mecanum drive system uses the same chassis as the tank drive, but instead of wheels, it uses mecanums. Basically, it is rollers on wheels. 
This allows the motors to turn at different speeds to move in any direction. Unfortunately, becuase it is wheel on wheel, it loses traction and acceleration. 

**Pros:**

1. Relatively simple to build
2. More degrees of movement

**Cons:**

1. Loses Traction
2. Wheels are expensive

## Swerve Drive (very experimental)

Swerve Drive is a self-designed mechanism to allow most complicated maneuvering (such as turning and moving in a parabolic pattern), because each wheel is individually turnable. This is mainly utilized in FRC, because they do not have an 8 motor limit. 
There are two types of swerve drive:

1. Coaxial (Uses one motor to turn and one motor to drive)
2. Differential (Uses both motors to turn and drive, using different combinations of gears.)

**Pros:**

1. Good maneuvering
2. Good traction

**Cons:**

1. Hard to make and you have to make it yourself
2. Hard to code

## Update on current situation

We are currently using mecanum drive, but designing and concept-testing a swerve drive in offseason. We hope to implement swerve drive next season. If you are interested in helping developing new drivetrains, please contact Han (self-proclaimed head of drive train development :3)
