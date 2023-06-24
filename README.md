![dextop](https://raw.githubusercontent.com/nathaneltitane/dextop/main/dextop.svg)

[![Donate](https://img.shields.io/badge/Donate-PayPal-2f343f.svg?style=for-the-badge)](https://www.paypal.com/donate/?hosted_button_id=2WZT7PCW3XDX6)

[[ Dextop // Project Page ]](https://github.com/nathaneltitane/dextop) [ Version // 06-24-2023 ]

---

### [ NOTICE // 06-24-2023 ]

**Added Termux:X11 display support and utilities update routine!**

### Welcome to [Dextop](https://dextop.app)

Dextop turns your modern Android device into a complete Linux-based distribution workstation in a matter of minutes!
No hassle or deep technical know-how required: **Dextop is easy and user friendly.**

Dextop was developed using a Samsung Galaxy Note 20 Ultra and a Samsung Galaxy Tab S7+.
**It has been tested and optimized to run in tandem with Samsung's Dex platform.**

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

**All of the above files can be changed or customized to your linking and serve as a good base to start if you have no configurations or preferences already set.**

### What it does:

Dextop compared to other similar projects:

- It provides you with a selection of the Ubuntu distribution base images: stable, popular and user-friendly knowledge bases.
- It expands the installed base image to run just like a normal PC installation.
- It generates an actual user profile and prepares a functional home directory for you to work in, easily and securely.
- It installs all the necessary applications and utilities to provide you with the right experience.
- It sets up your internal (and external, when available) storage media for flexible, system-wide access.
- It handles all the technical intricacies related to a container (chroot/proot) installation so that you do not have to bother with them and get right to work.
- It is configured as a transient container system: it talks to Android via the Termux shell to access Android and launch relevant viewers and applications for you.

![dextop-session](https://raw.githubusercontent.com/nathaneltitane/dextop/master/dextop-session.png)

Dextop is very quick and efficient:

Choose between a complete XFCE4 setup to get your work done, or keep the base install for command line interface and programming workflows.

### Note:

**Compositing should be disabled with XFCE4 to optimize resource usage and prevent display tearing and other glitches.**

Turning compositing off allows for the best possible performance and experience in accordance to current Android system and security limitations:
This is required due to the Android user space runtime policy and limited hardware access: there is no graphics hardware acceleration available - the container graphics are emulated and run using LLVM.

### Power users be warned:

- Dextop does not root your device!
- Dextop does not load any services or backends!
- Dextop does not install or configure advanced system services!

Applications that require backend services (i.e.: Ubuntu Snap/snapd), standalone services, hardware probes and other advanced features that require access to restricted core system directories will not function: you must root your device to remove those limitations and gain full access to all system devices.

Dextop links the modified utilities that have been patched under Termux for some limited access to whatever the Android user space runtime policy permits (htop, kill, pgrep, pkill, ps, top).

**Dextop only loads applications as needed: this helps keep a minimal footprint and your device running as smooth as possible!**

**Music, mail and web browsing activities should preferably be taken care of using native Android applications that are readily installed and configured on your device.**

```
┌─────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                                                                                             │
│ Device ///////////////////////////////////////////////////////////////////////////////////////////////////  │
│                                                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────────────────┐  ┌──────────────────┐  │
│  │                                                                                 ◄──┤                  │  │
│  │ Firmware                                                                        │  │ Hardware         │  │
│  │                                                                                 ├──►                  │  │
│  └───────────────────────────────────────────────────────────────────────────▲──┬──┘  │  ┌────────────┐  │  │
│                                                                              │  │     │  │ Speakers   │  │  │
│  ┌───────────────────────────────────────────────────────────────────────────┴──▼──┐  │  └────────────┘  │  │
│  │                                                                                 │  │                  │  │
│  │ Software                                                                        │  │  ┌────────────┐  │  │
│  │                                                                                 │  │  │ Battery    │  │  │
│  │  ┌───────────────────────────────────────────────────────────────────────────┐  │  │  └────────────┘  │  │
│  │  │                                                                           │  │  │                  │  │
│  │  │ Android OS                                                                │  │  │  ┌────────────┐  │  │
│  │  │                                                                           │  │  │  │ Microphone │  │  │
│  │  │  ┌─────────────────────────────────────────────────────────────────────┐  │  │  │  └────────────┘  │  │
│  │  │  │                                                                     │  │  │  │                  │  │
│  │  │  │  Termux Application                                                 │  │  │  │  ┌────────────┐  │  │
│  │  │  │                                                                     │  │  │  │  │ Cameras    │  │  │
│  │  │  │  ┌───────────────────────────────┐    ┌───────────────────────────┐ │  │  │  │  └────────────┘  │  │
│  │  │  │  │                               │    │                           │ │  │  │  │                  │  │
│  │  │  │  │  Termux System                ◄────┤ Termux Activity Manager   │ │  │  │  │  ┌────────────┐  │  │
│  │  │  │  │                               │    │                           │ │  │  │  │  │ Display    │  │  │
│  │  │  │  │  ┌───────────────────▲─────┐  ├────►                           │ │  │  │  │  └────────────┘  │  │
│  │  │  │  │  │                   │     │  │    │                           │ │  │  │  │                  │  │
│  │  │  │  │  │ Home Directory    │     │  │    └─────────────────────▲──┬──┘ │  │  │  │  ┌────────────┐  │  │
│  │  │  │  │  │                   │     │  │                          │  │    │  │  │  │  │ APU        │  │  │
│  │  │  │  │  │  ┌────────────────┴──┐  │  │    ┌─────────────────────┼──┼────┘  │  │  │  └────────────┘  │  │
│  │  │  │  │  │  │                   │  │  │    │                     │  │       │  │  │                  │  │
│  │  │  │  │  │  │ Dextop            │  │  │    │  ┌──────────────────┴──▼────┐  │  │  │  ┌────────────┐  │  │
│  │  │  │  │  │  │                   │  │  │    │  │                          │  │  │  │  │ RAM        │  │  │
│  │  │  │  │  │  └──▲──────────┬──┬──┘  │  │    │  │ Termux API               │  │  │  │  └────────────┘  │  │
│  │  │  │  │  │     │          │  │     │  │    │  │                          │  │  │  │                  │  │
│  │  │  │  │  │  ┌──┴──────────┼──▼──┐  │  │    │  │                          │  │  │  │  ┌────────────┐  │  │
│  │  │  │  │  │  │             │     │  │  │    │  │                          │  │  │  │  │ ROM        │  │  │
│  │  │  │  │  │  │ Frobulator  │     │  │  │    │  │                          │  │  │  │  └────────────┘  │  │
│  │  │  │  │  │  │             │     │  │  │    │  │                          │  │  │  │                  │  │
│  │  │  │  │  │  └─────────────┼─────┘  │  │    │  │                          │  │  │  │  ┌────────────┐  │  │
│  │  │  │  │  │                │        │  │    │  │                          │  │  │  │  │ Storage    │  │  │
│  │  │  │  │  └──▲─────────────┼────────┘  │    │  │                          │  │  │  │  └────────────┘  │  │
│  │  │  │  │     │             │           │    │  │                          │  │  │  │                  │  │
│  │  │  │  │  ┌──┴─────────────▼────────┐  │    │  │                          │  │  │  │  ┌────────────┐  │  │
│  │  │  │  │  │                         │  │    │  │                          │  │  │  │  │ Sensors    │  │  │
│  │  │  │  │  │ Container System        │  │    │  │                          │  │  │  │  └────────────┘  │  │
│  │  │  │  │  │                         │  │    │  │                          │  │  │  │                  │  │
│  │  │  │  │  └─────────────────────────┘  │    ◄──┤                          ◄──┼──┼──┤  ┌────────────┐  │  │
│  │  │  │  │                               │    │  │                          │  │  │  │  │ Comms      │  │  │
│  │  │  │  └───────────────────────────────┘    ├──►                          ├──┼──►  │  └────────────┘  │  │
│  │  │  │                                       │  │                          │  │  │  │                  │  │
│  │  │  └───────────────────────────────────────┘  └──────────────────────────┘  │  ◄──┤  ┌────────────┐  │  │
│  │  │                                                                           │  │  │  │ Extensions │  │  │
│  │  └───────────────────────────────────────────────────────────────────────────┘  ├──►  └────────────┘  │  │
│  │                                                                                 │  │                  │  │
│  └─────────────────────────────────────────────────────────────────────────────────┘  └──────────────────┘  │
│                                                                                                             │
└─────────────────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### Hardware requirements:

- Modern Android device with 64 bit ARM processor (Android 7.0 or above: Termux limitation - Avoid Android 11 when and if possible: [Phantom Process Killer](https://issuetracker.google.com/issues/205156966))
- Approximately 4GB in free storage for symmetric setup (Termux and distribution container)
- Mouse (bluetooth or other)
- Keyboard (bluetooth or other)
- Power source (for extended work periods and performance requirements: Samsung Dex limitation)
- Monitor (highly recommended for phones and small devices)
- Internet connectivity (wifi or other: for setup, updates and additional package downloads)

### Software requirements:

Dextop uses the X11 virtual framebuffer 'xvfb' alongside the X11 VNC server 'x11vnc' to turn your Android device into a desktop workstation and let you access both the Termux and container side using a graphical interface.
Think of the experience as setting up a Virtual Machine on a normal computer and accessing it through the application's viewer.

To proceed, install the following on your android device:

- [Termux](https://f-droid.org/en/packages/com.termux/ "Termux by Fredrik Fornwall")
- [Termux API](https://f-droid.org/en/packages/com.termux.api/ "Termux API by Fredrik Fornwall")
- A VNC viewer application with full screen or immersive capabillities for a better experience such as:
   - [Remotix](https://play.google.com/store/apps/details?id=com.nulana.android.remotix "Remotix Remote Desktop by Nulana")
   - [VNC Viewer ](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android "VNC Viewer by RealVNC Ltd.")
   - [bVNC](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC "bVNC by Iordan Iordanov")

**Termux application downloads are to be made via F-Droid:**
**Google Play Store updates are deprecated since November 2020**

### Setting things up:

Once the Android applications are installed on your device, open Termux and paste or type:

`curl -s -L run.dxtp.app > dextop && bash dextop`

Container install options are:

`-c, --console        Setup Console access to environment and utilities.`

`-e, --environment    Setup desktop environment and utilities.              [ XFCE ] [ Default ]`

`-u, --update         Update application packages and utilities.            [ Dextop ] [ Termux ]`

The 'console' option is great for users who would like to experiment or setup their own window manager/desktop environment, utilities and preferences.

### Process summary:

Most of the setup process is fully automated and should run its course until the container is ready for you to use.

**Be attentive!**

**User information and distribution preferences are captured throughout the setup process to set up the container's user profile, home directory and other parameters.**

Dextop automatically detects and processes any external media mounts and adds them to your container.

**User input is still required to give Termux storage access permissions and this can only be done through user interaction. There are no workarounds!**

You should press 'Allow' when prompted during the setup to grant this permission.

### Customization:

**You can modify any of the other scripts AT YOUR OWN RISK!**
**Any modification of the Dextop setup routine scripts implies you are fully aware of potential breakage and the consequences of doing so:**
**No bug report that stems from such action will be acknowledged and will be closed immediately!**

### Usage:

To access your newly generated container:

`container-session -o | -u <username> | -a <application>` to start your session directly or with an application on load.

To access the desktop environment installed directly under Termux, type `container-session -o`: it is recognizable by the green username prompt.

To acess the linux distribution image you've selected, type `container-session -u termux` and then initialize the session with `container-session -o`: it is recognizable by the fuschia username prompt.

**The user 'termux' is the default username that is utilized during the automatic container setup.**

It is used to identify a default user under the Linux-based distribution image you've selected and can be edited.

Other users can be added using the 'container-user' utility.

### The fun begins:

When logging into the container for the first time, a one-time configuration runs on your first login to set up your keyboard, locales and timezone preferences.

If using the vnc display server, the vnc session manager requires you to select your preferred display resolution for the best display experience:

Start the session using the vnc display server and restart the display output by typing `container-session -o vnc`.

Stop the session using the vnc display server and halt the display output by typing `container-session -x`.

The next login will automatically launch the session for you using the settings you've chosen previously:
The first login saves the selection under `"${HOME}"/.vnc/selection` and uses it to start the VNC server and viewer automatically for your convenience!

If using the native X11 display server (termux-x11):

Start the session using the X11 display server by typing `container-session -o x11`.

Log out by pressing Ctrl+D or by typing `'logout'` or `'exit'`: the session will automatically stop the vnc server and exit the container back to the Termux shell.

### Utility updates:

Automatic utility updates on login can be enabled as follows:

`echo update > "${HOME}"/.dextop/dextop-update`

Dextop will automatically fetch all relevant utilities and replace them withthe up-to-date versions.

Automatic utility updates on login can be disabled as follows:

`echo '' > "${HOME}"/.dextop/dextop-update`

### Audio:

Audio playback is configured and supported through 'pulseaudio'.

It is not recommended for use as it is very battery and cpu intensive:
latency on playback may vary depending on your device's hardware specification and if running directly under the Termux shell or from within a container.

Audio playback on login can be enabled as follows:

`echo audio > "${HOME}"/.dextop/dextop-audio`

Audio playback can be disabled as follows:

`echo '' > "${HOME}"/.dextop/dextop-audio`

### Session logout:

Automatic vnc display shutdown on terminal exit can be enabled as follows:

`echo logout >> "${HOME}"/.dextop/dextop-logout`

Automatic vnc display shutdown on terminal exit  can be disabled as follows:

`echo '' > "${HOME}"/.dextop/dextop-logout`

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

All setup dialogs, prompts, commands and binary execution outputs have been set to redirect to the `'${PREFIX}/var/log'` directory to keep output messages to a minimum.
Should you suspect any issues or errors, please provide a copy of those files  when submitting a bug report.

---

[[ Dextop // Project Page ]](https://github.com/nathaneltitane/dextop) [ Version // 06-24-2023 ]

### Enjoying Dextop? Buy me a coffee to show your appreciation!

[![Donate](https://img.shields.io/badge/Donate-PayPal-2f343f.svg?style=for-the-badge)](https://www.paypal.com/donate/?hosted_button_id=2WZT7PCW3XDX6)
