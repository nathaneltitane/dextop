![dextop](https://raw.githubusercontent.com/nathaneltitane/dextop/master/dextop.svg)

[![Donate](https://img.shields.io/badge/Donate-PayPal-2f343f.svg?style=for-the-badge)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=QG58TMRHNSZAU)

[[ Dextop // Project Page ]](https://github.com/nathaneltitane/dextop) [ Version // 01-21-2022 ]

Welcome to Dextop!

Dextop turns your modern Android device into a complete Linux-based distribution workstation in a matter of minutes!
No hassle or deep technical know-how required: **Dextop is easy and user friendly.**

Comparison in between Dextop and other projects:

- It provides you with a selection of the Ubuntu distribution base images: stable, popular and user-friendly knowledge bases.
- It expands the installed base image to run just like a normal PC installation.
- It generates an actual user profile and prepares a functional home directory for you to work in, easily and securely.
- It installs all the necessary applications and utilities to provide you with the right experience.
- It sets up your internal (and external, when available) storage media for flexible, system-wide access.
- It handles all the technical intricacies related to a container (chroot/proot) installation so that you do not have to bother with them and get right to work.
- It is configured as a transient container system: it talks to Android via the Termux shell to access Android and launch relevant viewers and applications for you.
- It uses [console](https://raw.github.com/nathaneltitane/console), a custom shell parser to handle the setup, colorize prompts and provide the user with an elegant, comprehensive and user-friendly experience.

![dextop-session](https://raw.githubusercontent.com/nathaneltitane/dextop/master/dextop-session.png)

Dextop is very quick and efficient:
Choose between a complete XFCE4 setup to get your work done, or keep the base install for command line interface and programming workflows.

### Note:

Compositing should be disabled with XFCE4 to optimize resource usage and prevent display tearing and other glitches.
Turning compositing off allows for the best possible performance and experience in accordance to current Android system and security limitations:
This is required due to the Android user space runtime policy and limited hardware access: there is no graphics hardware acceleration available - the container graphics are emulated and run using LLVM.

### Power users be warned:

- Dextop does not root your device!
- Dextop does not load any services or backends!
- Dextop does not install or configure audio or advanced system services!

Dextop only loads applications as needed to keep a minimal footprint!

Dextop is made, tested and optimized to run in tandem with Samsung's Dex: music, mail and web browsing should preferably be taken care of using native Android applications that are readily installed and configured on your device.

Services, hardware probes and other advanced features that require access to restricted core system directories will not function: you must root your device to remove those limitations and gain full access to all system devices.

Dextop links the modified utilities that have been patched under Termux for some limited access to whatever the Android user space runtime policy permits (htop, kill, pgrep, pkill, ps, top).

### Hardware requirements:

- Modern Android device (Android 7.0+: Termux limitation)
- Mouse (bluetooth or other)
- Keyboard (bluetooth or other)
- Power source (for extended work periods and performance requirements: Samsung Dex limitation)
- Monitor (highly recommended for phones and small devices)
- Internet connectivity (wifi or other: for setup, updates and additional package downloads)

### Software requirements:

Install the following:

**Termux application downloads are to be made via F-Droid:**
**Google Play Store updates are deprecated since November 2020**

- [Termux](https://f-droid.org/en/packages/com.termux/ "Termux by Fredrik Fornwall")
- [Termux API](https://f-droid.org/en/packages/com.termux.api/ "Termux API by Fredrik Fornwall")
- A VNC viewer application with full screen or immersive capabillities for a better experience such as:
   - [Remotix](https://play.google.com/store/apps/details?id=com.nulana.android.remotix "Remotix Remote Desktop by Nulana")
   - [VNC Viewer ](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android "VNC Viewer by RealVNC Ltd.")
   - [bVNC](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC "bVNC by Iordan Iordanov")

### Setting things up:

Once the Android applications are installed on your device, open Termux and paste or type:

`curl -s -L run.dxtp.app > dextop && bash dextop`

Container install options are:

`-x, --xfce       XFCE4 setup: install XFCE desktop environment and utilities.    [ Default ]`

`-c, --console    No DE setup: console access to environment and utilities.`

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

`'container-session -u <username> | -a <application>'` to start your session directly or with an application on load.

### The fun begins:

When logging into the container for the first time, a one-time configuration runs on your first login to set up your keyboard, locales and timezone preferences.

The vnc session manager requires you to select your preferred display resolution for the best display experience.

To stop the vnc server and halt the display output, type `'container-session -x'`.
To start the vnc server and restart the display output, type `'container-session -o'`.

The next login will automatically launch the session for you using the settings you've chosen previously:
The first login saves the selection under `"${HOME}"/.vnc/selection` and uses it to start the VNC server and viewer automatically for your convenience!

Logging out by pressing Ctrl+D or by typing `'logout'` or `'exit'` will automatically stop the vnc session and exit the container back to the Termux shell.

### Utility updates:

Automatic utility updates on login can be enabled as follows:

`'echo update >> ${HOME}/.dextop/dextop-update'`

Dextop will automatically fetch all relevant utilities and replace them withthe up-to-date versions.

Automatic utility updates on login can be disabled as follows:

`'echo '' > ${HOME}/.dextop/dextop-update'`

### Reports:

All setup dialogs, prompts, commands and binary execution outputs have been set to redirect to the `'${PREFIX}/var/log'` directory to keep output messages to a minimum.
Should you suspect any issues or errors, please provide a copy of those files  when submitting a bug report.

[[ Dextop // Project Page ]](https://github.com/nathaneltitane/dextop) [ Version // 01-21-2022 ]

### Enjoying Dextop? Buy me a coffee to show your appreciation!

[![Donate](https://img.shields.io/badge/Donate-PayPal-2f343f.svg?style=for-the-badge)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=QG58TMRHNSZAU)
