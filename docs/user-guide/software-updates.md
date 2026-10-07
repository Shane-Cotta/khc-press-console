# Software updates and Wi-Fi

KHC Press Console updates itself from the
[KHC Press Console releases](https://github.com/Shane-Cotta/khc-press-console/releases), over Wi-Fi or Ethernet, or
from a USB stick. You can install a newer version (an upgrade) or go back to an older one (a downgrade). Software
updates never change your press's firmware.

> [!NOTE]
> **Consoles older than 0.3.0b2** cannot find updates at this address. Update them by writing a new card
> ([Installing](install.md)). Writing a new card erases the settings and firmware backups kept on the old one.

## Before you update

- **Nothing is installed unless you tap INSTALL** (or SWITCH TO) and confirm. The console looks for new versions by
  itself ([Update available](#update-available)), but it never installs one by itself.
- **Updates are never offered while the press is busy:** while it runs, moves, calibrates or is in die setup, while a
  STOP is being confirmed, while a CRITICAL alert is open or a firmware update runs, and for 5 seconds after.
- **Every install disconnects the press first.** The console sends STOP if anything moves, resets the press
  controller, and keeps the press disconnected while the update downloads and installs. **STOP still works** the whole
  time. Then the console software restarts into the new version.
- **After an update,** tap PRESS, ACCEPT and CALIBRATE again, with an empty shell plate.
- **Updates are checked, not yet signed.** Every package is checked against the SHA-256 checksums published with its
  release, and is downloaded only over HTTPS from the KHC Press Console releases. Install only from the official
  releases, or from a USB stick you prepared yourself from them ([Safety](../../SAFETY.md#software-updates)).

## Setting up Wi-Fi

The press never needs Wi-Fi. Wi-Fi is for updates and license activation only. Wi-Fi stays **off** until you choose
the country the console is in (the radio channels and power allowed differ by country).

1. Open **SOFTWARE UPDATE** and tap **WI-FI** (also in **CONSOLE SETTINGS** and on **LICENSE**).
2. Choose your country from the list, or tap **OTHER CODE…** and type its two-letter code (for example US).

   ![The Wi-Fi screen asking for the country first, with the country list and OTHER CODE](../images/screen-wifi-country.png)

3. Tap **SCAN**, then tap your network.
4. Type its password on the on-screen keyboard. It shows dots; **SHOW** shows the text. Tap **CONNECT**.

   ![The Wi-Fi password entry with the on-screen keyboard, SHOW and CONNECT](../images/screen-wifi-password.png)

5. The status line shows the network and the console's address once it is connected.

- **A network that does not broadcast its name:** tap **HIDDEN NETWORK…**, type its name, choose its security (WPA2,
  WPA3 or open), then its password.
- **Supported:** open networks, WPA2 and WPA3 personal (a password). **Not supported:** WPA Enterprise (a user name and
  password) and WEP.
- **FORGET** removes a saved network and its password.
- The password is stored only in the console's network configuration, readable only by the system. It never goes into
  a log.

**Ethernet** works too: plug a cable from your router into the Pi's Ethernet port. The console gets its address from
the router by itself.

## Update available

The console looks for new versions by itself: a few minutes after it starts, then about once a day, and soon after the
network comes back. It does this **only while no press is connected**, and it only reads the release list: it never
downloads or installs anything by itself. A failed check (no internet, for example) shows nothing; it tries again
later.

When a newer version can be installed, the top bar of the home screen and of **SOFTWARE UPDATE** shows a badge:

- **UPDATE AVAILABLE**: a newer version is out.
- **SAFETY UPDATE** (amber): it fixes a safety problem, or this version is older than the safety minimum. Install it
  soon, with the press stopped.

Nothing pops up, nothing sounds, and nothing appears on the press screen. On the home screen, tap the badge to open
**SOFTWARE UPDATE** with that version highlighted. On SOFTWARE UPDATE, tap it for a short explanation.

## Checking and installing

![SOFTWARE UPDATE with example data: the running version, the Versions list marked Safety fix, Newer, Running and Older, and CHECK FOR UPDATES, USB STICK and WI-FI](../images/screen-software-check.png)

1. Stop the press.
2. Open **SOFTWARE UPDATE** and tap **CHECK FOR UPDATES**. The console reads the release list. (It may wait up to
   about 45 seconds for its clock to be set from the network: the Pi has no clock battery.)
3. The **Versions** list shows each version with its date and size, marked **Newer**, **Older**, **Running**,
   **Safety fix** or **Pre-release**, and **INSTALL** or **SWITCH TO** where it can be installed.
4. Tap a version to read its notes.
5. Tap **INSTALL**. Read the question: "The console software restarts to switch versions. The press does not move
   during the update. Keep your hands clear of the press." Confirm with **INSTALL**.
6. The download shows its progress. **CANCEL** stops it.
7. The console checks the package, installs it and restarts into the new version.

![The download progress bar with CANCEL, and the note that the press is disconnected and STOP still works](../images/screen-software-progress.png)

If an update finishes without restarting the console (for example a switch to the version already running), after
20 seconds the screen offers **USE THE PRESS AGAIN**. The press stays disconnected until you tap it.

## Going back to an older version

- **Older** versions down to the safety minimum can be installed like newer ones. The question says that it is a
  downgrade.
- **SWITCH TO** goes back to a version that is still on the console, without downloading it. The console keeps the
  running version, the last version that was confirmed working, and one more.

![The install question for an older version, warning that this is a downgrade](../images/screen-software-confirm-downgrade.png)

## The trial: automatic return to the previous version

A newly installed version is **on trial**: "Trying X.Y.Z. It is kept once the console has run for 15 seconds."

- It is kept once it has run for 15 seconds with its screen working.
- If it does not start, freezes for 3 minutes, or the console restarts twice before the version was confirmed, the
  console **goes back to the previous version by itself**. SOFTWARE UPDATE says so.
- A version the console went back from is not offered again by the update badge.

If this happens, please [report it](https://github.com/Shane-Cotta/khc-press-console/issues/new/choose).

## The safety minimum

The release list carries a **safety minimum** ("Safety minimum: X.Y.Z" on the screen).

- Versions below it are listed but cannot be installed: a later version fixed a safety problem in them.
- The minimum only ever goes up. Versions withdrawn by a release are never offered.
- A **Safety fix** mark on a version means it fixes a safety problem. Install it soon.

## Pre-release versions for testers

A pre-release is a test version, published before it becomes the public release.

- **Only testers get it.** KHC Precision can assign a pre-release to a license, or to a single console. That console
  then offers it as an update, marked **Pre-release**, and **SOFTWARE UPDATE** shows "Pre-release channel:" with its
  version. Everyone else sees only the public latest release.
- **Nothing installs by itself.** You install a pre-release exactly like any other version, after the same question.
- **It needs a licensed console on a card written with 0.4.0b1 or later.** A console in its trial, or on an older
  card, sees only the public releases.
- When the pre-release is no longer assigned, the console shows the public releases again. An installed pre-release
  keeps running until you install another version.

> [!WARNING]
> A pre-release is less tested than a public release. Use an empty shell plate first, and keep the power switch within
> reach.

## From a USB stick (no network)

1. On a computer, download `khc-press-console-X.Y.Z.bundle.tar.xz` from the release you want. Check it against that
   release's `SHA256SUMS.txt` ([Check the download](install.md#check-the-download)).
2. Copy it, unchanged, to the **top folder** of a FAT or exFAT USB stick, or into a folder named `khc-press-console`
   on it.
3. Plug the stick into the Pi, open **SOFTWARE UPDATE** and tap **USB STICK**. The stick's packages appear with their
   version.
4. Tap one, and confirm as for an online install.

The console mounts USB sticks **read-only**: it never writes to your stick.

**A package this console has never seen in an online release list** (the console has never been online, or the stick
came from somewhere else) shows a warning with the start of its SHA-256. It then needs **INSTALL ANYWAY**. Compare the
SHA-256 with the release's `SHA256SUMS.txt` before you tap it.

![The USB install question for a package never listed online: the SHA-256 warning and INSTALL ANYWAY](../images/screen-software-usb.png)

## Updates and the press firmware

- **Software updates carry no press firmware,** and no release carries a firmware image. Updating the console, or
  going back to an older version, never changes the firmware on your press. Only the [FIRMWARE](firmware.md) screen
  does that.
- The KHC primer-learn patch is made on the console, from a backup of your press's own firmware
  ([Firmware](firmware.md)).
- Your firmware backups are kept with the console's settings and survive software updates.
- A console whose card was written with 0.3.0b3 or earlier may still hold firmware images from that card. They are
  kept, and SOFTWARE UPDATE shows how many.
