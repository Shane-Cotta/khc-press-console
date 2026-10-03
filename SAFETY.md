# Safety

KHC Press Console controls a reloading press: a machine with a servo motor that can exert a lot of force, pinch points
around the ram, shell plate and dies, and live primers and powder. KHC Press Console is **BETA software** and **unofficial**:
it is not made, endorsed or supported by Mark 7 Reloading. It is provided without any warranty
([Terms of use](TERMS.md)). You use it at your own risk.

## The one rule: the console's power switch

**The Mark 7 press console has no separate emergency-stop button. Its power switch is the only hard stop.** Keep it
within reach whenever the press is powered. The STOP sign on the screen is a message sent over the USB cable. It is
not a substitute for the power switch.

**Switch off the console power** when:

- the screen shows a **CRITICAL** alert (full screen, red, ending in "Switch off the console power now");
- the press does not stop at once when you tap STOP, press the remote stop or open the guard;
- the screen goes dark, freezes, or shows "the console app has stopped";
- the touch screen stops responding while the press can move;
- anything else is not as you expect while the press can move.

Pulling the Raspberry Pi's plug does **not** stop the press: the press console's switch does.

## Before every session

- Know where the console's power switch is, and keep your hand near it for the first cycles.
- Keep hands and tools out of the press whenever it is powered and connected.
- Check that **STOP**, the **Remote Stop** and the **Machine Guard** (the Safety Shield on a 1050/1100) stop the press
  before you load components.
- For your first sessions with KHC Press Console, after every software or firmware update, and after any change of
  hardware: use an **empty shell plate**.
- Follow your press manual for everything the press itself does: dies, shell plate, powder, primers, calibration.

## STOP

- **STOP is on every screen**, in the same place on the right, and it is checked before anything else you touch.
  It acts the moment a finger touches it (it does not wait for you to lift the finger), and it goes out ahead of
  anything else waiting to be sent. It also cancels moves that were waiting to be sent, and closes any open question
  (a bypass confirmation, a firmware override, a turn-off question).
- **A STOP that is not confirmed is reported.** If the press does not confirm a STOP within about a second, the
  console resets the press controller through the USB cable (which stops the motor) and shows **STOP NOT CONFIRMED**
  with "Switch off the console power now". Do it.
- **The press can stop answering while its motor moves.** When the motor reports a fault as RUN, SINGLE CYCLE or END
  CYCLE starts, the press firmware can keep stepping the motor in a loop that answers nothing: not STOP, and not the
  Remote Stop. If the guard is opened during it, the run can even start with the guard open. The console watches for
  this: any RUN, SINGLE, END CYCLE or STOP that the press does not answer within about a second gets the controller
  reset and the CRITICAL alert **PRESS NOT ANSWERING**. If the press moves after it reported a stop, you get **PRESS
  KEPT MOVING**. Both tell you to switch off the console power.
- These **CRITICAL alerts** stay on the screen until you tap **CONSOLE IS OFF**, and they sound an alarm until then
  (if sounds are on). STOP stays tappable on them.
- **If the touch screen stops working** the console shows **TOUCHSCREEN NOT WORKING**: STOP on the screen cannot work
  then. Use the remote stop, or the console's power switch.

## If the console software stops

- If the console app crashes or hangs, the Raspberry Pi resets the press controller (the motor stops) and starts the
  app again within a few seconds. Nothing moves until you tap ACCEPT and calibrate again.
- If it keeps failing, it stops trying and the screen says **"the console app has stopped"**: the press is then
  **not controlled from the screen**. Switch the press console off before you touch the press.
- If the Raspberry Pi loses power, or the USB cable is pulled, nothing can be sent to the press. A running press may
  keep cycling. **Switch off the console power.**

## RUN needs a calibration

- RUN and SINGLE unlock only after the press confirms a successful **CALIBRATE** in the current connection. They lock
  again after every new connection, every restart of the press controller, and NEUTRAL. A refused or failed
  calibration keeps them locked.
- **Every connection restarts the press controller**, and the press forgets its calibration (and, with Mark 7's
  firmware, the learned Primer Orientation sensor). Calibrate after every connection, with an **empty shell plate**.
- After **NEUTRAL** (motor off, the press can be moved by hand) RUN stays locked until you calibrate again, even
  where your press manual goes straight back to RUN: the press may no longer be where it was calibrated.

## Interlocks and bypass

- **Remote Stop, the Machine Guard and Index torque (TorqueSense™) are switched ON (ACTIVE) every time the
  console connects**, whatever they were before. A bypass lasts until the next connection.
- **Bypassing the Remote Stop or the Machine Guard asks for confirmation.** The switch then shows **BYPASSED**.
- **A bypassed sensor or interlock does not stop the press.** With the Remote Stop bypassed, the remote stop button
  does nothing. With the Machine Guard bypassed, the press runs with the guard open. Bypass an interlock only for a
  specific reason, never while anyone can reach into the press, and turn it back on as soon as you can.
