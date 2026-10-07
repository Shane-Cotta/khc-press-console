# Sensors and interlocks

![The Sensors tab of an Evo: buttons in console-port order, Remote Stop and Machine Guard ACTIVE, the rest BYPASSED](../images/screen-press-evolution-sensors.png)

Each sensor on the **Sensors** tab is either:

- **ACTIVE** (green): the press checks it, and stops (or ends the run) when it trips;
- **BYPASSED** (dark): the press ignores it.

> [!WARNING]
> **A bypassed sensor or interlock does not stop the press.** With the Remote Stop bypassed, the remote stop button
> does nothing. With the Machine Guard bypassed, the press runs with the guard open.

The press itself forgets these settings at every restart, so the console sends them again after every connection.
Each button shows the console port its sensor plugs into ([Console ports](console-ports.md)).

## What starts active

The settings are kept per press model. The first time a model connects, it gets the defaults below.

| Sensor | The first time | At every connection |
|---|---|---|
| **Remote Stop** | ACTIVE | **Switched ACTIVE**, whatever it was before |
| **Machine Guard** (the **Safety Shield** on a 1050/1100) | ACTIVE | **Switched ACTIVE**, whatever it was before |
| **Index torque** (TorqueSense™, on the Control tab) | ACTIVE | **Switched ACTIVE**, whatever it was before |
| **Top Slowdown** (650/750, on the Setup tab) | ON | as you left it |
| **Primer sensor** (PrimerSense™) on the Revo, the Revo Dual and the GAP PRO | ACTIVE | as you left it |
| Every other sensor | BYPASSED, as in Mark 7's app | as you left it |

## Turning on the sensors you have

1. Switch the press console off, plug in the sensors, and switch it on again.
2. Connect, accept and calibrate as usual.
3. On the **Sensors** tab, tap each sensor that is fitted so it shows **ACTIVE** (green).
4. **Check each one stops the press** before you rely on it (for example, with a clear shell plate, RUN or SINGLE
   must raise the bullet sensor alert).

Leave unfitted sensors **BYPASSED**: an unfitted sensor that is ACTIVE can stop every run.

## Which sensors each press has

| Press | Sensors tab |
|---|---|
| Evo, Evo PRO, Revo, GAP PRO | Remote Stop, Machine Guard, Decap sensor, Swage sensor, Bullet sensor, Primer sensor, Primer Orientation, Powder Measure, Powder check |
| Evo Dual, Revo Dual | as above without the Decap sensor, plus Powder check 2 |
| 650/750 PRO and X | Remote Stop, Machine Guard, Decap sensor, Bullet sensor, Primer sensor, Powder check |
| 1050/1100 PRO, X and LTE | Remote Stop, Safety Shield, Decap sensor, Swage sensor, Bullet sensor, Primer sensor, Powder check |

Index torque is on the Control tab, and the 650/750's Top Slowdown on the Setup tab.

## Bypassing an interlock

The **Remote Stop** and the **Machine Guard** (Safety Shield) are safety interlocks.

1. Tap the interlock on the Sensors tab.
2. The console asks **"Bypass … ?"**: "The press will ignore it until you turn it back on." For the guard it also says
   what an open guard does and does not stop.
3. Tap **BYPASS** to confirm, or **CANCEL**. The button then shows **BYPASSED**, and the tab says **INTERLOCK
   BYPASSED** in red.

- The bypass lasts **until the next connection**: every connection switches both back to ACTIVE.
- **Index torque** (TorqueSense™) is switched on the Control tab, without a confirmation. It is also switched back to
  ACTIVE at the next connection.
- The foot pedal cannot be armed while the Remote Stop or the guard is bypassed, and bypassing either one disarms it.

Bypass an interlock only for a specific reason, never while anyone can reach into the press, and turn it back on as
soon as you can.

## What the guard does and does not stop

