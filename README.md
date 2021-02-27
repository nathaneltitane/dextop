# Linux on Android -  Termux // Dextop // Ubuntu
 
![termux dextop](https://github.com/nathaneltitane/dextop/blob/master/termux.png?raw=true)

This project provides any user owning a modern android device, the ability to setup their own Linux-based work environment and use it as their primary workstation.

With Dextop, your device turns into a workstation in the matter of minutes without all the hassle of technical know-how and having to dig through the internet to get staright to work.

Dextop is easy and user friendly.

If you compare Dextop to otherprojects, you will see that:

- It provides you with an installation of Ubuntu 20.04 (LTS): stable, popular and user-friendly knowledge bases.
- It expands the installed base image to run just like a normal PC installation
- It creates a user and a home directory for you to work in.
- It installes all the necessary utilities to provide an experince that is close to the native default Ubuntu install ('sudo', etc.)
- It sets up your internal and external storage media locations under /media for quick access and reference.
- It handles all the technical intricacies so that you do not have to bother with them and get right to work.
- It is configured as a transient chroot: it talks to Android via Termux utilities to access binaries and launch your favorite VNC viewer automatically for you!
- It uses a customized [console](https://github.com/nathaneltitane/console) system to handle the setup, colorize prompts and proved the user with a minimal, user-friendly experience. 

Dextop is very quick and efficient: it  uses DWM as a default window manager/desktop session or can also be set up using the more popular XFCE4 desktop environment.
You get a full set of utilities using XFCE4, but you have been warned, perfomance drops are bound to happen.

### Dextop is great and all, but...

Dextop does not install or configure sound output or advanced mail services!
It is made to run in tandem with Samsung'S Dex: all other features such as music, mail and web browsing should preferably be taken care of using native android applications.

Services backend and other advanced features that require access to restricted core system directories are bound to fail:
If you want to run things just like on any other computer, you must root your device to remove those limitations and gain access to all system directories.

For devices that have not been rooted, you can fake the access to /proc using the -fake flag when launching your user session:
This provides a session with fake, static entries that should bypass most errors, but not all of them.

### To get started, you will need:

- Modern Android device (running android 7.0+: this is a Termux limitation)
- Mouse (bluetooth or other)
- Keyboard (bluetooth or other)
- Power source (for extended work periods and performance requirements: Samsung Dex limitation)
- Monitor (highly recommended for phones and small devices)
- Internet connectivity (for setup, updates and additional package downloads)

### The first thing you want to do is:
- Install [Termux](https://play.google.com/store/apps/details?id=com.termux "Termux by Fredrik Fornwall") via the Google Play store or any other APK provider ([F-Droid](https://f-droid.org/en/packages/com.termux/) being a good example)
- Install a VNC viewer application with full screen or immersive capabillities for a better experience: Dextop supports [realVNC Viewer](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android) and [bVNC](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC "bVNC by Iordan Iordanov")

### Setting things up:

The setup speed greatly depends on your device model and internet connection speed.

Once the Android applications are installed on your device, open Termux and paste or type:

`curl -sL run.dxtp.app > setup && bash setup <option>`

Available install options are:

`-f | --full: download and install full desktop environment and utilities. ( xfce4 )`

`-m | --minimal: download and install minimal desktop environment and utilities. ( dwm ) [ Default ]`


Let the setup run and fetch all the required dependencies: it will prompt you for input once it is ready.
The rest of the setup is fully automated and should run its course until the proot environment is ready for you to use.

**Be attentive!**

**User input is required to capture necessary setup information and give Termux storage access permissions:**
**this can only be done through user interaction and there are no workarounds for now.**

### Process:
- The script goes through usual update and upgrade processes using 'apt' to get the Termux system up to date and ready.
- Necessary dependencies, configurations and binaries are downloaded and set up in both the Termux and proot environment.
- The base Ubuntu image is downloaded, unpacked and setup from within the Termux environment.
- Information is then captured to properly configure and setup a user account and environment features in the proot.
- The setup transitions automatically into the newly unpacked proot environment and proceeds with configuring and installing the rest of your packages, dependencies and additional applications and customizations..

### Note:
All setup dialogs, prompts, commands and binaries have all been made to redirect all output to the Termux's `'/var/log'` directory, keeping output messages to a minimum.

### Customization:

Use and edit the 'proot-applications' script to customize your list of installed applications, libraries, frameworks, utilities and other third party package locations.
You can fill and organize those items under the various arrays and create your own too: do not forget to append the newly made array names under the main installation array!

### Usage:

When the setup completes, it should exit the subshell and return to the default Termux prompt.

Close that Termux session by pressing Ctrl+Dor by typing `exit` (simulates a reboot).

Now you can launch Termux and you will be greeted by the Welcome Prompt:

To access your newly created proot you must type:

- `'proot-launch <username> <option>'`               to start your session or

- `'proot-launch <username> <application> <option>'` to start a specific application on session load.

### Note:

As mentioned above, the proot session does function as intended, but certain  niche cases and workflows may require the use of /proc.
To simulate the /proc directory access using a set of static files loaded during setup to that effect, start your session using the '-f' flag:

- `'proot-launch -f <username> <option>'`

This specific case usage emulates entries generated by hardware I/O under /proc with static files mounted and bound to the proot jail on session login.

### The fun begins!

When logging into the proot environmentfor the first time, you need to start the vnc server manually.
This will let you select the appropriate device resolution settings for you to enjoy the display you have chosen to its full potential.

To set this up, just type `'vnc-start'` and follow the prompt to select the desired resolution geometry.

The next time you log into your proot session on that same device/display setup, the session greeter should just automatically launch things for you:
The first login records your intial geometry selection under `"${HOME}"/.vnc/selection`. and uses it to start the VNC server and subsequently the  viewer automatically for your convenience!

Logging out by pressing Ctrl+D or by typing `'logout'` or `'exit'``will automatically stop all vnc servers that are running and exit the proot environment back to the Termux shell.
If you wish to simply stop the display output and continue work using the CLI, simply type `'vnc-stop'`.
To start the display once again, type `'vnc-start'`.

### Reports:

Should you suspect any issues or errors, please provide a copy of the files located under Termux's `'/var/log'` directory when submitting a bug report.
