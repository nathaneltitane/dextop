### NOTICE

  <details open>
  <summary>2026-10-23</summary>

  - Default container is now Debian 13 (trixie) - was Debian 12 (bookworm)
  - Fedora images: 41, 42, 43 and 44 (dnf5) alongside Debian and Ubuntu
  - Debian and Ubuntu images rebuilt with the current filesystem utility
  - Image selection, codename-free Fedora entries and fixed '-i' image option
  - Container apt sources match each release (archive, ports, non-free-firmware)
  - Container hostname: 'dextop' by default, no longer taken from Android - set with 'container-user -n'
  - 'container-user' only shows the information prompt when there is something to ask
  - Fedora package lists: container packages installed under their Fedora names through dnf
  - Papirus-Dark icon theme now installed with xfce - set by the desktop settings but never installed before
  - Setup runs in C.UTF-8 and initializes the container locale: prompt markers no longer garble
  - Sessions fall back to C.UTF-8 when the chosen locale is missing from the container

  </details>

  <details>
  <summary>2026-10-21</summary>

  - New restore option: '-r' brings back the home directory from a backup
  - Backups now stored in '${PREFIX}/bkp' - sortable names, no backup holds another
  - Purge removes every setup component and offers to restore the home directory from before setup
  - Restoring the earliest backup clears the setup's home links first

  </details>

  <details>
  <summary>2025-03-16</summary>

  - Fix 'container-session' application/focus mode:
    - Show default if application not found or empty
  - Prettify prompt messaging for connect/disconnect

  </details>

  <details>
  <summary>2025-03-15</summary>

  - Fix legacy groups override breaking proot container package installs
  - Now using docker.io stock minimal images for proot deployments
  - WIP: reimplement VNC functionality

  </details>

  <details>
  <summary>2025-01-07</summary>

  - Fix environment options being passed and wrap setup to handle option delegations

  </details>

  <details>
  <summary>2025-01-03</summary>

  - Fix debian images not being found:
    - Image archives now available through get.trmnl.me

  </details>
