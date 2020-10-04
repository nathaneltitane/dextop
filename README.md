# linux-dextop

This project provides any user owning a modern android device, the ability to setup their own Linux-based work environment and use it as their primary workstation.

### Requirements:
- Modern Android device (running android 7.0+ / Termux limitation)
- Mouse (bluetooth or other)
- Keyboard (bluetooth or other)
- Power source (for extended work periods and performance requirements)
- Monitor (highly recommended)
- Internet connectivity (for setup, updates and additional package downloads)

### Getting started:
- Install the [Termux](https://play.google.com/store/apps/details?id=com.termux "Termux by Fredrik Fornwall") application
- Install a VNC viewer application with full screen or immersive capabillities for a better experience such as [bVNC](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC "bVNC by Iordan Iordanov")

### Setup:

Once the Android applications are installed on your device, open Termux and paste

```
curl -sL dex.ntttn.me > setup && bash setup | <option> | <output>
```

where available install options are:

```
-f | --full:         download and install full desktop environment and utilities.
-m | --minimal:      download and install minimal set of utilities.                  [ Default ]
```

and additional optimized and precompiled arm64 applications can be downloaded using:

```
-a | --applications: download a set of optimized and precompiled arm64 applications. [ Default ]
```

available display output options are:

```
-c | --vnc:          download and setup vnc protocol display output.                 [ Default ]
-x | --xorg:         download and setup xorg/xrdp protocol display output.
```

The options flagged with the [ Default ] tag are automatically passed if no options have been explicitly set by the user.

### Note:
The setup speed greatly depends on your device model and internet connection speed.
Let the setup run and fetch all the required dependencies: it will prompt you for input once it is ready.
The rest of the setup is fully automated and should run its course until the proot environment is ready for you to use.

**Be attentive!**

**User input is required to capture necessary setup information and give Termux storage access permissions:**
**this can only be done through user interaction and there are no workarounds.**

### Process:
- The script goes through usual update and upgrade processes using apt to get the Termux system up to date and ready.
- Necessary dependencies, configurations and binaries are downloaded and set up in both the Termux and proot environment.
- Information is then captured to properly configure and setup a user environment in the proot.
- The base ubuntu image is downloaded, unpacked and setup from within the Termux environment.
- The setup transitions into the newly unpacked proot environment and proceeds with configuring and installing the rest of your setup.
- 
### Note:
The setup dialogs, prompts, comaands and binaries have been made to redirect all output to Termux's /var/log directory to keep the information stream to a minimum.
Should you suspect any issues or errors, please provide those files when submitting a bug report.

### Usage:
- Run ```'proot-launch <username>``` to start your session.
- Run ```'proot-launch <username> <application> ``` to start a specific application on session load.

When in the proot