Build Systems {#build_systems}
==================================

## Gradle

We don't run `javac` or `jar` directly, as these are made for desktop applications.
Instead, we use a build system called `gradle`. Gradle is a build system that is used to compile, test, and package the app.
It is also used to manage dependencies and run tasks, allowing us to bring in external code and automate routine operations.
The control hub runs Android, which is oddly common in the robotics world,
but we don't write an entire android app as FIRST has helpfully provided boilerplate code for us.
The real app (i.e. the android activity and other app related code) is stored in `FtcRobotController`.
This project essential wraps around our code and ensures that basic robot functions like telemetry work.
The control hub doesn't have a GUI, but many android concepts remain the same.
For starters, apps are packaged as `apk` files, which are then installed on the robot, we do so over `adb`.
`adb` is a command line tool that allows us to interact with the robot over USB or WIFI.

> [!caution]
> Do not modify the `FtcRobotController` project. This is permitted by FIRST, but the benefits of doing this are practically nonexistent.
> Modifying the official FIRST dependencies is ILLEGAL, and will result in disqualification.

### Concepts

- Min SDK Version: The minimum version of Android that the app will run on. This is set to 25 because the control hub runs that version.
- Compile SDK Version: The version of Android that the app is compiled against. This can be as high as you'd like it to be.
- Target SDK Version: The version of Android that the app is targeted towards. This can be as high as you'd like it to be, but it should be less than or equal to the compile sdk version. It should preferably be equal to the compile sdk version.
- Gradle: A build system for java projects. It is used to compile, test, and package the app.
- Gradle Wrapper: A script that downloads and runs a specific version of gradle. This is used to ensure that everyone is using the same version of gradle.
- Android Gradle Plugin: A plugin for gradle that adds support for building android apps. This allows gradle to output an `apk`, which is then installed on the robot.

The web logs should output the SDK version of the control hub on initialization.

.. note::

    The SDK installation location is stored in `local.properties`.

### Files

- `build.gradle`: The main build file for the project. This file is used to configure the project and its subprojects. You can upgrade the Android Gradle Plugin version here.
- `build.dependencies.gradle`: A file that contains all of the dependencies for the project. This file is used to keep the `build.gradle` file clean and storTes all the default FIRST dependencies.
- `build.common.gradle`: A file that contains all of the common configurations for the project. This is shared between the `eamCode` and `FtcRobotController` projects.
- `settings.gradle`: A file that is used to include or exclude subprojects from the build. This file is used to include the `TeamCode` and `FtcRobotController` projects in the build. If you want to add more subprojects, you must add a include directive here.
- `TeamCode/build.gradle`: The build file for the `TeamCode` project. This file is used to configure the `TeamCode` project. Any project specific modifications should be put here.

## Dependencies

### SDK

We use the FTC SDK, which is used for controlling the robot and talking to the driver station.

- `FTC SDK Documentation <https://javadoc.io/doc/org.firstinspires.ftc>`_
- `FTC SDK Examples <ttps://github.com/FIRST-Tech-Challenge/FtcRobotController/tree/master/FtcRobotController/src/main/java/org/firstinspires/ftc/robotcontroller/external/samples>`_

### FTCLib

Some FTC SDK APIs, such as the Servo API, are underdeveloped, therefore we use the FTCLib API as a replacement.

- `FTCLib Documentation <https://docs.ftclib.org/ftclib/v/v2.0.0/>`_
- `FTCLib Examples <https://github.com/FTCLib/FTCLib/tree/master/examples>`_

.. note::

        We used ftclib mainly for the servo API, so we copied the class out and it is now located in the util folder as ``ServoEx``. Thus, we do not add it as a Gradle dependency anymore.


### OpenCV

We use OpenCV for the vision challenge via EasyOpenCV.

| `OpenCV Documentation <https://docs.opencv.org/>`_
| `EasyOpenCV GitHub <https://github.com/OpenFTC/EasyOpenCV>`_
| `EasyOpenCV Javadoc <https://javadoc.io/doc/org.openftc/easyopencv/1.5.1/index.html>`_

.. note:: EasyOpenCV is in the process of being phased out for a Rust/OpenCV system instead. This will soon become deprecated.

### Apache Commons Math & Geometry

We use this library mainly used for vector math. However it's geometry utilities could be useful for pathfinding.

| `Info on Apache Commons Math <https://commons.apache.org/proper/commons-math/>`_
