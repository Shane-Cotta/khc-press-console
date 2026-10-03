# KHC Press Console

**KHC Press Console** is a touch-screen console for **Mark 7 automated reloading presses**. It runs on a **Raspberry Pi 4
or Raspberry Pi 5** with a **10.1-inch 1920x1200 HDMI touch screen**, and it drives the press through the press
console's USB cable, in place of the tablet that came with the press. It is made by **KHC Precision**, an independent
maker, in KHC's graphite-and-orange look. Its controls are laid out for operators who know automated presses: RUN,
END CYCLE, SINGLE and a red STOP on every screen. It is marked **BETA** while it is in testing.

![The KHC Press Console home screen: PRESS, FIRMWARE, SOFTWARE UPDATE, CONSOLE SETTINGS, ABOUT and TURN OFF, with STOP on the right](docs/images/screen-home.png)

> **Unofficial BETA software for real machinery.** KHC Press Console is an independent project. It is **not made,
> endorsed or supported by Mark 7 Reloading**. A reloading press has a servo motor, pinch points, primers and powder.
> Read [SAFETY.md](SAFETY.md) and the [Terms of use](TERMS.md) before you use it. **Keep the press console's power
> switch within reach at all times: it is the press's only hard stop.**
>
> **Status of this BETA:** KHC Press Console has been tested against press simulators, including the real press firmware
> running in a microcontroller simulator. **It has not yet been run on a real press or on the real Raspberry Pi
> hardware.** Treat every session as a test. See [what has not been verified yet](SAFETY.md#not-yet-verified-on-real-hardware).

## What it does

- Runs the press: **RUN**, **END CYCLE**, **SINGLE** and **STOP**, speed, digital clutch, index torque, jog, die
  setup, dwell and index settings, the round counters and supply monitors, and every sensor the press has.
- **STOP is on every screen**, always in the same place, and acts the moment your finger touches it. If the press
  does not confirm a STOP within about a second, the console resets the press controller and tells you to switch off
  the console power.
- **RUN stays locked until the press has calibrated** in this session.
- **Remote Stop, the Machine Guard and Index torque (TorqueSense™) are switched ON every time** the console connects,
  whatever they
  were before.
- Updates the **press firmware** with a check that the image matches your press model, and reads every page back
  after writing it.
- Updates **itself**, up or down, over Wi-Fi or from a USB stick, with an automatic return to the previous version if
  a new one does not start properly. (Consoles from the first BETA update by re-flashing the SD card.)
- Optional: a USB **foot pedal** for SINGLE CYCLE, **alert sounds** through the screen's speaker, a settings backup,
  and a reference of which sensor plugs into which **console port**.

## Supported presses

KHC Press Console works with the press firmware as Mark 7 shipped it. You do not have to change your press firmware.

| Press | Firmware it reports | Status |
|---|---|---|
| **Evo**: the Mark 7 Apex 10 Evolution | Evo FW 19 (Mark 7's), or Evo FW 20 (the optional KHC patch) | The main target. Not yet run on a press. |
| **Revo**: the Mark 7 Revolution | Revo FW 30 (Mark 7's), or Revo FW 31 (the optional KHC patch) | Same code base as the Evo. Not yet run on a press. |
| **650/750 PRO**: Mark 7's drive for the Dillon 650 / 750 | 650/750 PRO FW 43 | **Untested.** Built from Mark 7's manual and firmware. |
| **1050/1100 PRO**: Mark 7's drive for the Dillon 1050 / 1100 | 1050/1100 PRO FW 48 | **Untested.** |
| **1050/1100 X** | 1050/1100 X FW 53 | **Untested.** |
| 650/750 X, 1050/1100 LTE | as reported | **Untested.** The screens are there. |
| Evo PRO, Revo Dual / Evo Dual, GAP PRO | as reported | **Untested.** The screens are there. |

A press whose firmware the console does not recognise gets a **STOP-only** screen: STOP works, nothing else does.
The console carries the KHC primer-learn patch for the Evo and the Revo (a Primer Orientation fix); there is
none for the 650/750 and 1050/1100 presses yet. How to choose: [Firmware](docs/user-guide/firmware.md).

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

Get the newest version from the **[Releases page](https://github.com/Shane-Cotta/khc-press-console/releases/latest)**:

| File | What it is |
|---|---|
| `khc-press-console-X.Y.Z-rpi.img.xz` | **The SD card image.** This is the one you need. (`X.Y.Z` is the version number.) |
| `khc-press-console-X.Y.Z-rpi.img.xz.sha256` | The image's checksum on its own. |
| `SHA256SUMS.txt` | The checksum of every file in the release. |
| `khc-press-console-X.Y.Z.bundle.tar.xz` | The app update package, for updating a console from a USB stick. You do not need it to set up a new console. |
| `khc-*.json` | The KHC firmware patch definitions, for reference. The console applies them to a backup of your press's own firmware; a release carries no firmware image. |
| `khc-press-console-index.json` | The update list the consoles read. Not for you to open. |
| `khc-press-console-X.Y.Z-rpi.packages.txt` | Every software package on the card, with its version. |

**Check the download** before you write it. A download that stopped early or was changed must not drive a press.
Put `khc-press-console-X.Y.Z-rpi.img.xz` and `SHA256SUMS.txt` (from the same release) in one folder, open a terminal there,
and run:

- **Windows** (PowerShell): `Get-FileHash .\khc-press-console-X.Y.Z-rpi.img.xz -Algorithm SHA256`, then open
  `SHA256SUMS.txt` in Notepad and compare the long number on the image's line with the one Windows printed. Every
  character must match (upper or lower case does not matter).
- **macOS:** `shasum -a 256 -c --ignore-missing SHA256SUMS.txt`
- **Linux:** `sha256sum -c --ignore-missing SHA256SUMS.txt`

On macOS and Linux the image's line must say `OK`. If it says `FAILED`, or Windows shows a different number, do not
use the file: download it again, and [report it](https://github.com/Shane-Cotta/khc-press-console/issues/new/choose) if it
still fails. More detail: [Installing](docs/user-guide/install.md#check-the-download).

## Write the card with Raspberry Pi Imager

Install [Raspberry Pi Imager](https://www.raspberrypi.com/software/) on your computer, put the microSD card in the
reader, then:

1. **Choose Device:** Raspberry Pi 4 or Raspberry Pi 5 (whichever you have).
2. **Choose OS:** scroll to the bottom of the list and pick **Use custom**, then select the downloaded
   `khc-press-console-X.Y.Z-rpi.img.xz`. You do not need to unzip it: Imager reads `.img.xz` directly.
3. **Choose Storage:** pick the microSD card. Check it is the card, not another disk: everything on it is erased.
4. **Next.** If Imager asks **"Would you like to apply OS customisation settings?"**, answer **No**. (Current
   versions of Imager do not offer customisation for a custom image at all, so you may not see this question.) KHC
   Press Console sets itself up; Imager's user, Wi-Fi and SSH settings are not needed and are not supported. If you answered
   Yes by mistake, write the card again and answer No. Why: [Installing](docs/user-guide/install.md#os-customisation-answer-no).
5. Confirm, and let Imager **write and verify** the card. It takes a few minutes. Then take the card out.

**Other tools:** [balenaEtcher](https://etcher.balena.io/) also writes `.img.xz` files directly (Flash from file,
select target, Flash). On Linux from a terminal:
`xz -dc khc-press-console-X.Y.Z-rpi.img.xz | sudo dd of=/dev/<your card> bs=4M conv=fsync status=progress`.
Be very sure of the device name: `dd` overwrites whatever you point it at.

## First start

1. Put the card in the Pi. Connect the screen's HDMI cable to the Pi's **first HDMI port** (HDMI0, the one next to
   the USB-C power input), the screen's touch USB cable to any USB port of the Pi, and the screen's own 5 V supply.
2. Connect the press console's **micro-USB port** to any **USB-A port of the Pi**. Never use the press console's
   USB-A port: that one belongs to the motor.
3. Switch on the screen, then plug in the Pi's power.
4. You see the boot animation, then the KHC Press Console home screen. **The first start takes about a minute longer**
   than later ones: the card grows to fill the whole microSD card and finishes its setup.
   On the first start the console asks for Wi-Fi (or **SKIP**) and then for a **license number** or the **10-day
   trial**: [The trial and your license](docs/user-guide/license.md).
5. The console sees the press and asks **Press detected**: tap **CONNECT** (or tap **PRESS**, read the safety text
   and tap **ACCEPT**). Then **CALIBRATE** with an empty shell plate. RUN unlocks after a successful calibration.

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
| [Sensors and interlocks](docs/user-guide/sensors-and-interlocks.md) | Active and bypassed, Remote Stop, Machine Guard, index torque, Primer Orientation |
| [Alerts](docs/user-guide/alerts.md) | Normal alerts, stop alerts and CRITICAL alerts, and what to do |
| [Firmware](docs/user-guide/firmware.md) | The KHC primer-learn patch and which press it is for, flashing, DO NOT OPERATE |
| [Software updates and Wi-Fi](docs/user-guide/software-updates.md) | Wi-Fi setup, checking, installing, going back, USB updates, the trial |
| [The trial and your license](docs/user-guide/license.md) | The 10-day trial, activating a license, seats, moving a seat to another Pi |
| [Console settings](docs/user-guide/console-settings.md) | Touch calibration, rotation, sounds, settings export and import |
| [Foot pedal](docs/user-guide/foot-pedal.md) | A USB foot pedal for SINGLE CYCLE |
| [Console ports](docs/user-guide/console-ports.md) | Which sensor plugs into which port, per press family |
| [Troubleshooting](docs/user-guide/troubleshooting.md) | No press, touch offset, no picture, no sound, Wi-Fi |
| [FAQ](docs/user-guide/faq.md) | Common questions |
| [Terms of use](TERMS.md) | The terms under which you may use KHC Press Console |

## Getting help

- **Bugs:** open an [issue](https://github.com/Shane-Cotta/khc-press-console/issues/new/choose) with the bug report form.
- **If the press ever failed to stop** when you pressed STOP, the Remote Stop or opened the guard: stop using KHC
  Press Console, make the press safe, and report it as a bug, saying so in the first line.
- Mark 7 Reloading does not support KHC Press Console. Please ask here, not Mark 7.

## Trademarks

Mark 7, Apex 10, Evolution, Revolution, BulletSense, PrimerSense, DecapSense, SwageSense, TorqueSense, PowderCheck and
other Mark 7 names are trademarks of Lyman Products Corporation; Dillon, Super 1050, XL 750 and RL 1100 are trademarks
of Dillon Precision Products. Evo, Revo and Apex refer to those Mark 7 presses, and 650/750 and 1050/1100 to the Dillon
presses Mark 7's drives fit. KHC Precision is not affiliated with, sponsored by, or endorsed by either company; the
names are used only to describe compatibility. No logo, trade dress or product of Mark 7 Reloading, Lyman or Dillon is
part of the software. KHC Press Console is BETA software from KHC Precision, an independent maker. See the
[Terms of use](TERMS.md).
