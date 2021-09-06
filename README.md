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

Compositing is disabled by default to optimize resource usage and prevent display bugs: this is done to give you the best possible performance and experience in accordance to Android hardware performance.

Disabling compositing is required due to Android user-space limitations and limited hardware access: there is no graphics hardware acceleration available - the change root graphics are emulated and run using LLVM.

### Power users be warned:

- Dextop does not install or configure sound output or advanced mail services!
- Dextop does not have access to system processes as it does not root your device!
- Dextop does not load any services: applications are run as needed to get the session running!

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

- [Termux](https://f-droid.org/en/packages/com.termux/ "Termux by Fredrik Fornwall") via F-Droid - the Google Play Store version is deprecated since November 2020
- A VNC viewer application with full screen or immersive capabillities for a better experience such as:
   - [Remotix](https://play.google.com/store/apps/details?id=com.nulana.android.remotix "Remotix Remote Desktop by Nulana")
   - [VNC Viewer ](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android "VNC Viewer by RealVNC Ltd.")
   - [bVNC](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC "bVNC by Iordan Iordanov")

### Setting up:

Once the Android applications are installed on your device, open Termux and paste or type:

`curl -sL run.dxtp.app > dextop && bash dextop | <option>`

Available install options are:

`-k | --kde:     install K desktop environment and utilities (KDE5).                 [ Default ]`

`-x |--xfce:     install XFCE desktop environment and utilities (XFCE4).`

`-f | --full:    download and install full desktop environment, utilities and themes.`

`-m | --minimal: download and install full desktop environment and utilities.        [ Default ]`

**Be attentive!**

**User input is required to capture necessary setup information and give Termux storage access permissions:**
**this can only be done through user interaction and there are no workarounds for now.**

The rest of the setup is fully automated and should run its course until the proot environment is ready for you to use.

### Process:

- The script goes through usual update and upgrade processes using 'apt' to get the Termux system up to date and ready.
- Necessary dependencies, configurations and binaries are downloaded and set up in both the Termux and proot environment.
- The base Ubuntu image is downloaded, unpacked and setup from within the Termux environment.
- Information is then captured to properly configure and setup a user account and environment features in the proot.
- The setup transitions automatically into the newly unpacked proot environment and proceeds with configuring and installing the rest of your packages, dependencies and additional applications and customizations..
- The setups exits to force reload all changes and greet you with your freshly installed dextop setup once Termux is reopened.

### Note:

All setup dialogs, prompts, commands and binaries have all been made to redirect all output to the Termux's `'/var/log'` directory, keeping output messages to a minimum.

### Customization:

Use and edit the 'proot-applications' script to customize your list of installed applications, libraries, frameworks, utilities and other third party package locations.
You can fill and organize those items under the various arrays and create your own too: do not forget to append the newly made array names under the main installation array!

### Usage:

To access your newly created proot you must type:

- `'proot-session -u <username> | -a <application> | <option>'` to start your session or a specific application on session load.

### The fun begins:

When logging into the proot environment for the first time, you need to start the vnc server manually.
This will let you select the appropriate device resolution settings for you to enjoy the display you have chosen to its full potential.

To set this up, just type `'vnc-start'` and follow the prompt to select the desired resolution geometry.

The next time you log into your proot session on that same device/display, the session greeter will automatically launch the session for you.
The first login records your preferred geometry selection under `"${HOME}"/.vnc/selection`. and uses it to start the VNC server and viewer automatically for your convenience!

Logging out by pressing Ctrl+D or by typing `'logout'` or `'exit'``will automatically stop all vnc servers that are running and exit the proot environment back to the Termux shell.
If you wish to simply stop the display output and continue work using the CLI, simply type `'vnc-stop'`.
To start the display once again, type `'vnc-start'`.

### Reports:

Should you suspect any issues or errors, please provide a copy of the files located under Termux's `'/var/log'` directory when submitting a bug report.
