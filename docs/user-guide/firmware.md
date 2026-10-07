# Press firmware

The press controller inside the press console runs Mark 7's firmware. **You do not need to change it to use KHC Press
Console**: the console works with the firmware your press shipped with. The **FIRMWARE** screen is for when you want
to: to keep a backup of your press's firmware, to apply the KHC primer-learn patch, or to flash a file of your own.

> [!WARNING]
> Flashing rewrites the program that drives the press motor. Flash only with the press stopped and your hands clear,
> never unplug or power off anything while it writes, and after any flash calibrate with an empty shell plate and test
> with dummy rounds before you load.

## What the console carries

**No firmware image ships with KHC Press Console**, ours or Mark 7's. What the console carries is the **KHC
primer-learn patch** for the Evo and the Revo: a description of a few bytes to change. The console applies it to **a
backup of your own press's firmware** (below). The release page carries the same patch descriptions (`khc-*.json`), for
reference only.

| On the FIRMWARE screen | For | Made from | The press then reports |
|---|---|---|---|
| **KHC primer-learn patch for Evo** | the Evo (Mark 7 Apex 10 Evolution) **only** | Mark 7 FW 19 | Evo FW 20 |
| **KHC primer-learn patch for Revo** | the Revo (Mark 7 Revolution) **only** | Mark 7 FW 30 | Revo FW 31 |

There is no KHC firmware for the 650/750, the 1050/1100, the Evo PRO, the Duals or the GAP PRO: on those presses the
FIRMWARE screen says "This console carries no firmware file for this press." You can still back up the press's
firmware, restore a backup, and flash a file of your own from a USB stick.

Cards written with version 0.3.0b3 or earlier also carry the two KHC builds themselves, and still offer them in the
list (shown as **KHC patch for Evo** and **KHC patch for Revo**, marked **UNTESTED**).

## Which one to choose

- **Evo or Revo with Mark 7's Primer Orientation sensor, or none:** you do not need to change anything.
- **Evo with a replacement Primer Orientation sensor** that does not change state during every calibration: the KHC
  primer-learn patch for Evo.
- **Revo with a replacement sensor:** the KHC primer-learn patch for Revo, after reading the notes below.
- **650/750 and 1050/1100:** keep the firmware your press has. These presses have no Primer Orientation sensor, so
  there is nothing for the fix to change.

## The KHC primer-learn patch: the Primer Orientation fix

Mark 7's firmware learns the Primer Orientation sensor during a calibration **only if the calibration sees the sensor
change state**, and forgets it at every restart of the press controller, which happens at every connection. A sensor
that does not change state during calibration is then never checked. The KHC patch changes two things only:

- **the press learns the sensor at every CALIBRATE**, so a replacement sensor works after every restart;
- it reports a version **one higher** (Evo FW 20, Revo FW 31), so you can see which firmware is loaded.

Everything else is Mark 7's code, unchanged. The patch is **unofficial**, and each one is for **its own model only**.

- **Calibrate after every connect, with an empty shell plate.** The press forgets what it learned at every restart.
- **The sensor goes in console port 2**, the Primer Orientation port of the Evo and the Revo
  ([Console ports](console-ports.md)). **On a 1050/1100, port 2 is the swage sensor:** never fit a Primer Orientation
  sensor there.
- **With no sensor fitted, keep Primer Orientation bypassed** on the Sensors tab. With the patch, a sensor that is
  missing or dead at calibration is no longer silently skipped: the press stops with an index alarm on every cycle.
- **Revo:** it checks the shell-plate index at other points of its stroke than the Evo, so a sensor that works on an
  Evo must be tested again on the Revo: dummy rounds with seated primers (no index alarm), then pull a primer (the
  press must stop).

> [!CAUTION]
> **The KHC patch has not been validated on a press.** The first press test, on a Revo, ran an empty shell plate one
> index before it stopped, where Mark 7's own firmware stops before the tool head moves; this is still being traced.
> The FIRMWARE screen warns "Not yet run on a press: test with dummy rounds before loading." Use a KHC build with dummy
> rounds only, check that **Primer Orientation is ACTIVE** (green) on the Sensors tab, and check that the press stops
> when a primer is pulled. **RESTORE BACKUP** puts your press's own firmware back.

