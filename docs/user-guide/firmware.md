# Press firmware

The press controller inside the press console runs Mark 7's firmware. **You do not need to change it to use KHC
Press Console**: the console works with the firmware your press shipped with. The **FIRMWARE** screen is for putting a
firmware image on the press controller when you want to: the KHC primer-learn patch, or a file of your own from a
USB stick.

## The firmware on the console

The console carries the **KHC primer-learn patch** for the Evo and the Revo; nothing needs downloading. For a press on
Mark 7's original firmware, the console makes the KHC build itself, from **a backup of your own press's firmware**
("Backup, restore and the KHC patch" below). The release page carries no firmware image, only the patch descriptions
(`khc-*.json`).

| Firmware | For | Reports | What it is |
|---|---|---|---|
| KHC primer-learn patch for Evo (from Mark 7 FW 19) | the Mark 7 Apex 10 Evolution (Evo) **only** | Evo FW 20 | Primer Orientation fix. **Not yet run on a press** |
| KHC primer-learn patch for Revo (from Mark 7 FW 30) | the Mark 7 Revolution (Revo) **only** | Revo FW 31 | Primer Orientation fix. **Not yet run on a press** |

The list on the FIRMWARE screen shows them by their short names, **KHC patch for Evo** and **KHC patch for Revo**.

The console does not carry Mark 7's own firmware images. **There is no KHC firmware for the 650/750 PRO and X, the
1050/1100 PRO, X and LTE, the Evo PRO, the Duals or the GAP PRO yet**: on those presses the FIRMWARE screen says so,
and you can still flash a file of your own from a USB stick (below). None of these images has been flashed with KHC
Press Console on a real press yet.

## Which one to choose

- **Evo or Revo with Mark 7's Primer Orientation sensor, or none:** you do not need to change anything.
- **Evo with a replacement Primer Orientation sensor** that does not change state during every calibration: the KHC
  primer-learn patch for Evo.
- **Revo with a replacement sensor:** the KHC primer-learn patch for Revo, after reading the notes below.
- **650/750 and 1050/1100:** keep the firmware your press has. Their firmware has no Primer Orientation sensor,
  so there is nothing for the fix to change.

### The KHC primer-learn patch: the Primer Orientation fix

Mark 7's firmware learns the Primer Orientation sensor during a calibration **only if the calibration sees the sensor
change state**, and forgets it at every restart of the press controller, which happens at every connection. A sensor
that does not change state during calibration is then never checked. The KHC patch changes two things only: **the press
learns the sensor at every CALIBRATE**, so a replacement sensor works after every restart, and it reports a version
one higher (Evo FW 20, Revo FW 31), so you can see which firmware is loaded. Everything else is
Mark 7's code, unchanged.

- **Calibrate after every connect, with an empty shell plate.** The press forgets what it learned at every restart.
- **The sensor goes in console port 2**, the Primer Orientation port of the Evo and the Revo
  ([Console ports](console-ports.md)). **On a 1050/1100, port 2 is the swage sensor:** never fit a Primer
  Orientation sensor there.
- **With no sensor fitted, keep Primer Orientation bypassed** (black) on the Sensors tab. With the fix, a sensor that
  is missing or dead at calibration is no longer silently skipped: the press stops with an index alarm on every
  cycle instead.
- **Revo:** it checks the shell-plate index at other points of its stroke than the Evo, so a sensor that works on an
  Evo must be tested again on the Revo: dummy rounds with seated primers (no index alarm),
  then pull a primer (the press must stop).
- **The KHC patch has not run on a press yet.** The FIRMWARE screen marks both builds **UNTESTED**, with the warning
  **"Not yet run on a press: test with dummy rounds and pull a primer before loading."** If you load one, run dummy
  rounds first and check that the press stops when a primer is pulled.
- They are **unofficial**, and each is for **its own model only**.
- Going back is always possible: flash Mark 7's own firmware file for your press (from Mark 7's software package)
  from a USB stick, as below.

## Backup, restore and the KHC patch

**Before every flash, the console reads the firmware your press is running back from it and keeps a copy on the
console** (the screen shows BACKUP FIRST: READING THE PRESS FIRMWARE). It reads everything twice and compares the two
reads. **If the firmware cannot be read back, nothing is flashed**: the screen says NOT FLASHED, nothing was written,
and the press keeps its firmware. (A press whose firmware cannot be read back could not be checked after flashing
either.) Reading takes from a few seconds to about two minutes for firmware the console does not recognise.

For firmware the console does not recognise, it reads the whole memory, including an upper part (above 64 KiB) that
it has not yet read on a real press. If only that upper part fails, the screen offers **FLASH WITHOUT BACKUP…**: it
warns you first that your current firmware will not be kept, then flashes and verifies as usual. If the press's
firmware reads as empty, the press controller may not allow reading at all: the console then refuses to flash (it
could not check the result either) and nothing is written.

- **BACK UP FIRMWARE** on the FIRMWARE screen reads and keeps a copy without flashing anything. Do this once when you
  first connect a press: it is also a safe test that the console can talk to the press controller's bootloader.
- **The backups** of your press model are listed under the firmware, as **BACKUPS ON THIS CONSOLE**, with the date and
  the version the press reported. The console names the ones it recognises (for example "Evo FW 19 (Mark 7 original)" or
  "KHC primer-learn patch for Evo (from Mark 7 FW 19)"); others say "Not identified". It keeps the newest five per press model, and never
  drops a copy of Mark 7's original.
