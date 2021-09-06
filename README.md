# Linux on Android -  Termux // Dextop // Ubuntu
 
![termux dextop](https://github.com/nathaneltitane/dextop/blob/master/dextop.png?raw=true)

Dextop turns your modern Android device into a full workstation in a matter of minutes without all the hassle of technical know-how or having to dig through the internet to get it to work: Dextop is easy and user friendly.

Comparison in between Dextop and other projects:

- It provides you with an installation of Ubuntu 20.04 (LTS): stable, popular and user-friendly knowledge bases.
- It expands the installed base image to run just like a normal PC installation.
- It creates a user profile for secure access and a home directory for you to work in.
- It installs all the necessary applications and utilities to provide you with the right experience.
- It sets up your internal and external (when available) storage media for quick access.
- It handles all the technical intricacies related to a change root (chroot/proot) installation so that you do not have to bother with them and get right to work.
- It is configured as a transient change root system: it talks to Android via the Termux shell to access Android and launch your favorite viewer for you.
- It uses [console](https://github.com/nathaneltitane/console), a custom system to handle the setup, colorize prompts and proved the user with an elegant and user-friendly experience.

Dextop is very quick and efficient: choose between KDE5 or XFCE4 desktop environemnts to get your work done. They will provide all the necessary and familiar graphical utilities and applications for you to get your work done.

### Note:

Compositing must be disabled to optimize resource usage and prevent display bugs: this allows for the best possible performance and experience in accordance to current Android system and security limitations:
Disabling compositing is required due to the Android user-space runtime and limited hardware access: there is no graphics hardware acceleration available - the change root graphics are emulated and run using LLVM.

### Power users be warned:

- Dextop does not install or configure sound output or advanced mail services!
- Dextop does not root your device!
- Dextop does not have access to system process files!
- Dextop does not load any services or backends!
- Dextop only loads applications as needed to keep a minimal footprint!

Dextop is made to run in tandem with Samsung's Dex: music, mail and web browsing should preferably be taken care of using native Android applications that are readily installed and configured on your device.

Services backend and other advanced features that require access to restricted core system directories will fail: you must root your device to remove those limitations and gain access to all system directories.

### Hardware requirements:

- Modern Android device (running Android 7.0+: this is a Termux limitation)
- Mouse (bluetooth or other)
- Keyboard (bluetooth or other)
- Power source (for extended work periods and performance requirements: Samsung Dex limitation)
- Monitor (highly recommended for phones and small devices)
- Internet connectivity (wifi or other: for setup, updates and additional package downloads)

### Software requirements:

- [Termux](https://f-droid.org/en/packages/com.termux/ "Termux by Fredrik Fornwall")         via F-Droid - the Google Play Store version is deprecated since November 2020
- [Termux API](https://f-droid.org/en/packages/com.termux.api/ "Termux API by Fredrik Fornwall") via F-Droid - the Google Play Store version is deprecated since November 2020
- A VNC viewer application with full screen or immersive capabillities for a better experience such as:
   - [Remotix](https://play.google.com/store/apps/details?id=com.nulana.android.remotix "Remotix Remote Desktop by Nulana")
   - [VNC Viewer ](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android "VNC Viewer by RealVNC Ltd.")
   - [bVNC](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC "bVNC by Iordan Iordanov")

### Setting up:

Once the Android applications are installed on your device, open Termux and paste or type:

`curl -sL run.dxtp.app > dextop && bash dextop | <option>`

Available install options are:

`-k | --kde:     install K desktop environment and utilities (KDE5).                     [ Default ]`
`-x |--xfce:     install XFCE desktop environment and utilities (XFCE4).                            `

`-f | --full:    download and install full desktop environment, utilities and themes.               `
`-m | --minimal: download and install full desktop environment and utilities.            [ Default ]`

`-c | --core:    download and install core distribution image only.                                 `

### Process:

**Be attentive!**

**User input is required to give Termux storage access permissions:**
**this can only be done through user interaction and there are no workarounds.**

User information will be captured later on to set up profiles and home directories:
The rest of the setup is fully automated and should run its course until the proot container is ready for you to use.

- Dextop setup:
   - Termux setup:
      - Set up configurations,utilities, package dependencies and shell requirements
   - Proot setup:
      - Set up configurations, utilities, package dependencies and shell requirements
      - Set up proot container directories
      - Download, unpack and prepare core system image for use
      - Gather user information for successful setup
         - Initialize setup from within Termux
         - Enter blank proot container as 'root'
         - Expand system image for normal use
         - Login as root in newly created proot container
         - Finalize setup from within proot container
   - VNC setup:
      - Set up configurations, utilities and shell requirements
- Dextop setup exits to force reload all changes and greet you with your freshly installed dextop setup once Termux is reopened.

### Customization:

Use and edit 'dextop' prior to starting the setup to customize your list of installed applications, libraries, frameworks, utilities and other third party package locations.

### Usage:

To access your newly created proot container:

`'proot-session -u <username> | -a <application> | <option>'` to start your session, run a specific application or setup session options on load.

### The fun begins:

When logging into the proot container for the first time, you need to start the vnc server manually:
Type `'vnc-start'` and follow the prompt to select the appropriate device resolution settings for the Android device or external monitor.


The next login will automatically launch the session for you using the settings you've chosen previously:
The first login saves the selection under `"${HOME}"/.vnc/selection` and uses it to start the VNC server and viewer automatically for your convenience!

Logging out by pressing Ctrl+D or by typing `'logout'` or `'exit'``will automatically stop the vnc session and exit the proot container back to the Termux shell.

To stop the vnc server and halt the display output, type `'vnc-stop'`.
To start the vnc server and restart the display output, type `'vnc-start'`.

### Reports:

All setup dialogs, prompts, commands and binary execution outputs have been set to redirect to the Termux `'/var/log'` directory to keep output messages to a minimum.
Should you suspect any issues or errors, please provide a copy of the files located under the Termux `'/var/log'` directory when submitting a bug report.