## Backing up your press firmware

**Before every flash, the console reads the firmware your press is running and keeps a copy on the console.** It
reads everything twice and compares the two reads. **If the firmware cannot be read back, nothing is flashed**: the
screen says NOT FLASHED, and the press keeps its firmware.

To make a backup without flashing anything (do it once when you first connect a press; it is also a safe test that
the console can talk to the press controller's bootloader):

1. Stop the press. Connect to it (**PRESS**, **ACCEPT**), so the console knows the model.
2. Tap **MENU**, then **FIRMWARE**.
3. Tap **BACK UP FIRMWARE**. The press controller restarts into its bootloader (the motor is off) and the screen
   shows **READING THE PRESS FIRMWARE** with its progress.
4. When it is done, the screen says "Backed up:" and what it kept. The console reconnects to the press: calibrate
   again before you run.

Reading takes from a few seconds to about two minutes for firmware the console does not recognise.

- **The backups** of your press model are listed on the FIRMWARE screen under **BACKUPS ON THIS CONSOLE**, with the
  date and the version the press reported. The console names the ones it recognises ("Evo FW 19 (Mark 7 original)",
  "KHC primer-learn patch for Evo (from Mark 7 FW 19)"); others say "Not identified".
- It keeps the newest five per press model, and **never drops a copy of Mark 7's original**.
- For firmware it does not recognise, the console reads the whole memory, including an upper part (above 64 KiB) it
  has not yet read on a real press. If only that upper part fails, the screen offers **FLASH WITHOUT BACKUP…**: it
  warns you that your current firmware will not be kept, then flashes and verifies as usual.
- If the press firmware reads as empty, the bootloader may not allow reading. The console then refuses to flash (it
  could not check the result either) and nothing is written.

## Applying the KHC patch

1. Make a backup first (above). The patch needs a kept backup of Mark 7's original firmware for your press model
   (Evo FW 19 or Revo FW 30). If the press runs Mark 7's original but has no backup yet, the screen tells you to tap
   BACK UP FIRMWARE first.
2. On the FIRMWARE screen, tap **KHC primer-learn patch for Evo** (or **for Revo**) in the list. The **?** under the
   list explains it in full.
3. Tap **APPLY KHC PATCH**. The console changes those few bytes in **your own backup**, checks that the result is
   exactly the KHC build, byte for byte, then flashes and verifies it ([Flashing step by step](#flashing-step-by-step)).
4. When the console has reconnected: calibrate with an empty shell plate, turn **Primer Orientation** ACTIVE, run dummy
   rounds with seated primers (no index alarm), then pull a primer: the press must stop. If anything is wrong,
   restore your backup.

If KHC withdraws a patch, the console stops offering it after its next update check and says "This KHC patch was
withdrawn by KHC Precision".

## Restoring a backup

1. On the FIRMWARE screen, choose a backup under **BACKUPS ON THIS CONSOLE**.
2. Tap **RESTORE BACKUP**. It is checked against the press like any other file, and every page is verified.

A backup the console did not recognise has no model tag, so restoring it needs a warned confirmation.

## Flashing step by step

![The FIRMWARE screen: the KHC patch for Evo marked UNTESTED on the left, the check and FLASH AND VERIFY on the right](../images/screen-firmware.png)

1. Stop the press and connect to it (**PRESS**, **ACCEPT**), so the console knows the model. Then **MENU** and
   **FIRMWARE**.
2. **1. CHOOSE THE FIRMWARE:** tap the patch, a build or a backup in the list, or **USB STICK…** to pick a `.hex` file
   from a USB stick (FAT or exFAT; the file can be in a folder; sticks are mounted read-only).
3. **2. Check:** the console shows the model tag and the version the image reports, and whether it fits: OK,
   **Needs confirmation** (a warning you must accept first with the orange **I UNDERSTAND: …** button, for example
   "I UNDERSTAND: THIS PRESS IS REALLY A REVO"), or **Blocked**.
4. **3. Flash:** tap **FLASH AND VERIFY** (**APPLY KHC PATCH** for the patch, **RESTORE BACKUP** for a backup).
   - The press controller restarts into its bootloader (the motor is off).
   - Its firmware is read and kept first (**BACKUP FIRST**); if it cannot be read, nothing is flashed.
   - The image is written, and **every page is read back and verified**, with up to 3 attempts.
   - **CANCEL** works only until writing starts. **Do not unplug or power off anything** while it writes.
5. When it is done ("Flashed and verified"), the console reconnects by itself and shows the version the press now
   reports. Calibrate with an empty shell plate before you run.

A new flash needs a running trial or a license, like a new connection ([The trial and your license](license.md)).

## Never cross-flash

All Mark 7 presses speak the same language to the console, so **nothing on the press warns you when it runs another
model's firmware**. The sensor inputs then mean different things (on a 1050/1100, Evo firmware would read the swage
switch as Primer Orientation), and the motion and torque settings are the other model's. Never flash the Evo build on
a Revo or the other way round, never between the Evo/Revo and the 650/750 or 1050/1100, and never between the
1050/1100 PRO and the 1050/1100 X.

The console enforces this:

- It offers only the firmware whose **model tag** (written inside the image) matches the press it detected.
- A file from a USB stick is checked the same way, including the version its code reports. A custom or unknown file
  for another model is refused.
- **Mark 7's own original for another model**, from a USB stick, is accepted for one case only: a press that was
  flashed with the wrong model's firmware and must be put back. It needs a warned confirmation ("I UNDERSTAND: THIS
  PRESS IS REALLY A …"). Never do this on a press that is working.

![The override confirmation: Mark 7's original for another model from a USB stick, with the orange I UNDERSTAND button](../images/screen-firmware-override.png)

## Recovery

If the press cannot identify itself (for example after an interrupted flash), the FIRMWARE screen says "Recovery:" and
works from **the last press model the console saw**: it shows that model's firmware and backups, and checks any file
against that model. If the console has never seen a press, choose a `.hex` file from a USB stick (Mark 7's update file
for your model): every file then needs a warned confirmation. A recovery flash reads no backup first.

## DO NOT OPERATE

![FIRMWARE INCOMPLETE: DO NOT OPERATE THE PRESS, with FLASH AGAIN and I CONFIRMED IT IS SAFE…](../images/screen-marker.png)

If a flash wrote pages but could not verify them (a cable pulled, a power cut, repeated errors), the press controller
may be running a **partial image**. The console then shows **FIRMWARE INCOMPLETE: DO NOT OPERATE THE PRESS** instead
of the home screen, keeps showing it after restarts, and **will not connect to the press**.

To recover:

- **FLASH AGAIN** (recommended): opens FIRMWARE. A flash never touches the bootloader, so the press can always be
  flashed again. Flash the right image for your press (a backup, the patch, or Mark 7's file from a USB stick) and let
  it verify. This works even without a trial or license.
- **I CONFIRMED IT IS SAFE…**: only if you have re-flashed the press another way and know it is good. It needs two
  taps (the second within a few seconds: **TAP AGAIN: CONNECT TO THIS PRESS**), then the accept step as before every
  connection.

A flash that failed **before** it wrote anything says so ("Nothing was written; the press firmware is unchanged") and
does not set DO NOT OPERATE.

## Firmware available

Once a KHC build has been validated on a press, the console will tell you when a press connects with the Mark 7
version it is based on, or an older KHC build: the **Firmware available** alert, once per connection, while the press
is stopped (for example "KHC primer-learn patch for Evo is available for this press"), and the FIRMWARE screen marks
it **NEWER**. **No build is announced yet:** both are unvalidated, so they are only listed, with their warning. The
console never changes the press firmware by itself.

## Firmware and software updates

Software updates can bring new KHC patches (descriptions of a few bytes to change), never a firmware image. The
backups on the console are kept across software updates ([Software updates and Wi-Fi](software-updates.md)).
