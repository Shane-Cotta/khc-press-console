# M7 Console

**M7 Console** is a touch-screen console for **Mark 7 automated reloading presses**. It runs on a **Raspberry Pi 4
or Raspberry Pi 5** with a **10.1-inch 1920x1200 HDMI touch screen**, and it drives the press through the press
console's USB cable, in place of the tablet that came with the press. It looks like Mark 7's own console app (the same
tabs, buttons and STOP sign) and carries a large **BETA** mark while it is in testing.

![The M7 Console home screen: PRESS, FIRMWARE, SOFTWARE UPDATE, CONSOLE SETTINGS, ABOUT and TURN OFF, with STOP on the right](docs/images/screen-home.png)

> **Unofficial BETA software for real machinery.** M7 Console is an independent project. It is **not made,
> endorsed or supported by Mark 7 Reloading**. A reloading press has a servo motor, pinch points, primers and powder.
> Read [SAFETY.md](SAFETY.md) and the [Terms of use](TERMS.md) before you use it. **Keep the press console's power
> switch within reach at all times: it is the press's only hard stop.**
>
> **Status of this BETA:** M7 Console has been tested against press simulators, including the real press firmware
> running in a microcontroller simulator. **It has not yet been run on a real press or on the real Raspberry Pi
> hardware.** Treat every session as a test. See [what has not been verified yet](SAFETY.md#not-yet-verified-on-real-hardware).

## What it does

- Runs the press: **RUN**, **END CYCLE**, **SINGLE** and **STOP**, speed, digital clutch, TorqueSense, jog, die
  setup, dwell and index settings, the round counters and supply monitors, and every sensor the press has.
- **STOP is on every screen**, always in the same place, and acts the moment your finger touches it. If the press
  does not confirm a STOP within about a second, the console resets the press controller and tells you to switch off
  the console power.
- **RUN stays locked until the press has calibrated** in this session.
- **Remote Stop, the Machine Guard and TorqueSense are switched ON every time** the console connects, whatever they
  were before.
- Updates the **press firmware** with a check that the image matches your press model, and reads every page back
  after writing it.
- Updates **itself**, up or down, over Wi-Fi or from a USB stick, with an automatic return to the previous version if
  a new one does not start properly. (Consoles from the first BETA update by re-flashing the SD card.)
- Optional: a USB **foot pedal** for SINGLE CYCLE, **alert sounds** through the screen's speaker, a settings backup,
  and a reference of which sensor plugs into which **console port**.

## Supported presses

M7 Console works with the press firmware as Mark 7 shipped it. You do not have to change your press firmware.

| Press | Firmware it reports | Status |
|---|---|---|
| Apex 10 Evolution | Evolution 19 (Mark 7's), or Evolution 20 (optional custom build) | The main target. Not yet run on a press. |
| Revolution | Revolution 30 (Mark 7's), or Revolution 31 (optional custom build) | Same code base as the Evolution. Not yet run on a press. |
| 650 PRO AutoDrive (Dillon 650 / 750) | 650 PRO 43 | **Untested.** Built from Mark 7's manual and firmware. |
| 1050 PRO AutoDrive | 1050 PRO 48 | **Untested.** |
| 1050 X AutoDrive | 1050 X 53 | **Untested.** |
| 650 X, 1050 LTE | 650 X, 1050 LTE | **Untested.** The screens are there; no firmware image is included. |
| Evolution PRO, Revolution / Evolution Dual, GAP PRO | as reported | **Untested.** The screens are there; no firmware image is included. |

A press whose firmware the console does not recognise gets a **STOP-only** screen: STOP works, nothing else does.
The custom firmware builds and how to choose: [Firmware](docs/user-guide/firmware.md).

## What you need

| Item | Notes |
|---|---|
| **Raspberry Pi 4** (2 GB or more) **or Raspberry Pi 5** (2 GB or more) | One SD card image works on both. |
| **Power supply for the Pi** | The official Raspberry Pi supply for your model (Pi 4: 5.1 V 3 A USB-C; Pi 5: 5 V 5 A USB-C) or an equivalent. A weak supply causes random faults. |
| **10.1-inch 1920x1200 HDMI touch screen** with USB touch | The console is designed for this screen class (it was developed against the xbonfire MHEM101TP-C type). Other sizes and resolutions are not supported in this BETA. |
| **A separate 5 V supply for the screen** | Do not power the screen from a USB port of the Pi. |
| **HDMI cable** for the screen | On the Pi 4 a micro-HDMI to HDMI cable; on the Pi 5 the same. |
| **microSD card, 8 GB or larger** | A good-quality card from a known brand (A1 or A2 rated, 16 or 32 GB is a sensible choice). The download is about 260 MB; written, the system uses under 2 GB. |
| **USB data cable: USB-A to micro-USB** | From a USB port of the Pi to the **micro-USB port of the press console** (the port the tablet used). It must be a data cable, not a charge-only cable. |
| A computer with an SD card reader | To write the card once. |
| Optional | A USB stick (FAT or exFAT) for firmware files and offline updates; a USB foot pedal; Wi-Fi or an Ethernet cable for online updates. |

## Download

Get the newest version from the **[Releases page](https://github.com/Shane-Cotta/M7-Console/releases/latest)**:

| File | What it is |
|---|---|
| `m7console-X.Y.Z-rpi.img.xz` | **The SD card image.** This is the one you need. (`X.Y.Z` is the version number.) |
| `m7console-X.Y.Z-rpi.img.xz.sha256` | The image's checksum on its own. |
| `SHA256SUMS.txt` | The checksum of every file in the release. |
| `m7console-X.Y.Z.bundle.tar.xz` | The app update package, for updating a console from a USB stick. You do not need it to set up a new console. |
| `m7fw-*.hex`, `firmware-catalog.json` | The press firmware images. The console already carries all of them; these are for reference. |
| `m7console-index.json` | The update list the consoles read. Not for you to open. |
| `m7console-X.Y.Z-rpi.packages.txt` | Every software package on the card, with its version. |

**Check the download** before you write it. A download that stopped early or was changed must not drive a press.
Put `m7console-X.Y.Z-rpi.img.xz` and `SHA256SUMS.txt` (from the same release) in one folder, open a terminal there,
and run:

- **Windows** (PowerShell): `Get-FileHash .\m7console-X.Y.Z-rpi.img.xz -Algorithm SHA256`, then open
  `SHA256SUMS.txt` in Notepad and compare the long number on the image's line with the one Windows printed. Every
  character must match (upper or lower case does not matter).
- **macOS:** `shasum -a 256 -c --ignore-missing SHA256SUMS.txt`
- **Linux:** `sha256sum -c --ignore-missing SHA256SUMS.txt`

On macOS and Linux the image's line must say `OK`. If it says `FAILED`, or Windows shows a different number, do not
use the file: download it again, and [report it](https://github.com/Shane-Cotta/M7-Console/issues/new/choose) if it
still fails. More detail: [Installing](docs/user-guide/install.md#check-the-download).

## Write the card with Raspberry Pi Imager

Install [Raspberry Pi Imager](https://www.raspberrypi.com/software/) on your computer, put the microSD card in the
reader, then:

1. **Choose Device:** Raspberry Pi 4 or Raspberry Pi 5 (whichever you have).
2. **Choose OS:** scroll to the bottom of the list and pick **Use custom**, then select the downloaded
   `m7console-X.Y.Z-rpi.img.xz`. You do not need to unzip it: Imager reads `.img.xz` directly.
3. **Choose Storage:** pick the microSD card. Check it is the card, not another disk: everything on it is erased.
4. **Next.** If Imager asks **"Would you like to apply OS customisation settings?"**, answer **No**. (Current
   versions of Imager do not offer customisation for a custom image at all, so you may not see this question.) M7
   Console sets itself up; Imager's user, Wi-Fi and SSH settings are not needed and are not supported. If you answered
   Yes by mistake, write the card again and answer No. Why: [Installing](docs/user-guide/install.md#os-customisation-answer-no).
5. Confirm, and let Imager **write and verify** the card. It takes a few minutes. Then take the card out.

**Other tools:** [balenaEtcher](https://etcher.balena.io/) also writes `.img.xz` files directly (Flash from file,
select target, Flash). On Linux from a terminal:
`xz -dc m7console-X.Y.Z-rpi.img.xz | sudo dd of=/dev/<your card> bs=4M conv=fsync status=progress`.
Be very sure of the device name: `dd` overwrites whatever you point it at.

## First start

1. Put the card in the Pi. Connect the screen's HDMI cable to the Pi's **first HDMI port** (HDMI0, the one next to
   the USB-C power input), the screen's touch USB cable to any USB port of the Pi, and the screen's own 5 V supply.
2. Connect the press console's **micro-USB port** to any **USB-A port of the Pi**. Never use the press console's
   USB-A port: that one belongs to the motor.
3. Switch on the screen, then plug in the Pi's power.
4. You see Mark 7's boot animation, then the M7 Console home screen. **The first start takes about a minute longer**
   than later ones: the card grows to fill the whole microSD card and finishes its setup.
5. Tap **PRESS**, read the safety text and tap **ACCEPT**, then **CALIBRATE** with an empty shell plate. RUN unlocks
   after a successful calibration.

The full walk-through: [Getting started](docs/user-guide/getting-started.md).

## Documentation

| Page | What it covers |
|---|---|
| [Safety](SAFETY.md) | **Read first.** STOP, the power switch, interlocks, CRITICAL alerts, firmware, what is not verified yet |
| [User guide](docs/user-guide/README.md) | Everything below, in order |
| [Installing](docs/user-guide/install.md) | Download, checking the download, writing the card, first start |
| [Getting started](docs/user-guide/getting-started.md) | Wiring the Pi, the screen and the press; your first session |
| [The home screen](docs/user-guide/home-screen.md) | The buttons, the status line, ACCEPT before every connection, About, turning off |
| [Calibrating and running](docs/user-guide/calibrate-and-run.md) | CALIBRATE, RUN, END CYCLE, SINGLE, STOP, jog, NEUTRAL, die setup |
| [The press tabs](docs/user-guide/press-tabs.md) | Control, Monitors, Sensors, Setup and Settings, per press model |
| [Sensors and interlocks](docs/user-guide/sensors-and-interlocks.md) | Active and bypassed, Remote Stop, Machine Guard, TorqueSense, Primer Orientation |
| [Alerts](docs/user-guide/alerts.md) | Normal alerts, stop alerts and CRITICAL alerts, and what to do |
| [Firmware](docs/user-guide/firmware.md) | Which image for which press, the custom builds, flashing, DO NOT OPERATE |
| [Software updates and Wi-Fi](docs/user-guide/software-updates.md) | Wi-Fi setup, checking, installing, going back, USB updates, the trial |
| [Console settings](docs/user-guide/console-settings.md) | Touch calibration, rotation, sounds, settings export and import |
| [Foot pedal](docs/user-guide/foot-pedal.md) | A USB foot pedal for SINGLE CYCLE |
| [Console ports](docs/user-guide/console-ports.md) | Which sensor plugs into which port, per press family |
| [Troubleshooting](docs/user-guide/troubleshooting.md) | No press, touch offset, no picture, no sound, Wi-Fi |
| [FAQ](docs/user-guide/faq.md) | Common questions |
| [Terms of use](TERMS.md) | The terms under which you may use M7 Console |

## Getting help

- **Bugs:** open an [issue](https://github.com/Shane-Cotta/M7-Console/issues/new/choose) with the bug report form.
- **If the press ever failed to stop** when you pressed STOP, the Remote Stop or opened the guard: stop using M7
  Console, make the press safe, and report it as a bug, saying so in the first line.
- Mark 7 Reloading does not support M7 Console. Please ask here, not Mark 7.

## Trademarks

Mark 7, the Mark 7 logo, Apex 10, Evolution, Revolution and the other press names belong to Mark 7 Reloading (and
Dillon Precision for the Dillon press names). They are used only to say which presses M7 Console works with. M7 Console
is an independent BETA console offered to Mark 7; it is not a Mark 7 product. See the [Terms of use](TERMS.md).
