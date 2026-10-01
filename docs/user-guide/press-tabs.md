# The press tabs

The press screen shows the tabs of your press model along the top, as Mark 7's app does:

| Press | Tabs |
|---|---|
| Apex 10 Evolution, Revolution, 650 X / 650 PRO, 1050 X / 1050 PRO, and the Evolution PRO, Duals and GAP PRO | **CONTROL**, **MONITORS**, **SENSORS**, **SETUP**, **SETTINGS** |
| 1050 LTE | **CONTROL**, **SENSORS**, **SETTINGS** |
| A press the console does not recognise | **SETTINGS** only (STOP-only mode) |

Before the press is identified (connecting, identifying, restoring its settings) or after a fault, the tabs say why
they are not ready; the Settings tab stays usable.

The status bar at the bottom shows the console version, the press firmware and motor, the port, and on the right the
state: **CONNECTED**, **NOT CALIBRATED** / **CALIBRATING** / **CALIBRATED** / **RUNNING**, the rounds per hour while
running, and the round count.

## Control

![The Evolution's Control tab](../images/screen-press-evolution-control.png)

- **ROUNDS PER HOUR:** the speeds of your press model.
- **DIGITAL CLUTCH:** the torque limit for the stroke (on the 1050 LTE: LOW, MED, HIGH, MAX). A jam above it stops the
  press with the **Jam: Digital Clutch** alert.
- **TorqueSense:** ACTIVE or BYPASSED. It is switched **ACTIVE every time the console connects**.
- **TorqueSense level** (650 instead of the TorqueSense switch): the torque while the shell plate indexes, below the
  clutch; lower is more sensitive (the 650 manual).
- **Index Slowdown** (1050 LTE).
- **JOG UP / JOG DOWN** (models with jog), **CALIBRATE**, and **CLEAR SHELL PLATE** (1050 models). See
  [Calibrating and running](calibrate-and-run.md).
- With a foot pedal set up: **ARM PEDAL** / **DISARM PEDAL** ([Foot pedal](foot-pedal.md)).

Each model's Control tab looks a little different:

| | |
|---|---|
| ![Revolution](../images/screen-press-revolution-control.png) | ![650 PRO](../images/screen-press-650pro-control.png) |
| ![1050 PRO](../images/screen-press-1050pro-control.png) | ![1050 X](../images/screen-press-1050x-control.png) |

## Monitors

![The Monitors tab: rounds made, supplies remaining with stop levels](../images/screen-press-evolution-monitors.png)

- **ROUNDS:** the rounds made, **COUNTING** / **PAUSED**, **RESET**, and **STOP AFTER ROUNDS** (0 = off).
- **SUPPLIES REMAINING:** primers, brass and projectiles left, each with an optional **STOP AT** level. Each round
  made takes one of each. When a supply reaches its stop level, the run ends at the end of that cycle.
- RUN is refused while a supply is already at its stop level: refill and correct the count, or switch that stop off.

Numbers are typed on an on-screen number pad.

## Sensors

![The Sensors tab: Remote Stop and Machine Guard ACTIVE, the other sensors BYPASSED, and notes on the right](../images/screen-press-evolution-sensors.png)

Every sensor your press model has, in Mark 7's order, each **ACTIVE** (green: its checks are on) or **BYPASSED**
(black: the press ignores it). Tap a sensor to switch it. The notes on the right explain the sensors of your model.
See [Sensors and interlocks](sensors-and-interlocks.md).

## Setup

![The Setup tab: dwell and index, slowdown, die setup](../images/screen-press-evolution-setup.png)

- **DWELL AND INDEX:** **TOP DWELL** (with ±10 buttons), **INDEX SPEED**, **BOTTOM DWELL**. On a 650 the bottom
  setting is **Primer depth (0 = deepest)**: it sets how deep primers are seated; change it one step at a time, not
  while cycling, and check the seated primers with SINGLE before you RUN.
- **SLOWDOWN:** **BOTTOM SLOWDOWN** (for big brass; Evolution, Revolution and 1050 models), or **Top Slowdown** on
  the 650.
- **DIE SETUP:** **START DIE SETUP**, the moves, **FINISH DIE SETUP**
  ([Calibrating and running](calibrate-and-run.md#die-setup)).

## Settings

- The connection, the press model and firmware, the motor, and the screen layout in use.
- **RECONNECT:** disconnects and connects again. This restarts the press controller: calibrate again afterwards.
- **CONSOLE PORTS:** which sensor goes into which port ([Console ports](console-ports.md)); not while the press moves.

## STOP-only mode

![STOP-only mode](../images/screen-press-stop-only.png)

If the press reports a firmware type the console does not know, you get only the Settings tab: RUN, END CYCLE and
SINGLE are disabled, and **STOP works**. Use Mark 7's own console for such a press, or report its firmware version as
an [issue](https://github.com/Shane-Cotta/M7-Console/issues/new/choose).
