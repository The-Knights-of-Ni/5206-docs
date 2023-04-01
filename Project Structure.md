# Project Structure

The code we write is in [/TeamCode/src/main/java/org/firstinspires/ftc/teamcode/](https://github.com/The-Knights-of-Ni/FreightFrenzy/tree/master/TeamCode/src/main/java/org/firstinspires/ftc/teamcode) and it is divided in to multiple parts for readability.

## Op Modes

The op modes are the different portions of the game:

Auto or Autonomous refers to the portion of the game the robot drives itself without interaction from the drivers.

## Pure Pursuit

Pure Pursuit is a library that gives robots extra maneuverability. Essentially, with the library, we will be able to swerve, smoothly turn, and strafe the robot so that the time it takes for our robot to move between points on the field is minimized.

## Subsystems

Control - The control subsystem controls.

Drive - The drive subsystem controls the drive train of the robot. <Insert PID/Roadrunner/Pure Pursuit stuff here>.

Vision - The vision subsystem controls all things vision. This includes the vision challenge for the season.

## Robot.java

Contains all hardware setup and most subsystem configuration. Generally you won’t have to touch this file unless you’re adding an extra subsystem.