- **An open guard stops only four commands.** With the Machine Guard (or a 1050/1100's Safety Shield) open, the press
  refuses only RUN, SINGLE CYCLE, END CYCLE and CALIBRATE. **Every other move still moves the press with the guard
  open:** JOG UP / JOG DOWN, CLEAR SHELL PLATE, CLEAR CASE (the swage sensor alert's button) and the die-setup moves.
  Keep your hands out of the press whenever it is powered, guard open or not.
- Other sensors start **BYPASSED** on a new console (as in Mark 7's app), except the primer sensor (PrimerSense™) on the Revo. Turn
  on the ones fitted to your press and check that each one stops the press.

Details: [Sensors and interlocks](docs/user-guide/sensors-and-interlocks.md).

## After a jam: check for a double charge

After a **Jam**, **Index torque (TorqueSense™)** or **Swage sensor (SwageSense™)** stop a case can be left half-way through a station, and running on
can give a round **a double charge or no charge**. The alert says what to check on your press. When in doubt, switch
the press off, clear it by hand, and discard the affected rounds.

## The foot pedal

A USB foot pedal can start **SINGLE CYCLE** only. With it armed your hands are free while the press moves: keep them
clear. **The pedal is never a stop.** It cannot be armed while the Remote Stop or the Machine Guard is bypassed, and it
disarms itself on any stop. See [Foot pedal](docs/user-guide/foot-pedal.md).

## Firmware

- You do not need to change your press firmware to use KHC Press Console.
- **Each firmware image is for its own press model only.** All Mark 7 presses speak the same language to the
  console, so nothing on the press tells you when it runs another model's firmware: the sensor inputs and the motion
  and torque settings would be wrong. The console refuses another model's firmware, except Mark 7's own original for
  putting back a press that was flashed with the wrong one, and then only after a warning.
- The **KHC primer-learn patch** (for the Evo, from Mark 7 FW 19, and for the Revo, from Mark 7 FW 30) is
  unofficial and **has not yet run on a real press**. Test it with dummy rounds and pull a primer before loading; the
  Revo build must be validated on a Revo itself. With a KHC build, calibrate after every connect with an empty shell plate,
  and keep Primer Orientation bypassed if no sensor is fitted.
- If a firmware update is interrupted after it started writing, the console shows **DO NOT OPERATE THE PRESS** and
  will not connect until the press is flashed again. Do not run a press in that state.

Details: [Firmware](docs/user-guide/firmware.md).

## Software updates

Updates are installed only when you tap INSTALL, never while the press runs, and the console disconnects from the
press first. The update packages are checked against the checksums published on the releases page, but **they are not
yet digitally signed**: whoever controls the release account, or a USB stick you put in the console, could install
software that drives your press. Install only from the official releases page or from a stick you prepared yourself.
See [Software updates](docs/user-guide/software-updates.md).

## 650/750 and 1050/1100 presses

KHC Press Console supports Mark 7's drives for the Dillon 650 and 750 (the **650/750 PRO** and **650/750 X**; we believe a
750 drive reports itself as a 650 model) and for the Dillon 1050 and 1100 (the **1050/1100 PRO**, **X** and **LTE**). **None of these has been run with KHC Press Console
yet**; the support comes from Mark 7's manuals and from reading their firmware.

- On a 650/750, the Setup tab's **Primer depth (0 = deepest)** sets how deep primers are seated. Change it one step at a
  time and check seated primers with SINGLE CYCLE before you RUN.
- On a 1050/1100, **JOG needs the Dillon ratchet removed** (the 1050 manual): with it fitted, jogging from mid-stroke jams
  the press.
- **Never connect a DIY Primer Orientation sensor to a 1050/1100.** Its console port 2 is the swage sensor: the press
  would read the sensor as a swage switch.

## Not yet verified on real hardware

At the time of this BETA, KHC Press Console has been developed and tested against press simulators (a model of every press
build, and Mark 7's real firmware running in a microcontroller simulator), and the SD card has been built and started
in a container. These have **not yet been verified on real hardware**:

- **Running a real press** with KHC Press Console, at all, on any model.
- **The Raspberry Pi 4 and 5 themselves:** the screen, the touch panel, sound over HDMI, Wi-Fi and the boot time.
- **The press console's USB-serial chip** with the Pi, and the controller reset through the cable.
- **Firmware flashing** on a real press controller, and the KHC primer-learn patch for the Evo and the Revo on a press.
- **Software updates and Wi-Fi** on a real console.
- **The foot pedal** with a real USB pedal.

Until these are verified, treat every session as a test: the console's power switch within reach, an empty shell
plate first, and one careful step at a time. Please report what you find as an
[issue](https://github.com/Shane-Cotta/khc-press-console/issues/new/choose).
