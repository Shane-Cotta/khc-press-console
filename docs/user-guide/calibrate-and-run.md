# Calibrating and running

## The column on the right

Every tab of the press screen has the same column on the right:

| Button | What it does |
|---|---|
| **RUN** | Runs the press continuously. **Locked until the press has calibrated** in this connection. |
| **END CYCLE** | Stops at the end of the current cycle, with the press at home. (On the 1050/1100 LTE it is called **HOME**.) |
| **SINGLE** | Runs one cycle. Locked until calibrated, like RUN. (The 1050/1100 LTE has no SINGLE.) |
| **STOP** | Stops the press now. On every screen of the console, not only here. |

Disabled buttons are drawn dimmed and do nothing. If the press refuses a command (for example because the guard is
open), an alert says so.

## STOP

- **STOP acts the moment your finger touches it**, from any finger, even while another finger is on the screen.
- It is sent ahead of anything else, and cancels moves that were waiting to be sent.
- The press confirms a STOP. **If it does not confirm within about a second**, the console resets the press
  controller through the USB cable and shows the CRITICAL alert **STOP NOT CONFIRMED**: switch off the console power
  ([Alerts](alerts.md#critical-alerts)).
- After a stop, the **Stopped** alert offers **NEUTRAL** (see below) and **OK**.

## CALIBRATE

The press does not keep its calibration: **every connection restarts the press controller**, and with it the
calibration is gone. Calibrate after every connection, **with an empty shell plate**.

1. Clear the shell plate. Close the guard.
2. On the **Control** tab, tap **CALIBRATE**. The status bar shows **CALIBRATING**; the press moves through its
   calibration stroke.
3. When the press reports success the status bar shows **CALIBRATED**, and **RUN** and **SINGLE** unlock.

If the press refuses or aborts the calibration (guard open, busy, or blocked), the **Calibration failed** alert says
so and RUN stays locked. CALIBRATE is available only while the press is idle, and not during die setup.

**Primer Orientation** (Evo and Revo): the press also learns this sensor during calibration. With Mark 7's
firmware, it is learned only when the calibration sees the sensor change state; the KHC firmware learns it at every
calibration ([Firmware](firmware.md#the-khc-primer-learn-patch-the-primer-orientation-fix)).

## RUN, END CYCLE and SINGLE

- **Speed:** choose it on the Control tab. The buttons show rounds per hour (the numbers come from Mark 7's app).
  The speed always starts at the slowest when the console connects.
- **RUN** runs until you stop it, a sensor stops it, or a monitor's stop level is reached
  ([Monitors](press-tabs.md#monitors)).
- **END CYCLE** finishes the current cycle and stops at home. Use it for a normal stop.
- **SINGLE** runs one cycle. A USB [foot pedal](foot-pedal.md) can do the same.
- If the press does not answer RUN, SINGLE or END CYCLE within about a second, the console resets the press
  controller and shows **PRESS NOT ANSWERING**: switch off the console power. (The press firmware can step the motor
  without answering when the motor reports a fault at the start of a cycle; the reset is how the console stops that.)

## NEUTRAL

**NEUTRAL** (offered on a stop alert) switches the motor off so the press can be moved by hand, for example to clear a
jam. After NEUTRAL, **RUN stays locked until you calibrate again**: the press may no longer be where it was calibrated.
Calibration needs an empty shell plate, so clear the plate first.

## JOG

**JOG UP** and **JOG DOWN** (on the Control tab of the models that have them) move the press a short step. They are
available only while the press is idle. **JOG moves the press even with the guard open.**

On a 1050/1100, **remove the Dillon ratchet before you jog** (the 1050 manual): with it fitted, jogging from mid-stroke
jams the press.

## CLEAR SHELL PLATE (1050/1100 models)

**CLEAR SHELL PLATE** on the Control tab of a 1050/1100 runs the press's shell-plate clearing move. It also moves with the
guard open.

## Die setup

On the **Setup** tab (models with die setup): **START DIE SETUP**, then **MOVE TO TOP** / **MOVE TO BOTTOM** (on the
650/750 the order is reversed, because the platform moves) and **FINISH DIE SETUP**. The sensors and the powder measure are
disabled during die setup, and these moves run with the guard open. RUN, END CYCLE and CALIBRATE are not available
until you finish die setup.

## When the connection resets

If the press restarts, stops answering for 8 seconds, or the USB connection fails, the console shows **Connection
reset** and reconnects (or, for a USB failure, asks you to check the cable). Every reconnection restarts the press
controller: **calibrate again**. Your settings are sent to the press again automatically.

**RECONNECT** on the **Settings** tab does the same on purpose.
