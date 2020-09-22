# linux-dextop

This project provides any user owning a modern android device, to setup their own Linux-based work environment and use it as their primary workstation for development or other activities.

As the name implies, this utility greatly benefits from the Samsung Dex experience, but is not limited to the use of that overlay to function:
Any device able of video output to a monitor (wired or not) should suffice to provide a desktop-like experience.

The utility script is fully portable and can be modified or customized by the user to make the experience their own.

### Requirements:
- Modern android device (running android 7.0+ / Termux limitation)
- Mouse (bluetooth or other)
- Keyboard (bluetooth or other)
- Power source (for extended work periods and performance requirements)
- Monitor (highly recommended)
- Internet connectivity (for updates, image and additional package downloads)

### Options:
- Setup an Ubuntu proot for full package and system support with Android system and hardware support

### Getting started:
- Install the [Termux](https://play.google.com/store/apps/details?id=com.termux "Termux by Fredrik Fornwall") application
- Install a VNC viewer application with full screen or immersive capabillities for a better experience such as [bVNC](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC "bVNC by Iordan Iordanov")

Once the android applications are setup, open Termux and paste

```
curl -sL dex.ntttn.me > setup && bash setup | <option> | <output>
```

where available install options are:

```
-b | --base:    download and unpack root filesystem and utilities.
-f | --full:    download and install full desktop environment and utilities. [ Default - full setup when no option is selected ] 
-m | --minimal: download and install minimal set of utilities.
```
and available display output configurations are

```
-v | --vnc:     download and unpack root filesystem and utilities.
-x | --xorg:    download and install full desktop environment and utilities. [ Default - full setup when no option is selected ] 
```

The minimal setup option is ideal for running specific applications and their dependencies only (see Application mode).

### Note:
**Be attentive!**

Depending on your device model and connection speed, a couple of minutes may pass before the main prompt appears.

**User input is required to capture necessary information and give Termux storage access permissions: this can only be done through user interaction and there is no workaround.**

### Process:
- The script goes through usual update and upgrade processes using apt to get the Termux system up to date and ready.
- Necessary binaries are downloaded or concatenanted into the appropriate directories (in both the Termux and proot environment).
- Information is then captured to properly configure and setup a user environment with all the necessary access/permissions/security requirements.
- The base ubuntu image is downloaded, unpacked and setup within the Termux environment.
- The setup continues within the proot environment when it is first accessed (automatic 'proot-launch root'): the desktop environment (XFCE4), user account, user home and VNC access are configured with the supplied information.

### Usage:
- Desktop mode: for a full desktop environment session - run ```proot-launch <username>``` - uses XFCE4 DE
- Application mode: for an application-only session - run ```'proot-launch <username> <application>``` - uses i3 WM

### Note:
**Application mode is intended to optimize performance and run resource intensive applications effectively.**
