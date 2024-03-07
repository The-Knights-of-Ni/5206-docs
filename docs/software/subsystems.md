Subsystems {#subsystems}
=================

## Control

The control subsystem controls. Basically any motor or actuator that isn't the drive train.

## Drive
The drive subsystem controls the drive train of the robot.
See :ref:`pid_section` and :ref:`drive` for more info.

## Vision
The vision subsystem controls all things vision. This includes the vision challenge for the season.
OpenCV is used, as there is no viable alternative (Vuforia is no longer supported and see below for tensorflow-lite).

### Vision Strategies

#### Single Object, Multiple Locations

Use a threshold to isolate the object.
Then find the largest contour area and use that to determine the location of the object.

**Technical Details**
1. Use Gaussian Blur to remove noise (optional)
2. Convert to HSV
3. Core.inRange() to isolate the object
4. Use Imgproc.findContours() to find the contours of the object
5. See PowerPlay code if you're using color summing

#### Single Object, Single Location

... Why would you need vision for this?

*April Tags* have known locations and unique ids, and you could determine the robot's location from one,
and use them for auto adjustment.

#### Multiple Objects, Multiple Locations

Use a threshold to isolate the objects.
Then use the list of contour areas to get the locations of the objects; use April Tags to find absolute position if necessary.
This is probably the most complex vision strategy. Machine learning could be viably applied here.
