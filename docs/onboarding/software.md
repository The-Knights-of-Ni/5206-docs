Software Onboarding {#software_onboarding}
=========================

Welcome to the software team! We’re glad to have you here.

This tutorial will help you download, install, and set up the software tools needed to the help contribute to the 5206 codebase.
One of our core values is inclusivity, so we want to make sure that anyone regardless of experience feels ready to participate.
Therefore, we’ve split this guide into two sections.

The first section describes how to install graphical (GUI) versions of all the apps needed.
Most new members will find this process easiest to follow and most convenient because it avoids the use of a terminal,
which is a way to issue text-based commands to control a computer.
Although the terminal is a widely useful tool that is used by programmers around the world, it is not necessary to use to participate in our team.

If you are already comfortable with the terminal,
the second section describes how to install all necessary programs,
centering around terminal-based applications when possible.
Make sure to follow the instructions for your specific operating system,
as the methods used might change depending on that.

During the software onboarding process, we will help you install two tools.
The first is an Integrated Development Environment (IDE),
which is a program that is used to write, debug, and deploy code.
The IDE we’ll be using is called Android Studio, although you are free to choose another IDE if you’re already comfortable using one.
The second tool is a program called Git, which is a Version Control Software (VCS) that we use to keep track of each member’s changes to the code.
Throughout the instructions, we’ll provide several links to outside articles explaining how each of the tools we install work.
We highly recommend that you carefully read each article, as the concepts explained there are fundamental to the operation of our team.

If you have any questions at all during the onboarding process, don’t hesitate to contact Ashwin, Alessandro, or Ethan on Slack.

\note TL;DR
Install Android Studio and Git. Create a GitHub account (or use your existing one) and send your username to either the Captain or the Software Lead.

## GitHub

Sign-up link:

https://github.com/signup


\important Be sure to send Ashwin your GitHub username on slack so that he can add you to the organization.


GitHub is an internet hosting service that allows programmers to store, manage, track and control their code using Git.
Effectively, it lets you store code online in an easier way that allows many people to collaborate.
We host all our code in an "organization" called "The-Knights-of-Ni" (https://github.com/The-Knights-of-Ni/).

Optionally, you can install GitHub Desktop to simplify using git [from the website](https://desktop.github.com/).
Terminal users can use ``brew install --cask github`` on macs, or ``winget install -e --id GitHub.GitHubDesktop`` on windows.

## Installation Instructions (No Terminal)

### Git

To install git visit https://git-scm.com/downloads.

Git is a Version Control System (VCS) that is used keep everyone’s version of the code up to date.
[Here](https://rogerdudler.github.io/git-guide/) is a basic Git tutorial that should help get you started.
https://www.vogella.com/tutorials/Git/article.html is a more in-depth tutorial.
For those more technically inclined, Git has [official documentation](https://git-scm.com/doc).

### IDE

Android Studio, our main IDE: https://developer.android.com/studio/

Extra Setup Instructions: https://developer.android.com/studio/install

If you prefer a different IDE, IntelliJ IDEA is a good alternative: https://www.jetbrains.com/idea/


Extra Setup Instructions: https://www.jetbrains.com/help/idea/installation-guide.html

\attention To use IntellJ IDEA for android development, you will need an educational license,
you can get one here: https://www.jetbrains.com/community/education/
You should use your school email to apply for the license.

\warning If you are using IntelliJ IDEA, be sure to use the "Ultimate" version, not the "Community" version,
as only the "Ultimate" version has support for Android development. The only way to obtain said "Ultimate"
edition is to apply for the aformentioned license.


An IDE, or Integrated Development Environment, is an app that lets programmers code on a single interface.
Basically, IDEs let you do all your coding in one space with features to streamline the process as much as possible.
We use Android Studio because it is a base Java IDE that comes with all of the necessary additions to deploy code onto the robot.

IntellJ Ultimate is a turbo charged version of Android studio with more features,
but it requires you to complete the application process, which may have to be manually validated by JetBrains.

\note It may be useful to have Android Studio installed, even if you prefer to use IntelliJ IDEA.
Sometimes building and sdk management breaks on IntelliJ, so it is useful to have a backup IDE.


## Installation Instructions (Terminal)

Please follow the following instructions to install Android Studio and Git using the command line.
We’ve provided separate instructions for Windows and Mac users, so make sure to follow the instructions for your specific operating system.
Before we begin, make sure to read this warning.

\attention <h3>Careful!</h3>
\attention **NEVER** copy and paste scripts from the internet into your terminal. Doing so runs the risk of compromising your computer
because it is possible for websites to inject malicious code that runs as soon as you paste it in.
If you are going to copy and paste a command into your terminal, make sure you understand _EXACTLY_ what the code is doing,
and make sure that you have complete trust in the source.

With that warning out of the way, let’s get started installing the software needed for our system.

### Windows

To install the necessary software on Windows, we will first install a package manager called ``winget``.
A package manager is a tool that automates the download and installation of other pieces of software,
and is generally safer and easier to use than ``.exe`` files because each program is published to a trusted repository.
Most modern Windows 10/11 systems should come with ``winget`` already installed. To check whether this is the case,
open the Command Prompt by hitting ``Win+R`` and typing ``cmd`` at the prompt. Once you’re there, type the following command and hit ``Enter``:

```
    winget
```

The entire thing should look like this:

```
    Microsoft Windows [Version 10.0.22631.2265]
    (c) Microsoft Corporation. All rights reserved.

    C:\Users\[your username]>winget
    Windows Package Manager v1.x.xxxx
    Copyright (c) Microsoft Corporation. All rights reserved.

    The winget command line utility enables installing applications and other packages from the command line.

    usage: winget  [<command>] [<options>]

    The following commands are available:
      install    Installs the given package
      show       Shows information about a package
      source     Manage sources of packages
      search     Find and show basic info of packages
      list       Display installed packages
      upgrade    Shows and performs available upgrades
      uninstall  Uninstalls the given package
      hash       Helper to hash installer files
      validate   Validates a manifest file
      settings   Open settings or set administrator settings
      features   Shows the status of experimental features
      export     Exports a list of the installed packages
      import     Installs all the packages in a file
      pin        Manage package pins

    For more details on a specific command, pass it the help argument. [-?]

    The following options are available:
      -v,--version              Display the version of the tool
      --info                    Display general info of the tool
      -?,--help                 Shows help about the selected command
      --wait                    Prompts the user to press any key before exiting
      --logs,--open-logs        Open the default logs location
      --verbose,--verbose-logs  Enables verbose logging for winget
      --disable-interactivity   Disable interactive prompts

    More help can be found at: https://aka.ms/winget-command-help

    C:\Users\[your username here]>
```
If you see an output that is similar to this, ``winget`` is ready to go. If you see something that looks like this:


    C:\Users\[your username here]>winget
    'winget' is not recognized as an internal or external command,
    operable program or batch file.

    C:\Users\[your username here]>


Then install ``winget`` by installing the
[App Installer](https://apps.microsoft.com/store/detail/app-installer/9NBLGGH4NNS1?hl=en-us&gl=us>) program, then close and reopen Command Prompt and try the above command again.

Next, issue the following commands using ``winget`` in the command prompt (hit ``Enter`` after each line):

```shell
    winget install -e --id Google.AndroidStudio
    winget install -e --id Git.Git
```

Alternative command for IntelliJ IDEA

```shell

    winget install -e --id JetBrains.IntelliJIDEA.Ultimate
```

If you would like to install IntelliJ IDEA, Visual Studio Code, or another IDE instead of Android Studio,
use [this website](https://winget.run/) to search for the relevant command, or download them from the official website directly.

Once you are done, setup Android Studio.

### Mac

Open the app called “Terminal”

Next type (or paste) the following into the terminal:

```shell
    which brew
```

If it says brew is not installed, you need to install brew. To install brew type:
```
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Next paste this text:

```shell
    brew install git
    brew install --cask android-studio
```

Now setup Android Studio.

## Setting up Android Studio

- Open Android Studio
- Click “Do not import settings”
- Use standard setup (click next and accept licenses as needed)
- Wait for the downloads to finish

\note For the purposes of developing for this club an android emulator is not needed.

\remark Check out https://developer.android.com/studio/install for more detailed instructions.


## Project Setup

1. Open Android Studio
2. Click “Get from VCS”
3. Use https://github.com/The-Knights-of-Ni/CenterStage.git for the url.

   \attention <h3>Git URL</h3>
   \attention The above url changes from year to year, so make sure to use the correct one.

   ![AndroidStudioStartPage](AndroidStudioStartPage.png)

4. Click “Clone”
5. The repo will open and load the Read Me.
6. Go to your Android Studio settings (File>Settings), go to Tools>External Tools click the plus button, then fill it out with this:

   Windows:

    ```
        Name: HUB connect over Wifi Direct
        Group: External tools
        Description: N/A
        Program: $ModuleSdkPath$/platform-tools/.\adb
        Arguments: connect 192.168.43.1:5555
        Working Directory: $ProjectFileDir$
    ```

   Other (Mac, Linux, *nix):

    ```
        Name: HUB connect over Wifi Direct
        Group: External tools
        Description: N/A
        Program: $ModuleSdkPath$/platform-tools/adb
        Arguments: connect 192.168.43.1:5555
        Working Directory: $ProjectFileDir$
    ```

   Then click done.

   ![AndroidStudioADBExternalTool](AndroidStudioADBExternalTool.png)

7. New UI setup: Again, go to your Android Studio or IntelliJ IDEA settings (File>Settings), go to Appearance and Behavior>New UI, then check the box next to ``New UI``. Restart the IDE when prompted.

\note This part is an optional quality-of-life improvement.

![EnablingNewUI](EnablingNewUI.png)


## Working with the Code

### No Terminal (Recommended for Beginners)

Make the appropriate changes to the code and then click the green check mark on the top right hand side of your screen to commit the changes.

![AndroidStudioCommit](AndroidStudioCommit.png)

Next write a message accurately summarizing the changes you have made to the code so that others can check at a glance what you did.

Finally click “Commit and Push” and use the default options.

\note This last step might require you to login with your GitHub credentials.

### Terminal

Make the appropriate changes to the code and then open your terminal in Android Studio/IntelliJ IDEA.

![OpenTerminalIntelliJ](OpenTerminalIntelliJ.png)

Next, with ``YOUR_COMMIT_MESSAGE`` being an accurate description of the changes you made to the code, type the commands


    git commit -a -m "YOUR_COMMIT_MESSAGE"
    git push

\note This last step might require you to login with your GitHub credentials. If so, please
contact Ashwin for help. GitHub does **not** allow you to login via the terminal git interface.


\note I (Ashwin) would recommend looking at a git tutorial and using the terminal.
However, I find that using the GUI is easier when writing commit messages
