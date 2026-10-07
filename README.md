# KHC Press Console

**KHC Press Console** is a touch-screen console for **Mark 7 automated reloading presses**. It runs on a **Raspberry
Pi 4 or Raspberry Pi 5** with a **10.1-inch 1920x1200 HDMI touch screen**, and drives the press through the press
console's USB cable, in place of the tablet that came with the press. It is made by **KHC Precision**, an independent
maker, and it is marked **BETA** while it is in testing.

Online manual: https://shane-cotta.github.io/khc-press-console/

![The KHC Press Console home screen with the press not connected: PRESS, FIRMWARE, SOFTWARE UPDATE, CONSOLE SETTINGS, ABOUT, TURN OFF, and the red STOP sign on the right](docs/images/screen-home.png)

> [!WARNING]
> **Unofficial BETA software for real machinery.** KHC Press Console is **not made, endorsed or supported by Mark 7
> Reloading**. A reloading press has a servo motor, pinch points, primers and powder. Read [Safety](SAFETY.md) and
> the [Terms of use](TERMS.md) before you use it.
>
> **Keep the press console's power switch within reach at all times. It is the press's only hard stop.**

> [!IMPORTANT]
> **Status of this BETA.** KHC Press Console has been tested against press simulators, including the real press
> firmware running in a microcontroller simulator, and has been used on a real **Apex 10 Evolution** and a real
> **Revolution** (connect, calibrate, run, firmware backup and flash). **Nothing is validated yet:** the KHC
> primer-learn patch is still under test, and the 650/750 and 1050/1100 have not been run with the console at all.
> Treat every session as a test. See [what has not been verified yet](SAFETY.md#not-yet-verified-on-real-hardware).

Mark 7, Apex 10, Evolution and Revolution are trademarks of Lyman Products Corporation, and Dillon is a trademark of
Dillon Precision Products. KHC Precision is not affiliated with either company. See [Trademarks](#trademarks).

## What it does

- **Runs the press:** RUN, END CYCLE, SINGLE and STOP; speed, digital clutch, index torque, jog, die setup, dwell and
  index settings; the round counters, the supply monitors and every sensor the press has.
- **STOP is on every screen,** always in the same place, and acts the moment your finger touches it. If the press does
  not confirm a STOP within about a second, the console resets the press controller and tells you to switch off the
  console power.
- **RUN stays locked until the press has calibrated** in this connection.
- **Remote Stop, the Machine Guard and Index torque (TorqueSense™) are switched on** every time the console connects,
  whatever they were before.
- **Looks after the press firmware:** it backs up your press's own firmware before every flash, can make the KHC
  primer-learn patch for the Evo and the Revo from that backup, and puts the backup back when you ask. Every image is
  checked against your press model, and every page is read back after it is written.
- **Updates itself,** up or down, over Wi-Fi, Ethernet or a USB stick. It tells you when an update is available but
  never installs one by itself, and it goes back to the previous version by itself if a new one does not start
  properly.
- **Optional extras:** a USB **foot pedal** for SINGLE CYCLE, **alert sounds** through the screen's speaker, a
  settings file, and a reference of which sensor plugs into which **console port**.

## Supported presses

The console works with the press firmware as Mark 7 shipped it. You do not have to change your press firmware.

| Press | Firmware it reports | Status |
|---|---|---|
| **Evo**: the Mark 7 Apex 10 Evolution | Evo FW 19 (Mark 7's), or Evo FW 20 (the optional KHC patch) | The main target. Used on a real press; the KHC patch is still under test. |
| **Revo**: the Mark 7 Revolution | Revo FW 30 (Mark 7's), or Revo FW 31 (the optional KHC patch) | Same code base as the Evo. Used on a real press; the KHC patch is still under test. |
| **650/750 PRO**: Mark 7's drive for the Dillon 650 / 750 | 650/750 PRO FW 43 | **Untested.** Built from Mark 7's manual and firmware. |
| **1050/1100 PRO**: Mark 7's drive for the Dillon 1050 / 1100 | 1050/1100 PRO FW 48 | **Untested.** |
| **1050/1100 X** | 1050/1100 X FW 53 | **Untested.** |
| 650/750 X, 1050/1100 LTE | as reported | **Untested.** The screens are there. |
| Evo PRO, Revo Dual / Evo Dual, GAP PRO | as reported | **Untested.** The screens are there. |

A press whose firmware the console does not recognise gets a **STOP-only** screen: STOP works, nothing else does.
The KHC primer-learn patch (a Primer Orientation fix) exists for the Evo and the Revo only. See
[Firmware](docs/user-guide/firmware.md).

## What you need

| Item | Notes |
|---|---|
| **Raspberry Pi 4 or Raspberry Pi 5**, 2 GB of memory or more | One SD card image works on both. |
| **Power supply for the Pi** | The official Raspberry Pi USB-C supply for your model (Pi 4: 5.1 V 3 A; Pi 5: 5 V 5 A) or an equivalent. A weak supply causes random faults. |
| **10.1-inch 1920x1200 HDMI touch screen** with USB touch | The console is designed for this screen class (it was developed against the xbonfire MHEM101TP-C type). Other sizes and resolutions are not supported in this BETA. |
| **A separate 5 V supply for the screen** | Do not power the screen from a USB port of the Pi. |
| **Micro-HDMI to HDMI cable** | Both the Pi 4 and the Pi 5 have micro-HDMI ports. |
| **microSD card, 8 GB or larger** | A good-quality card from a known brand (A1 or A2 rated; 16 or 32 GB is a sensible size). |
| **USB-A to micro-USB data cable** | From a USB port of the Pi to the **micro-USB port of the press console** (the port the tablet used). It must be a data cable, not a charge-only cable. |
| A computer with an SD card reader | To write the card once. |
| Optional | A USB stick (FAT or exFAT) for offline updates; a USB foot pedal; Wi-Fi or an Ethernet cable for online updates and license activation. |

## Download

Get the newest version from the **[Releases page](https://github.com/Shane-Cotta/khc-press-console/releases/latest)**.
`X.Y.Z` stands for the version number.

| File | What it is |
|---|---|
| `khc-press-console-X.Y.Z-rpi.img.xz` | **The SD card image.** This is the one you need. |
| `SHA256SUMS.txt` | The checksum of every file in the release. Use it to check your download. |
| `khc-press-console-X.Y.Z-rpi.img.xz.sha256` | The image's checksum on its own. |
| `khc-press-console-X.Y.Z.bundle.tar.xz` | The app update package, for updating a console from a USB stick. Not needed for a new console. |
| `khc-*.json` | The KHC firmware patch definitions. A release carries no firmware image. |
| `khc-press-console-index.json` | The update list the consoles read. Not for you to open. |
| `khc-press-console-X.Y.Z-rpi.packages.txt` | Every software package on the card, with its version. |

## Check the download

A download that stopped early or was changed must not drive a press. Put the image and `SHA256SUMS.txt` from the same
release in one folder, open a terminal there, and run:

- **macOS:** `shasum -a 256 -c --ignore-missing SHA256SUMS.txt`
- **Linux:** `sha256sum -c --ignore-missing SHA256SUMS.txt`
- **Windows (PowerShell):** `Get-FileHash .\khc-press-console-X.Y.Z-rpi.img.xz -Algorithm SHA256`, then compare the
  number with the image's line in `SHA256SUMS.txt`.

On macOS and Linux the image's line must say `OK`. On Windows every character must match. If it does not match, do
not use the file. Step by step: [Check the download](docs/user-guide/install.md#check-the-download).

## Write the card

1. Install [Raspberry Pi Imager](https://www.raspberrypi.com/software/) and put the microSD card in the reader.
2. **Choose Device:** your Raspberry Pi 4 or 5.
3. **Choose OS:** **Use custom** (at the bottom of the list), then the `.img.xz` file. There is no need to unzip it.
4. **Choose Storage:** the microSD card. Everything on it is erased.
5. If Imager asks about **OS customisation settings**, answer **No**
   ([why](docs/user-guide/install.md#os-customisation-answer-no)).
6. Let Imager write and verify the card, then take it out.

Other tools and the details: [Installing](docs/user-guide/install.md).

## First start

1. Wire the Pi, the screen and the press console as in [Getting started](docs/user-guide/getting-started.md#wiring).
2. Switch on the screen, then plug in the Pi's power. The first start takes about a minute longer than later ones.
3. Read the [terms of use](TERMS.md) on the console and tap **I AGREE** on the last page.
4. Set up Wi-Fi or tap **SKIP**, then choose a license or the 10-day trial
   ([The trial and your license](docs/user-guide/license.md)).
5. Plug in the press and tap **CONNECT**, then **CALIBRATE** with an empty shell plate. RUN unlocks after a successful
   calibration.

The full walk-through: [Getting started](docs/user-guide/getting-started.md).

## Documentation

| Page | What it covers |
|---|---|
| [Safety](SAFETY.md) | **Read first.** STOP, the power switch, interlocks, CRITICAL alerts, firmware, what is not verified yet |
| [User guide](docs/user-guide/README.md) | Everything below, in order |
| [Installing](docs/user-guide/install.md) | Download, checking the download, writing the card, first start |
| [Getting started](docs/user-guide/getting-started.md) | Wiring the Pi, the screen and the press; your first session |
| [The home screen](docs/user-guide/home-screen.md) | The buttons, the status line, the badges, ACCEPT before every connection, About, turning off |
| [Calibrating and running](docs/user-guide/calibrate-and-run.md) | CALIBRATE, RUN, END CYCLE, SINGLE, STOP, jog, NEUTRAL, die setup |
| [The press tabs](docs/user-guide/press-tabs.md) | Control, Monitors, Sensors, Setup and Settings, per press model |
| [Sensors and interlocks](docs/user-guide/sensors-and-interlocks.md) | Active and bypassed, Remote Stop, Machine Guard, index torque, Primer Orientation |
| [Alerts](docs/user-guide/alerts.md) | Normal alerts, stop alerts and CRITICAL alerts, and what to do |
| [Firmware](docs/user-guide/firmware.md) | The firmware backup, the KHC primer-learn patch, restoring, DO NOT OPERATE |
| [Software updates and Wi-Fi](docs/user-guide/software-updates.md) | Wi-Fi, the update badge, installing, going back, USB sticks, pre-releases |
| [The trial and your license](docs/user-guide/license.md) | The 10-day trial, activating on the console or with your phone, seats |
| [Console settings](docs/user-guide/console-settings.md) | Touch calibration, rotation, sounds, settings export and import |
| [Foot pedal](docs/user-guide/foot-pedal.md) | A USB foot pedal for SINGLE CYCLE |
| [Console ports](docs/user-guide/console-ports.md) | Which sensor plugs into which port, per press family |
| [Troubleshooting](docs/user-guide/troubleshooting.md) | No press, touch offset, no picture, no sound, Wi-Fi |
| [FAQ](docs/user-guide/faq.md) | Common questions |
| [Terms of use](TERMS.md) | The terms under which you may use KHC Press Console |

## Getting help

- **Bugs:** open an [issue](https://github.com/Shane-Cotta/khc-press-console/issues/new/choose) with the bug report
  form. Quote the version shown on **ABOUT**.
- **If the press ever failed to stop** when you tapped STOP, pressed the Remote Stop or opened the guard: stop using
  KHC Press Console, make the press safe, and report it as a bug. Say so in the first line.
- **Licenses:** [khcprecision.com](https://khcprecision.com).
- Mark 7 Reloading does not support KHC Press Console. Please ask here, not Mark 7.

## Trademarks

Mark 7, Apex 10, Evolution, Revolution, BulletSense, PrimerSense, DecapSense, SwageSense, TorqueSense, PowderCheck and
other Mark 7 names are trademarks of Lyman Products Corporation; Dillon, Super 1050, XL 750 and RL 1100 are trademarks
of Dillon Precision Products. Evo, Revo and Apex refer to those Mark 7 presses, and 650/750 and 1050/1100 to the Dillon
presses Mark 7's drives fit. KHC Precision is not affiliated with, sponsored by, or endorsed by either company; the
names are used only to describe compatibility. No logo, trade dress or product of Mark 7 Reloading, Lyman or Dillon is
part of the software. KHC Press Console is BETA software from KHC Precision, an independent maker. See the
[Terms of use](TERMS.md).
