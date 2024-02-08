Build Systems
==================

Gradle
------------

We don't run `javac` or `jar` directly. Instead, we use a build system called `gradle`. Gradle is a build system that is used to compile, test, and package the app. It is also used to manage dependencies and run tasks, allowing us to bring in external code.
The control hub runs Android, which is oddly common in the robotics world, but we don't write an entire android app as FIRST has helpfully provided boilerplate code for us.
The real app (i.e. the android activity) is stored in `FtcRobotController`. This project essential wraps around our code and ensures that basic robot functions like telemetry work.

.. danger::

    Do not modify the `FtcRobotController` project. This is legal, but the benefits of doing this are dubious.

Concepts
^^^^^^^^^^^^^

- Min SDK Version: The minimum version of Android that the app will run on. This is set to 25 because the control hub runs that version.
- Compile SDK Version: The version of Android that the app is compiled against. This can be as high as you'd like it to be.
- Target SDK Version: The version of Android that the app is targeted towards. This can be as high as you'd like it to be, but it should be less than or equal to the compile sdk version. It should preferably be equal to the compile sdk version.
- Gradle: A build system for java projects. It is used to compile, test, and package the app.
- Gradle Wrapper: A script that downloads and runs a specific version of gradle. This is used to ensure that everyone is using the same version of gradle.
- Android Gradle Plugin: A plugin for gradle that adds support for building android apps. This allows gradle to output an `apk`, which is then installed on the robot.

The web logs should output the SDK version of the control hub on initialization.

.. note::

    The SDK location is stored in `local.properties`.

Files
^^^^^^^^^^^^^^^

- `build.gradle`: The main build file for the project. This file is used to configure the project and its subprojects. You can upgrade the Android Gradle Plugin version here.
- `build.dependencies.gradle`: A file that contains all of the dependencies for the project. This file is used to keep the `build.gradle` file clean and storTes all the default FIRST dependencies.
- `build.common.gradle`: A file that contains all of the common configurations for the project. This is shared between the `eamCode` and `FtcRobotController` projects.
- `settings.gradle`: A file that is used to include or exclude subprojects from the build. This file is used to include the `TeamCode` and `FtcRobotController` projects in the build. If you want to add more subprojects, you must add a include directive here.
- `TeamCode/build.gradle`: The build file for the `TeamCode` project. This file is used to configure the `TeamCode` project. Any project specific modifications should be put here.

Dependencies
_____________________
