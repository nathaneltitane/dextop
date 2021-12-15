# Linux on Android -  Termux // Dextop // Ubuntu

Version: 12-03-2021
 
![termux dextop](https://github.com/nathaneltitane/dextop/blob/master/dextop.png?raw=true)

Dextop turns your modern Android device into a full workstation in a matter of minutes without all the hassle of technical know-how or having to dig through the internet to get it to work: Dextop is easy and user friendly.

Comparison in between Dextop and other projects:

- It provides you with a selection of the Ubuntu distribution base images: stable, popular and user-friendly knowledge bases.
- It expands the installed base image to run just like a normal PC installation.
- It creates a user profile for secure access and a home directory for you to work in.
- It installs all the necessary applications and utilities to provide you with the right experience.
- It sets up your internal (and external, when available) storage media for flexible, system-wide access.
- It handles all the technical intricacies related to a container (chroot/proot) installation so that you do not have to bother with them and get right to work.
- It is configured as a transient container system: it talks to Android via the Termux shell to access Android and launch relevant viewers and applications for you.
- It uses [console](https://github.com/nathaneltitane/console), a custom shell parser to handle the setup, colorize prompts and provide the user with an elegant, comprehensive and user-friendly experience.

Dextop is very quick and efficient:
Choose between i3WM or XFCE4 to get your work done or keep the base install for command line interface and programming workflows.

### Note:

Compositing should be disabled under XFCE4 to optimize resource usage and prevent display tearing and other glitches.
Turning compositing off allows for the best possible performance and experience in accordance to current Android system and security limitations:
This is required due to the Android user space runtime policy and limited hardware access: there is no graphics hardware acceleration available - the container graphics are emulated and run using LLVM.

### Power users be warned:

- Dextop does not install or configure sound output or advanced mail services!
- Dextop does not root your device!
- Dextop does not load any services or backends!
- Dextop only loads applications as needed to keep a minimal footprint!

Dextop is made, tested and optimized to run in tandem with Samsung's Dex: music, mail and web browsing should preferably be taken care of using native Android applications that are readily installed and configured on your device.

Services backend and other advanced features that require access to restricted core system directories will fail: you must root your device to remove those limitations and gain access to all system directories.

### Hardware requirements:

- Modern Android device (running Android 7.0+: this is a Termux limitation)
- Mouse (bluetooth or other)
- Keyboard (bluetooth or other)
- Power source (for extended work periods and performance requirements: Samsung Dex limitation)
- Monitor (highly recommended for phones and small devices)
- Internet connectivity (wifi or other: for setup, updates and additional package downloads)

### Software requirements:

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

`curl -sL run.dxtp.app > dextop && bash dextop | <option>``


Container install options are:

`-i | --i3wm      I3WM setup: install i3 window manager and utilities.                                [ Default ]`

`-x | --xfce      XFCE4 setup: install XFCE desktop environment and utilities.`

`-n | --none      No DE setup: console access to environment and utilities.`


`-b | --base      Base setup: download and install base distribution image only.                                 `

`-f | --full      Full setup: download and install full desktop environment and utilities.            [ Default ]`

`-u | --update    Package update: check/download/install Termux and Termux API package updates.`


By selecting the 'none' option, Dextop automatically sets up minimal defaults to a 'base' install.
The 'none' option is great for users who would like to experiment or setup their own window manager/desktop environment, utilities and preferences.

The 'update' option runs a Termux package check and lets you update both Termux (com.termux) and Termux API (com.termux.api) via direct download from F-Droid when available.

### Process summary:

**Be attentive!**

Dextop now automatically detects and processes any external media mounts and adds them to your container.

**User input is still required to give Termux storage access permissions and this can only be done through user interaction. There are no workarounds.**

You can press 'Allow' any time during the setup to grant this permission.

User information and distribution preferences are captured to set up the container's user profiles and home directories:
The rest of the setup is fully automated and should run its course until the container is ready for you to use.

### Setup breakdown:

- Dextop setup:
   - Termux setup:
      - Set up Termux (com.termux) and Termux API (com.termux.api) package update [ Optional ]
      - Set up Termux properties
      - Set up Termux storage access
      - Set up Termux shell configurations
      - Set up Termux silent login
      - Set up Termux login welcome message
      - Set up Termux package repositories
      - Set up Termux required packages
      - Set up Termux directory, file and utility links
      - Mark Termux setup checkpoint
      - Clean up Termux setup
   - Container setup:
      - Check device architecture
      - Gather setup information
      - Select distribution type and version
      - Set up distribution image and container
      - Set up dangling group IDs into container
      - Set up container environemnt
      - Set up container network connectivity
      - Set up container library preload
      - Mark Proot setup checkpoint
      - Set up container setup completion routine
      - CONTAINER LOGIN - 'root'
         - Set up container user account
         - Set up container user's superuser privileges
         - Set up container shell configurations
         - Set up container silent login
         - Set up container login welcome message
         - Set up container image expansion
         - Set up container package repositories
         - Set up container required packages
         - Set up container directory, file and utility links
         - Clean up container setup
      - User setup:
         - Mark user setup checkpoint
         - Set up user setup completion routine
         - PROOT LOGIN - 'root'
            - Set up user configuration routine
            - Set up user required packages
            - Set up user addons (directories, files and utilities)
            - Clean up user setup
      - VNC setup:
         - Set up vnc environment
         - Mark vnc setup checkpoint
         - Clean vnc setup

- CONTAINER LOGIN - 'user'
   - Set up user configuration routine
      - Configure keyboard
      - Configure locales
      - Configure timezones

### Customization:

Edit the  'user_list' array in the 'container-packages' file prior to starting the setup to customize your list of installed applications, libraries, frameworks, utilities and other third party package locations.

**You can modify any of the other scripts AT YOUR OWN RISK!**
**Any modification of the Dextop setup routine scripts implies you are fully aware of potential breakage and the consequences of doing so:**
**No bug report that stems from such action will be acknowledged and closed immediately!**

### Usage:

To access your newly created container:

`container-session -u <username> | -a <application> | <option>'` to start your session, run a specific application or setup session options on load.

### The fun begins:

When logging into the container for the first time, a one-time configuration runs on your first login to set up your keyboard, locales and timezone preferences.

The vnc session manager requires you to select your preferred display resolution for the best display experience.

To stop the vnc server and halt the display output, type `'container-vnc -x'`.
To start the vnc server and restart the display output, type `'container-vnc -o'`.

The next login will automatically launch the session for you using the settings you've chosen previously:
The first login saves the selection under `"${HOME}"/.vnc/selection` and uses it to start the VNC server and viewer automatically for your convenience!

Logging out by pressing Ctrl+D or by typing `'logout'` or `'exit'` will automatically stop the vnc session and exit the container back to the Termux shell.

### Reports:

All setup dialogs, prompts, commands and binary execution outputs have been set to redirect to the Termux `'/var/log'` directory to keep output messages to a minimum.
Should you suspect any issues or errors, please provide a copy of the files located under the Termux `'/var/log'` directory when submitting a bug report.