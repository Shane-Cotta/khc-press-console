# Installing M7 Console

M7 Console comes as one ready-to-write **SD card image** for the Raspberry Pi 4 and the Raspberry Pi 5. You write it
to a microSD card once; the Pi then starts straight into M7 Console, full screen. There is nothing to install on top,
no login and no keyboard needed.

## What you need

- A **Raspberry Pi 4** (2 GB of memory or more) or a **Raspberry Pi 5** (2 GB or more).
- The **power supply** for your Pi: the official Raspberry Pi USB-C supply (Pi 4: 5.1 V 3 A; Pi 5: 5 V 5 A) or an
  equivalent. A weak supply causes random restarts and faults.
- A **10.1-inch 1920x1200 HDMI touch screen** whose touch panel connects over USB, with **its own 5 V supply**, and a
  micro-HDMI to HDMI cable.
- A **microSD card of 8 GB or more**. A good-quality card from a known brand (A1 or A2 rated) lasts longer; 16 or
  32 GB is a sensible size. The download is about 260 MB; on the card the system takes under 2 GB, and the rest is
  free space for updates.
- A **USB-A to micro-USB data cable** for the press console (see [Getting started](getting-started.md)).
- A computer with an SD card reader, to write the card.

## Download

Open the **[Releases page](https://github.com/Shane-Cotta/M7-Console/releases/latest)** and download, from the
newest release:

- `m7console-X.Y.Z-rpi.img.xz`: the SD card image (`X.Y.Z` is the version, for example `0.1.0`);
- `SHA256SUMS.txt`: the checksums of every file of that release.

## Check the download

Checking tells you the image arrived complete and unchanged. Put both files in the same folder and open a terminal
(Windows: PowerShell; macOS: Terminal; Linux: any terminal) in that folder.

**Windows (PowerShell):**

```powershell
Get-FileHash .\m7console-X.Y.Z-rpi.img.xz -Algorithm SHA256
```

Windows does not compare for you. Open `SHA256SUMS.txt` in Notepad and compare the long hexadecimal number on the
image's line with the one PowerShell printed. Every character must be the same; upper or lower case does not matter.
(In Command Prompt instead: `certutil -hashfile m7console-X.Y.Z-rpi.img.xz SHA256`.)

**macOS:**

```sh
shasum -a 256 -c --ignore-missing SHA256SUMS.txt
```

**Linux (including Raspberry Pi OS):**

```sh
sha256sum -c --ignore-missing SHA256SUMS.txt
```

On macOS and Linux the image's line must end in `OK`. `FAILED` means it does not match. If nothing is printed, the
image is not in that folder or has another name.

Each release also has `m7console-X.Y.Z-rpi.img.xz.sha256`, the image's checksum alone, in the same format: you can
check against it instead of `SHA256SUMS.txt`.

**If it does not match:** do not use the file. Download the image and `SHA256SUMS.txt` again, from the same release,
and check again (a download that stopped early is the usual cause). Make sure you downloaded from the official
[releases page](https://github.com/Shane-Cotta/M7-Console/releases). If it still fails, report it as an
[issue](https://github.com/Shane-Cotta/M7-Console/issues/new/choose) with the file name and the output of the check.

Check the file **as downloaded**, still ending in `.img.xz`.

## Write the card with Raspberry Pi Imager

Install [Raspberry Pi Imager](https://www.raspberrypi.com/software/) (Windows, macOS or Linux) and put the microSD
card in your computer's card reader.

1. **Choose Device:** pick **Raspberry Pi 4** or **Raspberry Pi 5**, whichever you have.
2. **Choose OS:** scroll to the very bottom of the list and pick **Use custom**. Select the downloaded
   `m7console-X.Y.Z-rpi.img.xz`. There is no need to unzip it first.
3. **Choose Storage:** pick the microSD card. Look at the size to be sure it is the card: everything on it is
   erased.
4. **Next.** If Imager asks whether to apply **OS customisation settings**, answer **No** (see below). Current
   versions of Imager do not offer customisation for a custom image, so you may not be asked.
5. Confirm that the card will be erased. Imager writes the card and then **verifies** it (reads it back). This takes
   a few minutes. When it says the card can be removed, take it out.

### OS customisation: answer No

M7 Console's card configures itself: its name on the network, its firewall, the kiosk that runs the console, and
Wi-Fi (which you set up later on the console's own screen, if you want online updates). It needs no user account,
no SSH (the card has no SSH server) and no Wi-Fi settings from Imager, and Imager's customisation is **not supported** for it:

- **Current Imager versions (2.x)** do not know how a custom image wants to be customised, so they skip the
  customisation step for it. Nothing to do.
- **Older Imager versions (1.8, 1.9)** ask "Would you like to apply OS customisation settings?". If you answer Yes,
  they add a first-start script made for older Raspberry Pi OS releases. M7 Console's card is built on a newer
  release, so those settings would not be applied reliably and the first start could behave unexpectedly (for
  example an extra restart, a changed network name, or Wi-Fi switched on without a country set on the console).
  **Answer No.**

If you answered Yes by mistake, simply write the card again and answer No.

## Other ways to write the card

- **balenaEtcher** ([etcher.balena.io](https://etcher.balena.io/)) also reads `.img.xz` directly: **Flash from file**,
  pick the image, **Select target** (the card), **Flash**. It verifies the card afterwards.
- **From a terminal** on Linux (on macOS, use Imager or balenaEtcher):

  ```sh
  xz -dc m7console-X.Y.Z-rpi.img.xz | sudo dd of=/dev/<your card> bs=4M conv=fsync status=progress
  ```

  Find the card's device name first with `lsblk` (the whole card, for example `/dev/sdb` or `/dev/mmcblk0`, not a
  partition), and unmount its partitions. **`dd` overwrites whatever device you give it without asking**: a wrong name
  can erase your computer's disk.

## First start

1. Wire the Pi, the screen and the press console as in [Getting started](getting-started.md).
2. Switch the screen on, then plug in the Pi's power. The Pi has no power switch: it starts when power is applied.
3. The screen shows Mark 7's boot animation while the system starts, then the M7 Console **home screen**.
4. **The very first start takes about a minute longer** than later ones: the card grows to use the whole microSD
   card and finishes its one-time setup. Do not unplug the Pi during it.
5. On the home screen, the status line reads **Press not connected** until you tap **PRESS** and **ACCEPT**. Nothing
   is sent to the press before that.

If the screen stays black, see [Troubleshooting](troubleshooting.md#no-picture-on-the-screen).

## Updating later

Newer consoles update themselves from the SOFTWARE UPDATE screen, over Wi-Fi or Ethernet, or from a USB stick: see
[Software updates](software-updates.md). Writing a new card with a newer image also works at any time, but it
starts from scratch: the console's saved settings, saved Wi-Fi networks and settings exports on the card are lost.