- **To restore a backup**, choose it in the list and tap **RESTORE BACKUP**. It is checked against the press like any
  other file and every page is verified. A backup the console did not recognise has no model tag, so restoring it
  needs a warned confirmation.

**The KHC patch.** When the console has a backup of Mark 7's original firmware (Evo FW 19 or Revo FW 30),
the FIRMWARE screen offers **KHC primer-learn patch for Evo** (or **for Revo**) instead of the build on the card. Tap
it and then **APPLY KHC PATCH**: the console changes those few bytes in **your own backup**, checks that the result is
exactly the KHC build, byte for byte, and then flashes and verifies it as usual. If the press runs Mark 7's original
but has no backup yet, the screen tells you to tap BACK UP FIRMWARE first. A press on other firmware can still take
the KHC build the console carries.

**Test with dummy rounds.** Neither KHC build has run on a press yet. After the patch or a KHC build: calibrate with an
empty shell plate, run dummy rounds with seated primers (no index alarm), then pull a primer: the press must stop. If
anything is wrong, restore your backup.

### Firmware available

Once a KHC build has been run on a press, the console will say so when a press connects with Mark 7's version that
the build is based on, or an older KHC build: once per connection, while the press is stopped and no other alert is
open (for example **"KHC primer-learn patch for Evo (from Mark 7 FW 19) is available for this press"**), and the FIRMWARE screen will mark the
build **NEWER**. **No build is announced yet:** both are untested, so they are only listed, with their warning.
Nothing is ever flashed unless you do it yourself.

## Never cross-flash

All Mark 7 presses speak the same language to the console, so **nothing on the press warns you when it runs another
model's firmware**. The sensor inputs then mean different things (on a 1050/1100, Evo firmware would read the
swage switch as Primer Orientation) and the motion and torque settings are the other model's. Never flash the Evo
build on a Revo or the other way round, never between the Evo/Revo and the 650/750 or 1050/1100, and never between
the 1050/1100 PRO and the 1050/1100 X.

The console enforces this:

- It offers only the firmware whose **model tag** (written inside the image) matches the press it detected.
- A file from a USB stick is checked the same way, including the version its code reports; a custom or unknown file
  for another model is refused.
- **Mark 7's own original for another model**, from a USB stick, is accepted for one case only: a press that was
  flashed with the wrong model's firmware and must be put back. It needs a warned confirmation ("I UNDERSTAND: THIS
  PRESS IS REALLY A …"). Never do this on a press that is working.

## Flashing

![The firmware screen: the KHC patch for Evo on the left, the check and FLASH AND VERIFY on the right](../images/screen-firmware.png)

1. Stop the press and connect to it (PRESS, ACCEPT), so the console knows the model. Then **MENU** and
   **FIRMWARE**.
2. **1. Choose the firmware:** tap the KHC build in the list (what it changes is shown under the list), or **USB
   STICK…** to pick a `.hex` file from a USB stick (FAT or exFAT; the file can be in a folder; sticks are mounted
   read-only).
3. **2. Check:** the console shows the image's model tag and version and whether it fits: OK, **needs
   confirmation** (a warning you must accept with the orange **I UNDERSTAND: …** button first, for example "I
   UNDERSTAND: THIS PRESS IS REALLY A REVO"), or **blocked**.
4. **3. Flash:** tap **FLASH AND VERIFY** (**RESTORE BACKUP** for a backup, **APPLY KHC PATCH** for the patch). The
   press controller restarts into its bootloader (the motor is off), its firmware is read back and kept first (the
   backup; if it cannot be read, nothing is flashed), the image is written, and **every page is read back and
   verified**, with up to 3 attempts. **Do not unplug or power off anything** while it writes. CANCEL works only
   until writing starts.
5. When it is done, the console reconnects by itself and shows the version the press now reports. After a KHC build:
   calibrate with an empty shell plate, and check that the press stops when a primer is pulled.

![The override confirmation for Mark 7's original for another model, from a USB stick](../images/screen-firmware-override.png)

**Recovery:** if the press cannot identify itself (for example after an interrupted flash), the FIRMWARE screen shows
the KHC build for **the last press model the console saw**, if there is one, and checks any file against that model.
If the console has never seen a press, choose a file from a USB stick: every file then needs a warned confirmation.

## DO NOT OPERATE

![FIRMWARE INCOMPLETE: DO NOT OPERATE THE PRESS, with FLASH AGAIN and I CONFIRMED IT IS SAFE…](../images/screen-marker.png)

If a flash wrote pages but could not verify them (a cable pulled, a power cut, repeated errors), the press controller
may be running a **partial image**. The console then shows **FIRMWARE INCOMPLETE: DO NOT OPERATE THE PRESS** instead
of the home screen, keeps showing it after restarts, and **will not connect to the press**.

To recover:

- **FLASH AGAIN** (recommended): goes to FIRMWARE. The bootloader is never touched by a flash, so the press can always
  be flashed again. Flash the right image for your press and let it verify.
- **I CONFIRMED IT IS SAFE…**: only if you have re-flashed the press another way and know it is good. It needs two
  taps (the second within a few seconds: **TAP AGAIN: CONNECT TO THIS PRESS**), then the accept screen as before every
  connection.

A flash that failed **before** it wrote anything says so ("Nothing was written; the press firmware is unchanged") and
does not set DO NOT OPERATE.

## Firmware and software updates

Software updates can bring new KHC patches (descriptions of a few bytes to change), never a firmware image: the
console applies a patch to the backup of your own press's firmware. The builds the console had on its card stay
([Software updates](software-updates.md)). A recovery flash (after DO NOT OPERATE, or a press that cannot identify
itself) reads no backup first.
