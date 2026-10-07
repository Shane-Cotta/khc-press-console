# Getting started

> [!WARNING]
> **Read [Safety](../../SAFETY.md) first.** KHC Press Console is unofficial BETA software that drives real machinery.
> Keep the press console's power switch within reach: it is the press's only hard stop.

This page wires the console up and walks you through a first session. Write the card first
([Installing](install.md)).

## Wiring

```
 press console                      Raspberry Pi 4 / 5                    touch screen
 ┌───────────────┐   USB-A to       ┌──────────────────┐  micro-HDMI to   ┌──────────────┐
 │ micro-USB  ●──┼── micro-USB ─────┼─● any USB-A port │  HDMI ───────────┼─● HDMI        │
 │               │   data cable     │ ● HDMI0 ─────────┼──────────────────┘              │
 │ USB-A (motor) │  (never to the   │ ● another USB ───┼── touch USB ─────● touch USB   │
 │ only for the  │   Pi or anything │ ● USB-C power    │                  ● own 5 V power│
 │ ClearPath     │   else)          └──────────────────┘                  └──────────────┘
 └───────────────┘
```

1. **The press:** connect a **USB-A to micro-USB data cable** from **any USB-A port of the Pi** to the **micro-USB
   port of the press console** (the port Mark 7's tablet used). Charge-only cables do not work.
2. **The picture:** connect a micro-HDMI to HDMI cable from the Pi's **first HDMI port** (HDMI0, the one next to the
   USB-C power input) to the screen.
3. **The touch:** connect the screen's touch USB cable to any free USB port of the Pi.
4. **Power:** give the screen **its own 5 V supply**, not a USB port of the Pi (the Pi cannot supply enough current
   for it, and a sagging supply makes the Pi unreliable). Give the Pi its own supply.
5. **Optional:** an Ethernet cable (for online updates through a router), a USB foot pedal, a USB stick.

> [!CAUTION]
> **Never plug anything into the press console's USB-A port** except the cable to the ClearPath motor that is already
> there. That port is the press's link to its motor.

- Connect **one press** to a console. A second press adapter on the same Pi is not supported.
- Plug and unplug **sensors** at the press console only with the console switched off
  ([Console ports](console-ports.md)).

## Power-on order

1. Leave the press console switched **off**, or on with the press at rest. KHC Press Console never moves the press by
   itself: nothing is sent until you tap **ACCEPT** or **CONNECT**.
2. Switch on the screen.
3. Plug in the Pi's power. The boot animation plays, then the home screen appears. The very first start takes about a
   minute longer, and shows the terms of use and the welcome screens ([Installing](install.md#first-start)).
4. Switch on the press console if it was off.

## Your first session

Use an **empty shell plate** for your first sessions. Keep your hand near the console's power switch, and go one step
at a time.

1. **Plug in the press and tap CONNECT.** When the console sees the press console's USB cable (plugged in, or already
   plugged in when the console starts), it shows **Press detected**: the USB adapter, the press it last saw, and
   **"Connecting restarts the press controller. Keep hands clear."** Tap **CONNECT**, or **NOT NOW** (it asks again
   the next time you plug the cable in).

   ![The Press detected popup: the USB adapter, the last press seen on it, the keep-hands-clear warning, CONNECT and NOT NOW](../images/screen-press-detected.png)

2. **Or connect from the home screen.** Tap **PRESS**, read the safety text and tap **ACCEPT** (or **DENY** to go
   back).

   ![The accept screen before connecting: "Reloading is dangerous.", with ACCEPT and DENY](../images/screen-accept.png)

3. **Wait for the press to be identified.** Either way, the console connects and restarts the press controller. The
   status bar at the bottom shows the firmware (for example "Firmware: Evo FW 19") and the motor, then **CONNECTED**
   and **NOT CALIBRATED**. The tabs for your press model appear.

You accept **before every connection**: see
[The home screen](home-screen.md#accept-before-every-connection). If the console has no trial or license yet, CONNECT
and PRESS open **LICENSE** instead ([The trial and your license](license.md)).

### Check the interlocks and calibrate

1. **Check the interlocks.** On the **Sensors** tab, **Remote Stop** and **Machine Guard** must be **ACTIVE** (green).
   Turn on the other sensors that are fitted to your press. Close the guard.
2. **Calibrate.** With the shell plate **empty**, tap **CALIBRATE** on the Control tab. The press moves through its
   calibration. When it succeeds, the status bar shows **CALIBRATED** and **RUN** unlocks.
3. **Test STOP.** Tap **SINGLE**, and tap **STOP** while the press moves. It must stop at once. Test the **Remote
   Stop** and opening the **guard** the same way.
4. **Run.** Choose a speed and tap **RUN**. **END CYCLE** stops at the end of the current cycle; **STOP** stops now.
   See [Calibrating and running](calibrate-and-run.md).

![The Control tab of an Evo: speeds, digital clutch, Index torque, JOG and CALIBRATE, with RUN, END CYCLE, SINGLE and STOP in the column on the right](../images/screen-press-evolution-control.png)

> [!CAUTION]
> If the press does not stop at once when you tap STOP, press the Remote Stop or open the guard, **switch off the press
> console's power**, and do not use the console until you have reported it.

### When you are done

1. Stop the press (**STOP** or **END CYCLE**).
2. Tap **MENU** to go back to the home screen.
3. Tap **TURN OFF** before you unplug the Pi ([Turning off](home-screen.md#turning-off)).
4. Switch off the press console.

## What the console remembers

- Your **press settings** (sensors, clutch, dwell, index and the monitors), per press model. They are sent to the
  press every time it connects, because the press itself forgets them at every restart.
- The **speed** always starts at the slowest, and **Remote Stop, Machine Guard and Index torque (TorqueSense™)** always
  start **ACTIVE**.
- The **console settings:** touch calibration, screen rotation, sounds, the foot pedal.
- The **backups of your press's firmware** ([Firmware](firmware.md)).
- The last press model it saw (used for firmware recovery).

All of this lives on the SD card and survives software updates. A newly written card starts from scratch: the
[settings files](console-settings.md) and firmware backups saved on the old card do not carry over.