> [!WARNING]
> With the **Machine Guard** (or the 1050/1100's **Safety Shield**) open, the press refuses **only RUN, SINGLE CYCLE,
> END CYCLE and CALIBRATE** (on the 1050/1100 LTE: RUN, HOME and CALIBRATE). **Every other move still moves the press
> with the guard open:** JOG UP and JOG DOWN, CLEAR SHELL PLATE, CLEAR CASE (the swage sensor alert's button) and the
> die-setup moves, on the models that have them.

This is how the press firmware works, with Mark 7's app as well. The guard alert and the Sensors tab's **?** notes
name the moves your press has. Keep your hands out of the press whenever it is powered, guard open or not.

## Notes on particular sensors

- **Primer Orientation** (Evo and Revo models): learned during calibration; its checks run only once it has been
  learned. With Mark 7's firmware a calibration learns it only if it sees the sensor change state, and every restart
  of the press (every connection) forgets it. The KHC primer-learn patch learns it at every calibration
  ([below](#the-khc-primer-orientation-sensor)).
- **Decap sensor** (DecapSense™): plug it in **before** the console connects: the press looks for it only when it
  starts, and every connection restarts it. The press remembers a decap sensor it has seen, so if you unplug one,
  plug it back in or bypass it (otherwise the **Decap sensor dirty** alert stops the press).
- **Powder check** (PowderCheck™) and **Powder Measure** on the Evo and Revo models: bypass them if they are not
  fitted. An unfitted one is likely to stop runs with a **Sensor malfunction** or **Powder check** alert.
- **Powder check on the 650/750 PRO and 1050/1100 PRO and X:** the press tests the optical powder check at every
  connection. If that test fails (not fitted, dirty, or the rod in the beam), it uses the Dillon powder check switch
  (port 7) until the next connection, and with nothing on port 7 nothing is checked and there is no alarm. Connect
  with the press at home and the beam clear, then check: a deliberately empty case must raise a **Powder check**
  alert. On a 1050/1100 the button shows **PORTS 4 + 7**.
- **Powder check on the 650/750 X and 1050/1100 LTE:** not verified for their firmware. Bypass it if it is not
  fitted; if it is, check it with an empty case after connecting.
- **Powder check 2** (the Duals): the analysed firmware does not store this setting, so the switch has no effect.
- **650/750 and 1050/1100:** these presses have no Primer Orientation sensor, and the console shows none. Their Powder
  Measure input is always kept bypassed.

## The KHC Primer Orientation sensor

A KHC (or other replacement) Primer Orientation sensor checks that a case is present and its primer seated at the
priming station, like Mark 7's. Mark 7's firmware uses it only after a calibration that sees it change state, which a
replacement sensor may never do, so it can be silently ignored after every restart. Use it with the **KHC
primer-learn patch** for your press (Evo or Revo): the press then learns the sensor at every CALIBRATE
([Press firmware](firmware.md#the-khc-primer-learn-patch-the-primer-orientation-fix)).

1. With the press console switched off, **fit the sensor in console port 2** (Evo and Revo).
2. Connect and **calibrate with an empty shell plate**.
3. On the Sensors tab, turn **Primer Orientation** to **ACTIVE** (green).
4. **Check it every session:** load a case, pull its primer, and confirm the press stops with the **Primer
   Orientation** alert.

> [!CAUTION]
> - **Never fit it on a 1050/1100.** There port 2 is the swage sensor, and the press would read your sensor as a
>   swage switch.
> - **Without the sensor, keep Primer Orientation bypassed.** With the KHC patch a missing or dead sensor is not
>   skipped: the press stops with an index alarm on every cycle (it fails safe).
> - **Revo:** its index check runs at other points of the stroke than the Evo's, so a sensor set up on an Evo must be
>   tested again on the Revo: dummy rounds with seated primers (no index alarm), then pull a primer (the press must
>   stop).
> - **The KHC patch has not been validated on a press yet.** Use dummy rounds only until you have checked that the
>   press stops when a primer is pulled.

What each alert means: [Alerts](alerts.md).
