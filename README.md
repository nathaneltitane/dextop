<p align="center"><img src="https://raw.githubusercontent.com/nathaneltitane/dextop/main/resources/logo/logo-dextop.svg" alt="dextop"><br><b>Linux based workstation for Android</b><br>YOUR DESKTOP, IN YOUR POCKET.</p>

---

[![Donate](https://img.shields.io/badge/Paypal-2f343f.svg?style=for-the-badge&logo=paypal&label=Donate)](https://www.paypal.com/donate?hosted_button_id=ZW3CDCANHJCWJ)<br>
Show your appreciation with a PayPal donation!

---

[![Star](https://img.shields.io/github/stars/nathaneltitane/dextop.svg?style=for-the-badge&logo=github&label=Star&color=2f343f)](https://github.com/nathaneltitane/dextop)<br>
Useful? Star the repository - it helps others find it.

---

### Welcome to [Dextop](https://dextop.app)

Dextop turns most modern Android devices into a complete Linux based workstation in a matter of minutes!
No hassle or deep technical know-how required: **Dextop is easy and user friendly.**

Every command, option, distribution and package is documented on [dextop.app](https://dextop.app) - release notes are listed in [NOTICE.md](NOTICE.md).

---

### TL;DR

**Prepare ↴**

Install the [Termux](https://github.com/termux/termux-app/releases) and [Termux:X11](https://github.com/termux/termux-x11/releases) APKs - [Termux:API](https://github.com/termux/termux-api/releases) is optional but recommended - never the deprecated Google Play Store packages.

**Link storage ↴**

'cd' into the directory to use as home storage:

```
echo 'Home' > .storage
```

**Install ↴**

Launch Dextop setup:

```
curl -s -L run.dxtp.app > dextop && bash dextop
```

**Use ↴**

Log into the container:

```
container-session -d
```

Start the graphical interface:

```
container-session -o
```

---

### Credits:

Dextop runs on [Termux](https://github.com/termux/termux-app) and [Termux:X11](https://github.com/termux/termux-x11), with its scripts written for [GNU Bash](https://www.gnu.org/software/bash/).

Dextop is related to [Frobulator](https://github.com/nathaneltitane/frobulator), the shell scripting function library behind every Dextop script, and [Terminal](https://github.com/nathaneltitane/terminal), which hosts the container images Dextop downloads.

---

### License:

Dextop is free software released under the GNU General Public License version 3 - see 'LICENSE.md'.

Linux is a registered trademark of Linus Torvalds. Android is a trademark of Google LLC. Neither sponsors, authorizes or endorses this project.

---

### Reports:

[Submit bug report or feature request](https://github.com/nathaneltitane/dextop/issues)

Note:

All setup dialogs, prompts, commands and binary execution outputs have been set to redirect to the `${PREFIX}/var/log` directory to keep output messages to a minimum.
Should you suspect any issues or errors, please provide a copy of those files when submitting a bug report.

---

### Projects:

[![GitHub Repo stars](https://img.shields.io/github/stars/nathaneltitane/dextop?style=for-the-badge&logo=gnubash&logoColor=ffffff&label=DEXTOP)](https://github.com/nathaneltitane/dextop)

[![GitHub Repo stars](https://img.shields.io/github/stars/nathaneltitane/frobulator?style=for-the-badge&logo=gnubash&logoColor=ffffff&label=FROBULATOR)](https://github.com/nathaneltitane/frobulator)

[![GitHub Repo stars](https://img.shields.io/github/stars/nathaneltitane/l2cu?style=for-the-badge&logo=gnubash&logoColor=ffffff&label=L²CU)](https://github.com/nathaneltitane/l2cu)

[![GitHub Repo stars](https://img.shields.io/github/stars/nathaneltitane/terminal?style=for-the-badge&logo=gnubash&logoColor=ffffff&label=TERMINAL)](https://github.com/nathaneltitane/terminal)

[![GitHub Repo stars](https://img.shields.io/github/stars/nathaneltitane/mechablocks?style=for-the-badge&logo=gnubash&logoColor=ffffff&label=MECHA%20//%20BLOCKS)](https://github.com/nathaneltitane/mechablocks)

[![GitHub Repo stars](https://img.shields.io/github/stars/nathaneltitane/studworx?style=for-the-badge&logo=gnubash&logoColor=ffffff&label=STUDWORX)](https://github.com/nathaneltitane/studworx)

[![GitHub Repo stars](https://img.shields.io/github/stars/nathaneltitane/nathaneltitane?style=for-the-badge&logo=gnubash&logoColor=ffffff&label=NATHANEL%20%2b%20TITANE)](https://github.com/nathaneltitane/nathaneltitane)

[![GitHub Repo stars](https://img.shields.io/github/stars/nathaneltitane/pewpewprints?style=for-the-badge&logo=gnubash&logoColor=ffffff&label=PEW%21%20PEW%21%20PRINTS)](https://github.com/nathaneltitane/pewpewprints)

---

[![Donate](https://img.shields.io/badge/Paypal-2f343f.svg?style=for-the-badge&logo=paypal&label=Donate)](https://www.paypal.com/donate?hosted_button_id=ZW3CDCANHJCWJ)<br>
Show your appreciation with a PayPal donation!

---

[![Star](https://img.shields.io/github/stars/nathaneltitane/dextop.svg?style=for-the-badge&logo=github&label=Star&color=2f343f)](https://github.com/nathaneltitane/dextop)<br>
Useful? Star the repository - it helps others find it.
