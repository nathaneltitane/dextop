![dextop](https://raw.githubusercontent.com/nathaneltitane/dextop/main/dextop.svg)

[![Donate](https://img.shields.io/badge/Donate-PayPal-2f343f.svg?style=for-the-badge)](https://www.paypal.com/donate/?hosted_button_id=2WZT7PCW3XDX6)

[[ Dextop // Project Page ]](https://github.com/nathaneltitane/dextop) [ Version // 06-26-2023 ]

---

### [ NOTICE // 06-26-2023 ]

**Added Termux:X11 display support and utilities update routine!**

### Welcome to [Dextop](https://dextop.app)

Dextop turns your modern Android device into a complete Linux-based distribution workstation in a matter of minutes!
No hassle or deep technical know-how required: **Dextop is easy and user friendly.**

Dextop was developed using a Samsung Galaxy Note 20 Ultra, a Samsung Galaxy Tab S7+ and optimized to run within/alongside Samsung DeX.

### Before you proceed:

To run the way it does and transition seamlessly in between Termux and the container instance of your choice, Dextop is built a certain way: it loads and links scripts, configuration files and utilities to enhance your Android-based workstation experience.

It is highly recommended to install Dextop on a fresh Termux instance or profile to benefit from a clean slate and a snappy experience, although you can always attempt deploying it on an already existing setup.

**Backing up your existing setup by following the [Termux backup recommendations](https://wiki.termux.com/wiki/Backing_up_Termux) is a must as the Dextop project will not be held responsible for any overrides, file corruptions or deletions caused by the installation and configuration process - You Have Been Warned.**

A few other elements to note before proceeding:

- Dextop installs certain core utilities to load and use a custom scripting library to make the overall command line interface more pleasant and informative:
  - ~/.local/bin/frobulator
- Dextop sets up all required items for it to function, aside from the container you choose, under the home directory
- Dextop looks and behaves the way it does because it loads/links a specific set of Termux preferences and properties:
  - ~/.termux/colors.properties    → ~/.local/bin/termux-colors
  - ~/.termux/font.ttf             → ~/.local/bin/termux-font
  - ~/.termux/termux.properties    → ~/.local/bin/termux-properties
- Dextop is BASH-centric and and may not play well with other shell setups and loads/links its own set of BASH configurations:
  - ~/.bashrc            → ~/.local/bin/bash-configuration
  - ~/.bash_aliases      → ~/.local/bin/bash-aliases
  - ~/.bash_functions    → ~/.local/bin/bash-functions
  - ~/.bash_login        → ~/.local/bin/bash-login
  - ~/.bash_logout       → ~/.local/bin/bash-logout
  - ~/.bash_profile      → ~/.local/bin/bash-profile

### Customization:

**All of the above files can be changed or customized and serve as a good base to start if there are no configurations or preferences already set.**

**You can modify any of the other scripts and utilities as well,  AT YOUR OWN RISK!**
**Any modification of the Dextop setup routine scripts implies you are fully aware of potential breakage and the consequences of doing so:**
**Any bug report that stems from such action will be acknowledged and will be closed immediately!**

### Environment:

Dextop is very quick and efficient:

Choose between a complete XFCE4 setup to get your work done, or keep the base install for command line interface and programming workflows.

**Compositing is and should remain disabled with XFCE4 to optimize resource usage and prevent display tearing and other glitches.**

Turning compositing off allows for the best possible performance and experience in accordance to current Android system and security limitations:
This is required due to the Android user space runtime policy and limited hardware access: there is no graphics hardware acceleration available - the container graphics are emulated and run using LLVM.

### What it does:

Dextop can be compared to other very similar projects, though:

- It provides you with a selection of the Ubuntu distribution base images: stable, popular and user-friendly knowledge bases.
- It expands the installed base image to run **just like a normal PC!**.
- It **generates an actual user profile and prepares a functional home directory for you to work in**, easily and securely.
- It installs all the necessary applications and utilities to provide you with the right experience.
- It sets up your internal (and external, when available) storage media for flexible, system-wide access.
- It **handles all the technical intricacies related to a container installation** (chroot/proot) so that you do not have to bother with them and get right to work.
- It is configured as a transient container system: it talks to Android via the Termux shell to access Android and launch relevant viewers and applications for you.

![dextop-session](https://raw.githubusercontent.com/nathaneltitane/dextop/master/dextop-session.png)

### What is doesn't:

Power users be warned! As efficient and well rounded as it may be:

- Dextop does not root your device!
- Dextop does not load any services or backends!
- Dextop does not install or configure advanced system services!

Applications that require backend services (i.e.: Ubuntu Snap/snapd), standalone services, hardware probes and other advanced features that require access to restricted core system directories will not function: you must root your device to remove those limitations and gain full access to all system devices.

Dextop links the modified utilities that have been patched under Termux for some limited access to whatever the Android user space runtime policy permits (htop, kill, pgrep, pkill, ps, top).

### Activities:

**Dextop only loads applications as needed: this helps keep a minimal footprint and your device running as smooth as possible!**

Music, mail, games and web browsing activities should preferably be taken care of using native Android applications that are readily installed and configured on your device.

### Interface:

Dextop offers two methods to turn an Android device into a desktop workstation and provide access to both the Termux and container side using a graphical interface.

The VNC method uses the X11 virtual framebuffer 'xvfb' alongside the X11 VNC server 'x11vnc' and forwards a display port within your device as 'localhost' to minimize latency and runs it using software emulated acceleration (LLVM).

The X11 method uses a native display server application 'termux-x11' alongside the Termux:X11 android application package and forwards the display using your device's native resolution and DPI settings using your device' hardware platform (GPU).

In either case, you can think of the experience as setting up a VM (virtual machine) on a typical laptop or desktop computer and accessing it through a viewer.


```
┌─────────────────────────────────────────────────────────────────────────────────────────────┐
│                                                                                             │
│ Device ///////////////////////////////////////////////////////////////////////////////////  │
│                                                                                             │
│  ┌───────────────────────────────────────────────────────────────────┐  ┌────────────────┐  │
│  │                                                                   ◄──┤                │  │
│  │ Firmware                                                          │  │ Hardware       │  │
│  │                                                                   ├──►                │  │
│  └──────────────────────────────────────────────────────────────▲─┬──┘  │  ┌──────────┐  │  │
│                                                                 │ │     │  │ Sound    │  │  │
│  ┌──────────────────────────────────────────────────────────────┴─▼──┐  │  └──────────┘  │  │
│  │                                                                   │  │                │  │
│  │ Software                                                          │  │  ┌──────────┐  │  │
│  │                                                                   │  │  │ Power    │  │  │
│  │  ┌─────────────────────────────────────────────────────────────┐  │  │  └──────────┘  │  │
│  │  │                                                             │  │  │                │  │
│  │  │ Android OS                                                  │  │  │  ┌──────────┐  │  │
│  │  │                                                             │  │  │  │ . . .    │  │  │
│  │  │  ┌───────────────────────────────────────────────────────┐  │  │  │  └──────────┘  │  │
│  │  │  │                                                       │  │  │  │                │  │
│  │  │  │  Termux Application                                   │  │  │  │  ┌──────────┐  │  │
│  │  │  │                                                       │  │  │  │  │ Cameras  │  │  │
│  │  │  │  ┌────────────────────────────┐  ┌─────────────────┐  │  │  │  │  └──────────┘  │  │
│  │  │  │  │                            │  │                 │  │  │  │  │                │  │
│  │  │  │  │  Termux System             ◄──┤ Activity        │  │  │  │  │  ┌──────────┐  │  │
│  │  │  │  │                            │  │ Manager         │  │  │  │  │  │ Display  │  │  │
│  │  │  │  │  ┌─────────────────▲────┐  ├──►                 │  │  │  │  │  └──────────┘  │  │
│  │  │  │  │  │                 │    │  │  │                 │  │  │  │  │                │  │
│  │  │  │  │  │ Home Directory  │    │  │  └─────────────▲─┬─┘  │  │  │  │  ┌──────────┐  │  │
│  │  │  │  │  │                 │    │  │                │ │    │  │  │  │  │ APU      │  │  │
│  │  │  │  │  │  ┌──────────────┴─┐  │  │  ┌─────────────┼─┼────┘  │  │  │  └──────────┘  │  │
│  │  │  │  │  │  │                │  │  │  │             │ │       │  │  │                │  │
│  │  │  │  │  │  │ Dextop         │  │  │  │  ┌──────────┴─▼────┐  │  │  │  ┌──────────┐  │  │
│  │  │  │  │  │  │                │  │  │  │  │                 │  │  │  │  │ RAM      │  │  │
│  │  │  │  │  │  └──▲─────────┬─┬─┘  │  │  │  │ Termux          │  │  │  │  └──────────┘  │  │
│  │  │  │  │  │     │         │ │    │  │  │  │ X11             │  │  │  │                │  │
│  │  │  │  │  │  ┌──┴─────────┼─▼─┐  │  │  │  │                 │  │  │  │  ┌──────────┐  │  │
│  │  │  │  │  │  │            │   │  │  │  │  │                 │  │  │  │  │ ROM      │  │  │
│  │  │  │  │  │  │ Frobulator │   │  │  │  │  │                 │  │  │  │  └──────────┘  │  │
│  │  │  │  │  │  │            │   │  │  │  │  └──────────▲─┬────┘  │  │  │                │  │
│  │  │  │  │  │  └────────────┼───┘  │  │  │             │ │       │  │  │  ┌──────────┐  │  │
│  │  │  │  │  │               │      │  │  │  ┌──────────┴─▼────┐  │  │  │  │ Storage  │  │  │
│  │  │  │  │  └──▲────────────┼──────┘  │  │  │                 │  │  │  │  └──────────┘  │  │
│  │  │  │  │     │            │         │  │  │ Termux          │  │  │  │                │  │
│  │  │  │  │  ┌──┴────────────▼──────┐  │  │  │ API             │  │  │  │  ┌──────────┐  │  │
│  │  │  │  │  │                      │  │  │  │                 │  │  │  │  │ Sensors  │  │  │
│  │  │  │  │  │ Container System     │  │  │  │                 │  │  │  │  └──────────┘  │  │
│  │  │  │  │  │                      │  │  │  │                 │  │  │  │                │  │
│  │  │  │  │  └──────────────────────┘  │  ◄──┤                 ◄──┼──┼──┤  ┌──────────┐  │  │
│  │  │  │  │                            │  │  │                 │  │  │  │  │ Comms    │  │  │
│  │  │  │  └────────────────────────────┘  ├──►                 ├──┼──►  │  └──────────┘  │  │
│  │  │  │                                  │  │                 │  │  │  │                │  │
│  │  │  └──────────────────────────────────┘  └─────────────────┘  │  ◄──┤  ┌──────────┐  │  │
│  │  │                                                             │  │  │  │ Addons   │  │  │
│  │  └─────────────────────────────────────────────────────────────┘  ├──►  └──────────┘  │  │
│  │                                                                   │  │                │  │
│  └───────────────────────────────────────────────────────────────────┘  └────────────────┘  │
│                                                                                             │
└─────────────────────────────────────────────────────────────────────────────────────────────┘
```

### Hardware requirements:

For the best possible experience, make sure to have:

- A modern Android device with 64 bit ARM processor (Android 7.0 or above: Termux limitation - Avoid Android 11/12/13 when and if possible: [Phantom Process Killer](https://issuetracker.google.com/issues/205156966))
- Approximately 4GB in free storage on the device for symmetric setup (Termux and distribution container)
- A mouse (bluetooth or other)
- A keyboard (bluetooth or other)
- A power source other than your battery (for extended work periods and performance requirements: Samsung DeX limitation)
- A monitor (highly recommended for phones and small devices)
- Medium to high speed internet connectivity (wifi or other: for setup, updates and additional package downloads)

### Software requirements:

Before you begin, please note that:

**Termux application downloads are to be made via F-Droid: Google Play Store updates are deprecated since November 2020**

**Android packages require that the 'Install Unknown apps' permission be enabled for the Termux application:**

To enable this permission, navigate into Settings → Security and Privacy → Install unknown apps → Termux and toggling the switch on.

To get Dextop set up, install the following packages on your android device:

- [Termux](https://f-droid.org/en/packages/com.termux/ "Termux by Fredrik Fornwall")
- [Termux API](https://f-droid.org/en/packages/com.termux.api/ "Termux API by Fredrik Fornwall")
- A VNC viewer application with full screen or immersive capabillities for a better experience such as:
   - [Remotix](https://play.google.com/store/apps/details?id=com.nulana.android.remotix "Remotix Remote Desktop by Nulana")
   - [VNC Viewer ](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android "VNC Viewer by RealVNC Ltd.")
   - [bVNC](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC "bVNC by Iordan Iordanov")

### Setup:

Once the Android applications are installed on your device, open Termux and paste or type:

```
curl -s -L run.dxtp.app > dextop && bash dextop
```

Container install options are:

```
-c, --console        Setup Console access to environment and utilities.
```

```
-e, --environment    Setup desktop environment and utilities.              [ XFCE ] [ Default ]
```

The 'console' option is great for users who would like to experiment or setup their own window manager/desktop environment, utilities and preferences.

The 'environemnt' option lets you specify the DE you would like to set up.

It currently defaults to XFCE4 for the base setup or when no argument is passed (work in progress: more selections to come).

### Process summary:

**Be attentive!**

**User information and distribution preferences are captured throughout the setup process to set up the container's user profile, home directory and other parameters.**

Most of the setup process is fully automated and should run its course until the container is ready for you to use.

Dextop automatically detects and processes any external media mounts, adds them to your container and labels them in your file browser's [bookmarks file](https://www.freedesktop.org/wiki/Specifications/desktop-bookmark-spec/).

**User input is still required to give Termux storage and installation access permissions when required and this can only be done through user interaction.**

**There are no workarounds!**

---

Storage:

Press 'Allow' when prompted during the setup to grant the storage permission.

Display:

Press 'Install' when prompted during the setup to install the display server components.

### Usage:

All utilities created for, loaded, and used by desktop contain a help argument. Please refer to the help dialogs before opening a bug report.

### Starting a session:

To start a session and access the newly generated container, paste or type:

```
container-session -o <display server> | -u <username> | -a <application>
```

To access the desktop environment installed directly under Termux (recognizable by the green username prompt), paste or type:

```
container-session -o <display server>
```

To acess the container housing distribution you've selected (recognizable by the fuschia username prompt), paste or type:

```
container-session -o <display server> -u termux
```

To start the session using the vnc display server (x11vnc) and restart the display output, paste or type:

```
container-session -o vnc
```

If using the native X11 display server (termux-x11), paste or type:

```
container-session -o x11
```

### Session notes:

**User 'termux' is the default username that is utilized during the automatic container setup.**
It is used to identify a default user under the distribution image you've selected and can be edited after setup.
Other users can be added by using the 'container-user' utility.

When accessing the container for the very first time, a one-time configuration runs on login to set up your keyboard, locales and timezone preferences.

If using the vnc display server (x11vnc), the vnc session manager requires you to select your preferred display resolution for the best display experience:
The selection is saved under ```"${HOME}"/.vnc/selection``` and the login routine uses it to start the VNC server and viewer automatically for your convenience!

The next login will automatically launch the session using the selection you've chosen previously. To override the selection, paste or type:

```
container-session -n vnc
```

### Stopping a session:

To stop the active session using the vnc display server by halting the vnc display server, paste or type:

```
container-session -x
```

To log out, press Ctrl+D or type ```'logout'``` or ```'exit'``` for the session to immediately stop the vnc server and exit:

Depending on the shell level in use at the time the command is executed, the container exits back to the Termux shell (recognizable by the green username prompt), or to the Android home screen.

### Utilities:

As the project evolves, certain utilities may change, either slightly or significantly and some new utilities may be introduced into the Dextop ecosystem.

To ensure Dextop runs as expected, and wth the latest features in tow, proceed as follows:

For new installations, run the normal setup routine and follow instructions as they appear (refer to the setup section).

For existing installations, manual updates can be run by downloading and executing the update routine from the latest Dextop deployment script.

To do so, paste or type:

```
curl -s -L run.dxtp.app > dextop && bash dextop -u dextop
```

To add Termux X11 server features, after running the main update routine as shown, run 'termux-display' and follow instructions as they appear.

Once the latest version of Dextop is deployed, configuring it to fetch all the latest and relevant utilities is possiblewhen automatic updates on login are enabled.

Automatic utility updates on login can be enabled as follows:

```
echo update > "${HOME}"/.dextop/dextop-update
```

Automatic utility updates on login can be disabled as follows:

```
echo '' > "${HOME}"/.dextop/dextop-update
```

### Audio:

**Audio playback is configured and supported through 'pulseaudio, although it is not recommended for use as it can be process and cycle intensive on the device's battery and processor(s):**
latency on playback may vary depending on the host device's hardware specification, and depending on if it is running directly under the Termux shell or from within a distribution container.

Audio playback on login can be enabled as follows:

```
echo audio > "${HOME}"/.dextop/dextop-audio
```

Audio playback can be disabled as follows:

```
echo '' > "${HOME}"/.dextop/dextop-audio
```

### VNC termination:

Automatic vnc display shutdown on terminal exit can be enabled as follows:

```echo logout >> "${HOME}"/.dextop/dextop-logout```

Automatic vnc display shutdown on terminal exit can be disabled as follows:

```echo '' > "${HOME}"/.dextop/dextop-logout```

### Repositories:

[Frobulator](https://github.com/nathaneltitane/frobulator) to streamline the scripts and make redundant code a thing of the past.

[Termux](https://github.com/termux/termux-app) as the android shell provider application to make Dextop interface with your device.

[GNU/Bash](https://github.com/gitGNU/gnu_bash) as the shell environment on top of which the scripts function.

### Projects:

[[ Dextop // Project Page ]](https://github.com/nathaneltitane/dextop)

[[ Frobulator // Project Page ]](https://github.com/nathaneltitane/frobulator)

[[ L²CU // Project Page ]](https://github.com/nathaneltitane/l2cu)

[[ Lego // Linux // Project Page ]](https://github.com/nathaneltitane/legolinux)

[[ Nathanel + Titane // Project Page ]](https://github.com/nathaneltitane/nathaneltitane)

[[ Terminal // Project Page ]](https://github.com/nathaneltitane/terminal)

[[ Termux // Project Page ]](https://github.com/nathaneltitane/termux)

### Reports:

[Submit bug report or feature request](https://github.com/nathaneltitane/dextop/issues)

Note:

All setup dialogs, prompts, commands and binary execution outputs have been set to redirect to the ```'${PREFIX}/var/log'``` directory to keep output messages to a minimum.
Should you suspect any issues or errors, please provide a copy of those files when submitting a bug report.

---

[[ Dextop // Project Page ]](https://github.com/nathaneltitane/dextop) [ Version // 06-26-2023 ]

### Enjoying Dextop? Buy me a coffee to show your appreciation!

[![Donate](https://img.shields.io/badge/Donate-PayPal-2f343f.svg?style=for-the-badge)](https://www.paypal.com/donate/?hosted_button_id=2WZT7PCW3XDX6)
