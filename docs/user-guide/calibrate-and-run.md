# Calibrating and running

This page covers the buttons that move the press: STOP, CALIBRATE, RUN, END CYCLE, SINGLE, NEUTRAL, JOG, CLEAR SHELL
PLATE and die setup. Where each one sits on the press screen: [The press tabs](press-tabs.md).

> [!WARNING]
> The press console's **power switch is the only hard stop**. Keep it within reach whenever the press is powered.
> STOP on the screen is a message sent over the USB cable, not a substitute for the switch.

## Every session at a glance

1. On the home screen, tap **PRESS**, then **ACCEPT** (or **CONNECT** on the **Press detected** question).
2. Clear the shell plate and close the guard.
3. Tap **CALIBRATE** on the **Control** tab and wait for **CALIBRATED** in the status bar.
4. Check that STOP, the Remote Stop and the guard stop the press.
5. Choose the speed, then **SINGLE** for one cycle or **RUN** to run.
6. Stop with **END CYCLE** (at the end of the cycle) or **STOP** (at once).

## The run column

The same column is on the right of every tab of the press screen:

| Button | What it does | When it works |
|---|---|---|
| **RUN** | Runs the press continuously. | Only after a successful calibration in this connection, with the press idle |
| **END CYCLE** | Finishes the current cycle and stops with the press at home. On the 1050/1100 LTE it is called **HOME**. | Whenever the press is ready, except during die setup |
| **SINGLE** | Runs one cycle. The 1050/1100 LTE has no SINGLE. | As RUN |
| **STOP** | Stops the press now. | Always, on every screen of the console |

A dimmed button does nothing. If the press refuses a command (for example because the guard is open), an alert says
why.

## STOP

- **STOP acts the moment a finger touches it**, from any finger, even while another finger is on the screen. It does
  not wait for you to lift the finger.
- It goes out ahead of anything else, cancels moves that were waiting to be sent, and closes any open question.
- The press confirms every STOP. **If it does not confirm within about a second**, the console resets the press
  controller through the USB cable and shows the CRITICAL alert **STOP NOT CONFIRMED**. Switch off the press
  console's power ([CRITICAL alerts](alerts.md#critical-alerts)).
- After a stop, the **Stopped** alert offers **NEUTRAL** (below) and **OK**.

## CALIBRATE

The press keeps its calibration only while it runs: **every connection restarts the press controller**, and the
calibration is gone. RUN and SINGLE stay locked until the press confirms a new calibration.

> [!IMPORTANT]
> Calibrate after every connection, **with an empty shell plate**.

1. Clear the shell plate and close the guard.
2. On the **Control** tab, tap **CALIBRATE**. The status bar shows **CALIBRATING** while the press makes its
   calibration stroke.
3. When the press reports success, the status bar shows **CALIBRATED**, and **RUN** and **SINGLE** unlock. No alert
   is shown for a success.

CALIBRATE works only while the press is idle, and not during die setup. If the press refuses or aborts the
calibration (the guard open, the press busy or blocked), the **Calibration failed** alert says so and RUN stays
locked.

**Primer Orientation** (Evo and Revo models): the press learns this sensor during the calibration. With Mark 7's
firmware it is learned only when the calibration sees the sensor change state; the KHC primer-learn patch learns it at
every calibration ([The KHC primer-learn patch](firmware.md#the-khc-primer-learn-patch-the-primer-orientation-fix)).

## RUN, END CYCLE and SINGLE

1. Choose the speed under **ROUNDS PER HOUR** on the Control tab. The speed always starts at the slowest when the
   console connects. (The figures are Mark 7's own labels; while running, the status bar shows the rate the press
   reports.)
2. Tap **SINGLE** for one cycle, or **RUN** to run until you stop it. A USB [foot pedal](foot-pedal.md) can start
   SINGLE too.
3. For a normal stop, tap **END CYCLE**: the status bar shows **ENDING**, and the press stops at home at the end of
   the cycle. Tap **STOP** to stop at once.

A run also ends when a sensor stops the press, or at the end of the cycle in which a counter on the Monitors tab
reaches its stop level ([Monitors](press-tabs.md#monitors)).

If the press does not answer RUN, SINGLE or END CYCLE within about a second, the console resets the press controller
and shows the CRITICAL alert **PRESS NOT ANSWERING**: switch off the press console's power. (When its motor reports a
fault as a cycle starts, the press firmware can step the motor without answering anything; the reset is how the
console stops that.)

## NEUTRAL

**NEUTRAL** is offered on the **Stopped**, **Jam: Digital Clutch** and **Index torque** alerts. It switches the motor
off so the press can be moved by hand, for example to clear a jam.

After NEUTRAL, **RUN stays locked until you calibrate again**, because the press may no longer be where it was
calibrated. Calibration needs an empty shell plate, so clear the plate first.

## JOG

**JOG UP** and **JOG DOWN** on the Control tab move the press a short step. They work only while the press is idle.
Every model has them except the 1050/1100 LTE.

> [!WARNING]
> **JOG moves the press even with the guard open.** Keep your hands out of the press.

On a 1050/1100, **remove the Dillon ratchet before you jog** (the 1050 manual): with it fitted, jogging from mid-stroke
jams the press. The Control tab says so too.

## CLEAR SHELL PLATE

**CLEAR SHELL PLATE** (Control tab, 1050/1100 PRO and X) runs the press's own shell-plate clearing move. It works only
while the press is idle, and it **also moves the press with the guard open**.

## Die setup

Every model except the 1050/1100 LTE has die setup, on the **Setup** tab:

1. With the press idle, tap **START DIE SETUP**.
2. Move the press with **MOVE TO TOP** and **MOVE TO BOTTOM** (on the 650/750, **MOVE TO BOTTOM** comes first,
   because the platform moves). Adjust your dies.
3. Tap **FINISH DIE SETUP** to end it. (The 650/750 manual ends die setup with END CYCLE; on this console use FINISH
   DIE SETUP.)

During die setup the sensors and the powder measure are off, and **these moves run with the guard open**. END CYCLE,
CALIBRATE and MENU are not available until you finish die setup.

## When the connection resets

If the press controller restarts, the press stops answering for 8 seconds, or the USB connection fails, the console
shows **Connection reset** and reconnects by itself. After a USB failure it asks you to check the cable instead: plug
it back in, and the **Press detected** question offers **RECONNECT**.

Every reconnection restarts the press controller, so **calibrate again**, with an empty shell plate. Your settings
are sent to the press again automatically.

**RECONNECT** on the **Settings** tab does the same on purpose.
