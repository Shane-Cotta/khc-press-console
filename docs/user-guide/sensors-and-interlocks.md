# Sensors and interlocks

![The Sensors tab of an Evolution](../images/screen-press-evolution-sensors.png)

Each sensor on the **Sensors** tab is either:

- **ACTIVE** (green): the press checks it and stops (or ends the run) when it trips;
- **BYPASSED** (black): the press ignores it. **A bypassed sensor or interlock does not stop the press.**

The press itself forgets these settings at every restart, so the console sends them again after every connection.

## What starts active

| | On a new console | At every connection |
|---|---|---|
| **Remote Stop** | ACTIVE | **Switched ACTIVE**, whatever it was before |
| **Machine Guard** (the **Safety Shield** on a 1050) | ACTIVE | **Switched ACTIVE**, whatever it was before |
| **TorqueSense** | ACTIVE | **Switched ACTIVE**, whatever it was before (it is on the Control tab) |
| Top Slowdown (650) | ACTIVE | as you left it |
| PrimerSense on the Revolution | ACTIVE | as you left it |
| Every other sensor (DecapSense, SwageSense, BulletSense, PrimerSense, Primer Orientation, Powder Measure, Digital Powder Check) | BYPASSED, as in Mark 7's app | as you left it |

**Turn on the sensors that are fitted to your press**, and check that each one stops the press before you rely on
it. An unfitted sensor that is ACTIVE can stop every run.

## Bypassing an interlock

- **Remote Stop** and **Machine Guard** are safety interlocks. Bypassing either one **asks for confirmation** first.
  It then shows **BYPASSED**, and the tab says **INTERLOCK BYPASSED**.
- The bypass lasts **until the next connection**: every connection switches both back to ACTIVE.
- TorqueSense can be bypassed on the Control tab without a confirmation; it too is switched back to ACTIVE at the
  next connection.
- The foot pedal cannot be armed while the Remote Stop or the Machine Guard is bypassed, and bypassing either one
  disarms it.

Bypass an interlock only for a specific reason, never while anyone can reach into the press, and turn it back on as
soon as you can.

## What the guard does and does not stop

With the **Machine Guard** (or the 1050's **Safety Shield**) open, the press refuses **only RUN, SINGLE CYCLE, END
CYCLE and CALIBRATE** (on the 1050 LTE: RUN, HOME and CALIBRATE). **Every other move still moves the press with the
guard open:** JOG UP / JOG DOWN, CLEAR SHELL PLATE, CLEAR CASE (the SwageSense alert's button) and the die-setup moves,
on the models that have them. This is how the press firmware works, with Mark 7's app as well. The guard alert and the
notes on the Sensors tab name the moves your press has.

## Notes on particular sensors

- **Primer Orientation** (Evolution, Revolution): learned during calibration; its checks run only once it has been
  learned. With Mark 7's firmware a calibration learns it only if it sees the sensor change state, and every restart
  of the press (every connection) forgets it. The custom "pocketlearn" firmware learns it at every calibration
  ([Firmware](firmware.md#the-custom-pocketlearn-builds)).
- **DecapSense:** plug it in **before** the console connects: the press looks for it only when it starts, and every
  connection restarts it. The press remembers a DecapSense it has seen, so if you unplug one, either plug it back in
  or bypass DecapSense.
- **Digital Powder Check** and **Powder Measure:** bypass them if they are not fitted; an unfitted one is likely to
  stop runs with a malfunction or powder check alert.
- **650 / 1050:** these presses have no Primer Orientation sensor, and the console does not show one. On a 1050,
  console **port 2 is SwageSense**: never plug a DIY Primer Orientation sensor in there. On these presses the Powder
  Measure input is always kept bypassed.

Which sensor goes into which port: [Console ports](console-ports.md). What each alert means: [Alerts](alerts.md).
