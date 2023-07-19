![dextop](https://raw.githubusercontent.com/nathaneltitane/dextop/main/dextop.svg)

[![Donate](https://img.shields.io/badge/Donate-PayPal-2f343f.svg?style=for-the-badge)](https://www.paypal.com/donate/?hosted_button_id=2WZT7PCW3XDX6)

[[ Dextop // Project Page ]](https://github.com/nathaneltitane/dextop) [ Version // 07-19-2023 ]

---

### [ NOTICE // 07-19-2023 ]

- All setup issues debugged and fixed, streamlined assertions and default options, fixed container ROOT assertion issues using conatiner setup initialization!

### Welcome to [Dextop](https://dextop.app)

Dextop turns most modern Android devices into a complete Linux-based distribution workstation in a matter of minutes!
No hassle or deep technical know-how required: **Dextop is easy and user friendly.**

Dextop was developed using a Samsung Galaxy Note 20 Ultra, a Samsung Galaxy Tab S7+ and optimized to run within/alongside Samsung DeX.

### Contents

To run the way it does and transition seamlessly in between Termux and the chosen container instance, Dextop is built a certain way:
it loads and links scripts, configuration files and utilities to enhance the Android-based workstation experience

- Dextop installs certain core utilities to load and use a custom scripting library to make the overall command line interface more pleasant and informative:
  - ~/.local/bin/frobulator
- Dextop sets up all required items for it to function, aside from the container, under the home directory
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

### Before proceeding:

It is highly recommended to install Dextop on a fresh Termux instance or profile to benefit from a clean slate and a snappy experience, although you can always attempt deploying it on an already existing setup.

---

### Back. It. Up.

**Backing up your existing setup by following the [Termux backup recommendations](https://wiki.termux.com/wiki/Backing_up_Termux) is a must as the Dextop project will not be held responsible for any overrides, file corruptions or deletions caused by the installation and configuration process - You Have Been Warned.**

A backup routine has also been built that archives the user'S home directory before proceeding, regardless, to ensure some kind of safety.

---

### Customization:

**All of the above files can be changed or customized and serve as a good base to start if there are no configurations or preferences already set.**

**All scripts and utilities can be edited or modified to benefit from a more customized experience and the Dextop project releases itself for any responibility regarding hardware failure or loss of data when doing so!**
**Any modification of the Dextop setup routine, scripts or utilities implies the user is fully aware of potential hardware failure or breakage and/or loss of data, including the consequences of doing so:**
**Any bug report that stems from such action will not be acknowledged and will be closed immediately!**

### Environment:

Dextop is very quick and efficient:

Choose between a complete XFCE setup to get work done, or keep the base install for command line interface and programming workflows.

**Compositing is and should remain disabled with XFCE to optimize resource usage and prevent display tearing and other glitches.**

Turning compositing off allows for the best possible performance and experience in accordance to current Android system and security limitations:
This is required due to the Android user space runtime policy and limited hardware access: there is no graphics hardware acceleration available - the container graphics are emulated and run using LLVM.

### What it does:

Dextop can be compared to other very similar projects, though:

- It provides a selection of the Ubuntu distribution base images: stable, popular and have tons of user-friendly knowledge bases.
- It expands the installed base image to run **just like a normal PC!**
- It **generates an actual user profile and prepares a functional home directory for the user to work in**, easily and securely.
- It installs all the necessary applications and utilities to provide the user with the right experience.
- It sets up the internal (and external, when available) storage media for flexible, system-wide access.
- It **handles all the technical intricacies related to a container installation** (chroot/proot) so that the user does not have to bother with them and get right to work.
- It is configured as a transient container system: it talks to Android via the Termux shell to access Android and launch relevant viewers and applications as needed.

![dextop-session](https://raw.githubusercontent.com/nathaneltitane/dextop/master/dextop-session.png)

### What is doesn't:

Power users be warned! As efficient and well rounded as it may be:

- Dextop does not root the host device!
- Dextop does not load any services or backends!
- Dextop does not install or configure advanced system services!

Applications that require backend services (i.e.: Ubuntu Snap/snapd), standalone services, hardware probes and other advanced features that require access to restricted core system directories will not function: the device must bee rooted to remove those limitations and gain full access to all system hardware and virtual devices.

Dextop links some of the modified utilities that have been patched under Termux for an attempt at limited access to whatever the Android user space runtime policy permits (htop, kill, pgrep, pkill, ps, top).

### Activities:

**Dextop only loads applications as needed: this helps keep a minimal footprint and the host device running as smooth as possible!**

Music, mail, web browsing and gaming activities should preferably be taken care of using native Android applications as they interface with the device's hardware and provide acceleration and other desirable features. See additons.

![dextop-additions](https://raw.githubusercontent.com/nathaneltitane/dextop/master/dextop-additions.png)

### Interface:

Dextop offers two methods to turn an Android device into a desktop workstation and provide access to both the Termux and container side using a graphical interface.

The VNC method uses the X11 virtual framebuffer 'xvfb' alongside the X11 VNC server 'x11vnc' and forwards a display port within the device as 'localhost' to minimize latency and runs it using software emulated acceleration (LLVM).

The X11 method uses a native display server application 'termux-x11' alongside the Termux:X11 android application package and forwards the display using the device's native resolution and DPI settings using the device's hardware graphics platform (GPU).

In either case, the experience is extremely similar to setting up a virtual machine (VM) on a typical laptop or desktop computer and accessing it through a viewer.


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

- **A modern Android device equipped with a 64 bit ARM processor** (Android 7.0 or above: Termux limitation - Avoid Android 11/12/13 when and if possible: read more regarding the [Phantom Process Killer](https://issuetracker.google.com/issues/205156966))
- **Medium to high speed internet connectivity** (wifi or other: for setup, updates and additional package downloads)
- Approximately 4GB in free storage on the device for symmetric setup (Termux and distribution container)
- A mouse (bluetooth or other)
- A keyboard (bluetooth or other)
- A power source other than the battery (for extended work periods and performance requirements: Samsung DeX limitation)
- A monitor (highly recommended for phones and small devices)

### Software requirements:

Before beginning, please note that ** automated Android package installs require that the 'Install Unknown apps' permission be enabled for the Termux application:**

To enable this permission, navigate into Settings → Security and Privacy → Install unknown apps → Termux and toggling the switch on.

To get Dextop set up, install the following packages on the host Android device:

- [Termux](https://github.com/termux/termux-app/releases/download/v0.118.0/termux-app_v0.118.0+github-debug_arm64-v8a.apk "Termux by Fredrik Fornwall")
- A VNC viewer application with full screen or immersive capabillities for a better experience such as:
   - [Remotix](https://play.google.com/store/apps/details?id=com.nulana.android.remotix "Remotix Remote Desktop by Nulana")
   - [VNC Viewer ](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android "VNC Viewer by RealVNC Ltd.")
   - [bVNC](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC "bVNC by Iordan Iordanov")

### Setup:

Once the Android applications are installed on the device, open Termux and paste or type:

```
curl -s -L run.dxtp.app > dextop && bash dextop
```

The 'console' option is great for users who would like to experiment or setup their own window manager/desktop environment, utilities and preferences.

The 'environemnt' option lets the user specify the desktop environment (DE) to be set up and used.

It currently defaults to XFCE for the base setup or when no argument is passed (work in progress: more selections to come).

### Process summary:

**Be attentive!**

**User information and distribution preferences are captured throughout the setup process to set up the container's user profile, home directory and other parameters.**

Most of the setup process is fully automated and should run its course until the container is ready for the user to use.

Dextop automatically detects and processes any external media mounts, adds them to the working container and labels them adequately in the file browser's [bookmarks file](https://www.freedesktop.org/wiki/Specifications/desktop-bookmark-spec/).

**User input is still required to give Termux storage and installation access permissions when required and this can only be done through user interaction.**

**There are no workarounds!**

**Storage:**

Press 'Allow' when prompted during the setup to grant the storage permission.

**Additions:**

Press 'Install' when prompted during the setup to install the display server components.

### Additional packages:

The 'termux-additions' utility is part of the newest deployment and sets up the required Android packages to interface with the main Termux application, including Termux API, Termux GUI and Termux:X11.

These additions are fetched directly from their respective Termux project GitHub releases page: any previously installed version should be removed to not inherit any conflicting packaege signatures that may contribute to unexpected issues.

The display server, Termux:X11 will interface with the required 'termux-x11' package and provides Dextop with a native display solution on the host device, using the available DPI settings and running it through the hardware platform (with possibility of acceleration when it is compiled and enabled).

### Usage:

All utilities created for, loaded, and used by desktop contain a help argument. Please refer to the help dialogs before opening a bug report.

### Session start:

To start a session and access the newly generated container, paste or type:

```
container-session -o <display server> | -u <username> | -a <application>
```

To access the desktop environment installed directly under Termux (recognizable by the green username prompt), paste or type:

```
container-session -o <display server>
```

To access the container housing distribution that has been selected (recognizable by the fuschia username prompt), paste or type:

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
It is used to identify a default user under the distribution image that has been selected and can be edited after setup.
Other users can be added by using the 'container-user' utility.

When accessing the container for the very first time, a one-time configuration runs on login to set up the keyboard layout, locales and timezone preferences.

If using the vnc display server (x11vnc), the vnc session manager requires the user to select a preferred display resolution for the best display experience:
The selection is saved under ```"${HOME}"/.vnc/selection``` and the login routine uses it to start the VNC server and viewer automatically for your convenience!

The next login will automatically launch the session using the previously chosen selection. To override the selection, paste or type:

```
container-session -n vnc
```

### Session stop:

To stop the active session using the vnc display server by halting the vnc display server, paste or type:

```
container-session -x
```

To log out, press Ctrl+D or type ```'logout'``` or ```'exit'``` for the session to immediately stop the vnc server and exit:

Depending on the shell level in use at the time the command is executed, the container exits back to the Termux shell (recognizable by the green username prompt), or to the Android home screen.

### Utilities:

As the project evolves, certain utilities may change, either slightly or significantly and some new utilities may be introduced into the Dextop ecosystem.

To ensure Dextop runs as expected, and wth the latest features in tow, proceed as follows according to the existing setup:

**For new installations, run the normal setup routine and follow instructions as they appear (refer to the setup section).**

For existing installations, manual updates can be run by downloading and executing the update routine from the latest Dextop deployment script.

To do so, paste or type:

```
curl -s -L run.dxtp.app > dextop && bash dextop -u dextop
```

to update the main dextop utility.

To then update the utilities needed by Dextop, paste or type:

```
curl -s -L run.dxtp.app > dextop && bash dextop -u utilities
```

### Issues:

High latency internet connectivity or issues with accessing server content (GitHub) may cause some files to malfunction or go corrupt.

If for whatever reason an update fails due to an error of because of deployment script corruption, paste or type:

```
curl -s -L run.dxtp.app > "${HOME}"/.local/bin/dextop && bash dextop -u utilities
```

Once the latest version of Dextop is deployed, configuring it to fetch all the latest and relevant utilities is possiblewhen automatic updates on login are enabled.

Automatic utility updates on login can be enabled as follows:

```
echo update > "${HOME}"/.dextop/dextop-update
```

Automatic utility updates on login can be disabled as follows:

```
echo '' > "${HOME}"/.dextop/dextop-update
```
# Additions:

For the purpose of keeping the system load slim and light, setting up default applications via the use of 'dextop-additions' is highly recommended, and by doing so, 'dextop-additions' transfers mimetype requests for specific applications through the use of the Activity Manager and opens the relevant Android application for you to use.

'dextop-additions' handles activities:

```
dextop-additions -a <activity>
```

or takes care of mimetype handles:

```
dextop-additions -n <handle>
```

### Audio:

**Audio playback is configured and supported through 'pulseaudio', although it is not recommended for use as it can be process and cycle intensive on the device's battery and processor(s).**

Audio latency on playback and other such related parameters may vary depending on the host device's hardware specification, and depending on if it is running directly under the Termux shell or from within a distribution container.

Audio playback on login can be enabled as follows:

```
echo audio > "${HOME}"/.dextop/dextop-audio
```

Audio playback can be disabled as follows:

```
echo '' > "${HOME}"/.dextop/dextop-audio
```
### Termination:

Automatic session and display shutdown on terminal exit can be enabled as follows:

```echo logout >> "${HOME}"/.dextop/dextop-logout```

Automatic session and display shutdown on terminal exit can be disabled as follows:

```echo '' > "${HOME}"/.dextop/dextop-logout```

### Repositories:

[Frobulator](https://github.com/nathaneltitane/frobulator) to streamline the scripts and make redundant code a thing of the past.

[Termux](https://github.com/termux/termux-app) as the android shell provider application to make Dextop interface with the host device.

[Termux:X11](https://github.com/termux/termux-x11) as the android native display server provider.

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

[[ Dextop // Project Page ]](https://github.com/nathaneltitane/dextop) [ Version // 07-19-2023 ]

### Enjoying Dextop? Buy me a coffee to show your appreciation!

[![Donate](https://img.shields.io/badge/Donate-PayPal-2f343f.svg?style=for-the-badge)](https://www.paypal.com/donate/?hosted_button_id=2WZT7PCW3XDX6)
