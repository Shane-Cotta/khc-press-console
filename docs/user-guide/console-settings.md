# Console settings

**CONSOLE SETTINGS** on the home screen holds the settings of the console itself, not of the press: the touch screen,
the screen rotation and the sound. Its bottom row opens **FOOT PEDAL**, **SETTINGS FILE**, **CONSOLE PORTS**,
**WI-FI** and **LICENSE**, and has **SAVE LOGS**.

![Console settings: touch screen, screen rotation and sound, with FOOT PEDAL, SETTINGS FILE, CONSOLE PORTS, WI-FI, LICENSE and SAVE LOGS along the bottom](../images/screen-settings.png)

These settings are kept on the console and survive software updates.

## Touch screen

Fix it here if touches land in the wrong place (for example a tap on the left reacts on the right, or up and down are
swapped). The touch panel's name is shown at the top.

| Setting | Use it when |
|---|---|
| **Swap X and Y** | the panel's axes are turned |
| **Invert X** | left and right are mirrored |
| **Invert Y** | top and bottom are mirrored |

1. Tap one setting. It applies **at once, on trial**: the console asks "Keep this touch setting? It goes back by
   itself in 15 s."
2. If touches now land correctly, tap **KEEP** within 15 seconds. **UNDO** goes back at once.
3. If you cannot tap KEEP (touches are now wrong), wait: the setting goes back by itself.

![A touch setting on trial, with KEEP, UNDO and the 15-second countdown](../images/screen-settings-touch-trial.png)

Touch settings cannot be changed while the press runs or calibrates ("Stop the press to change the touch settings."):
a wrong setting would move STOP to the wrong place.

## Screen rotation

**0°** or **180°** (upside down, for a screen mounted the other way up). It applies the next time the console starts:
tap **TURN OFF** on the home screen, then switch the Pi on again.

## Sound

**Sound** **ON** or **OFF**.

- With sound on, each new alert plays a short tone by its kind, and a **CRITICAL** alert sounds an alarm every few
  seconds until you close it.
- Sound plays through the screen's speaker over HDMI. If the console finds no speaker, the panel says "No speaker
  found: alerts are silent." The alerts still show on the screen.
- Switching sound off silences everything, the CRITICAL alarm included.

## Settings file: export and import

**SETTINGS FILE** saves the console's settings to a file and restores them.

![The SETTINGS FILE screen: SAVE SETTINGS on the left, the settings files found on the console and on USB sticks on the right](../images/screen-settings-file.png)

### Export

1. Tap **SETTINGS FILE**, then **SAVE SETTINGS**.
2. The console saves every press model's settings (sensors, dwell, clutch, index), the Monitors counters and the foot
   pedal's settings to one file, `m7-settings-v1-<date>.json`, and says where it went.

- The file is **kept on the console**, and survives software updates. USB sticks are mounted read-only on the console,
  so the file cannot be written to a stick.
- Writing a new SD card loses the saved files with everything else.
- The speed is not saved: every session starts at the slowest speed.

### Import

1. Plug in a USB stick with a settings file if you have one, then tap **RESCAN**. The list shows the settings files on
   the console and on any USB stick.
2. Tap a file. The console shows **what it would change** first, with every note.
3. Tap **IMPORT**, or **CANCEL**.
4. Connect to the press again with **PRESS**.

![The preview of an import: what the file would change, with IMPORT and CANCEL](../images/screen-settings-file-preview.png)

- Importing **disconnects the press first** (its controller restarts).
- It is refused while the press runs or calibrates, or while a firmware update runs.
- An import can only turn sensors **on**: it **never bypasses a sensor**, never clears DO NOT OPERATE and never arms
  the foot pedal. Remote Stop, Machine Guard and Index torque (TorqueSense™) are switched ACTIVE at the next
  connection anyway.

## Save logs

**SAVE LOGS** saves the console's logs in one file for a bug report: see
[Reporting a problem](troubleshooting.md#reporting-a-problem).

## The other buttons

- **FOOT PEDAL:** [Foot pedal](foot-pedal.md).
- **CONSOLE PORTS:** [Console ports](console-ports.md).
- **WI-FI:** [Software updates and Wi-Fi](software-updates.md).
- **LICENSE:** [The trial and your license](license.md).
