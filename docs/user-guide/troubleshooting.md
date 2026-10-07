# Troubleshooting

> [!WARNING]
> **If the press is moving and anything is not as you expect, switch off the press console's power first.** Then read
> on. Pulling the Raspberry Pi's plug does not stop the press.

Find your symptom below. If nothing here helps, [ask for help](#reporting-a-problem).

## Connecting to the press

The home screen's status line stays at **Press not connected** or **Connecting to the press…**, or the press screen
shows an error and **CONNECT**.

| Symptom | Likely cause | What to do |
|---|---|---|
| Nothing happens when you plug the press in | The press console is off, or the cable is in the wrong port | Switch the press console on. The cable goes from the press console's **micro-USB port** to a **USB-A port of the Pi**, never into the press console's USB-A port (that is the motor's). |
| Still no connection with the right ports | A charge-only cable | Use a **data** cable. Many micro-USB cables sold with chargers carry power only. Try another cable. |
| A notice says the console cannot choose the press port | Several USB-serial adapters are plugged in | Unplug the other adapters: connect **one press** only. Try another USB port of the Pi. |
| You tapped **NOT NOW** on the **Press detected** question | Nothing is wrong | Tap **PRESS** on the home screen, then **ACCEPT**. |
| **Connection reset** keeps coming back | A bad cable or a weak power supply | Change the cable; check the Pi's power supply. Calibrate again after each reconnection. |
| **Identifying the press…** never ends, or a fault shows in the status line | The press controller is stuck | Switch the press console off and on, then connect again. For a motor USB or oscillator fault, check the ClearPath motor's USB cable and see your press manual. |
| PRESS opens the terms of use or the LICENSE screen | The terms are not accepted yet, or there is no trial or license | Accept the terms; start the trial or activate a license ([The trial and your license](license.md)). |
| Only the **Settings** tab, and RUN dimmed | The press runs firmware the console does not recognise | See [STOP-only mode](press-tabs.md#stop-only-mode). |
| **DO NOT OPERATE THE PRESS** instead of the home screen | A flash was interrupted | See [DO NOT OPERATE](firmware.md#do-not-operate). |

## Running the press

| Symptom | Likely cause | What to do |
|---|---|---|
| RUN and SINGLE are dimmed | No successful calibration in this connection, or after NEUTRAL | Clear the shell plate and tap **CALIBRATE** ([CALIBRATE](calibrate-and-run.md#calibrate)). |
| **Calibration failed** | The guard is open, the press is busy, or something blocks it | Close the guard, clear the press, and calibrate again. |
| **Not now** when you tap a button | The press cannot do it at that moment | Read the reason in the alert ([Not now](alerts.md#not-now)). |
| **Refused by the press** | The press is busy, not at home, or the guard is open | Wait for the press to finish, or close the guard. |
| Every run stops with a sensor alert | A sensor is ACTIVE but not fitted, dirty or unplugged | Bypass sensors that are not fitted; clean or reconnect the others ([Sensors and interlocks](sensors-and-interlocks.md)). |
| **Decap sensor dirty** | The beam is blocked, or the sensor was unplugged | Clean it with compressed air; plug it back in or bypass it. |
| **Sensor malfunction** | A powder-check sensor is obstructed or not fitted | Clean it, or bypass it if it is not fitted. |
| Primer Orientation never stops the press | With Mark 7's firmware, a replacement sensor may never be learned | See [The KHC Primer Orientation sensor](sensors-and-interlocks.md#the-khc-primer-orientation-sensor). |
| An index alarm on every cycle with the KHC patch | Primer Orientation is ACTIVE with no working sensor | Fit and check the sensor, or bypass Primer Orientation. |
| The Remote Stop or guard bypass came back on | On purpose: both are switched ACTIVE at every connection | Nothing to fix. |
| A CRITICAL alert (red, full screen) | The console cannot be sure the press is under control | **Switch off the press console's power**, then tap **CONSOLE IS OFF** ([CRITICAL alerts](alerts.md#critical-alerts)). |

## Touches land in the wrong place

| Symptom | What to do |
|---|---|
| A tap reacts somewhere else | **CONSOLE SETTINGS → Touch screen**: **Swap X and Y**, **Invert X**, **Invert Y**. Each change is on trial for 15 seconds: tap **KEEP** if it is right; if it is wrong, wait and it goes back by itself ([Touch screen](console-settings.md#touch-screen)). |
| Nothing reacts to touch | Check the touch USB cable from the screen to the Pi. The console shows **TOUCHSCREEN NOT WORKING** (CRITICAL): STOP on the screen cannot work then; use the remote stop or the press console's power switch. |
| The picture is upside down | **CONSOLE SETTINGS → Screen rotation → 180°**, then **TURN OFF** and switch on again. |

## No picture on the screen

| Symptom | What to do |
|---|---|
| Black screen | The HDMI cable must be in the Pi's **first HDMI port** (HDMI0, next to the USB-C power input). Power the screen from **its own 5 V supply**, and switch it on **before** the Pi. |
| A red light only on the Pi, or a Pi that restarts by itself | Too little power: use a proper Raspberry Pi power supply. |
| The picture comes only sometimes after a cold start | A technician can make the console remember the screen's identification: see `PRESS-CONSOLE.txt` on the card's boot partition ("If the screen or sound misbehaves"). |
| Not even the boot animation appears | The card may be badly written: write it again and let Imager verify it, or try another card ([Installing](install.md)). |

The console drives the screen at 1920x1200. Screens of another resolution are not supported in this BETA.

## The screen says "the console app has stopped"

The console app failed to start several times in a row and stopped trying.

> [!CAUTION]
> **The press is not controlled from this screen.** Switch the press console off before you touch the press.

1. Restart the Pi (unplug it and plug it in again).
2. If it happens again, write the card again ([Installing](install.md)).
3. [Report it](https://github.com/Shane-Cotta/khc-press-console/issues/new/choose) with a photo of the screen.

## No sound

| Cause | What to do |
|---|---|
| The screen has no speaker, or its volume is down | Sound comes through the screen's own speaker over HDMI. Turn the screen's volume up. |
| Sound is off | **CONSOLE SETTINGS → Sound** must be **ON**. If the panel says "No speaker found: alerts are silent.", the console found no sound device. |
| The screen was not identified at start-up | The same `PRESS-CONSOLE.txt` note as for the picture applies. |

The first fraction of a second of a sound can be lost while the screen's audio wakes up. Sounds are an extra: every
alert also shows on the screen.

## Wi-Fi and updates

| Symptom | What to do |
|---|---|
| The Wi-Fi list is empty, or Wi-Fi is off | Choose your **country** first (Wi-Fi stays off until it is set), then **SCAN**. |
| Your network is not listed | It may be hidden (**HIDDEN NETWORK…**), out of range, or on a 5 GHz channel not allowed in the country you chose. |
| It does not connect | Check the password (**SHOW** shows what you typed). WPA Enterprise and WEP networks are not supported. |
| CHECK FOR UPDATES fails while Wi-Fi is connected | The network may need a sign-in page (hotel or guest Wi-Fi), which the console cannot open, or it has no internet. The console also needs the correct time from the internet. |
| No network at all | Use Ethernet to a router, or update from a USB stick. |
| An update went back to the previous version by itself | The new version did not start properly. The press is fine; please report it with both version numbers. |

Details: [Software updates and Wi-Fi](software-updates.md).

## Reporting a problem

Open an [issue](https://github.com/Shane-Cotta/khc-press-console/issues/new/choose) and choose the **Bug report**
form. KHC Press Console is not made or supported by Mark 7 Reloading: please do not contact Mark 7 about it.

Include:

- the console version (bottom right of every screen, or **ABOUT**);
- the press model and firmware as the console shows them (the status bar on the press screen);
- what you did, what happened, and **the exact text of any alert** (a photo of the screen is best);
- whether the press stopped when it should have. **If it did not, say so in the first line**, and do not use KHC Press
  Console again until the problem is understood;
- the name of the logs file, if you saved one (below), or the ticket number of a diagnostic report.

### Save logs

The console keeps a detailed log of every session on the card, including a record of the last moments before each
CRITICAL alert. **SAVE LOGS** puts it into one file, with the console's version, the press model and firmware, and the
recent alerts.

1. Tap **CONSOLE SETTINGS → SAVE LOGS** at any time, or **SAVE LOGS** on the **Save the logs?** question the console
   asks after you close a CRITICAL alert with **CONSOLE IS OFF**.
2. Wait a few seconds (the button shows **SAVING…**). The console and STOP keep working meanwhile. It is not possible
   while a firmware update runs.
3. The **Logs saved** alert shows the file's name and where it was saved. Give that name in your bug report.

![Logs saved: the alert with the file's name and where it was saved on the console](../images/screen-alert-logs-saved.png)

- The file is **kept on the console**. USB sticks are mounted read-only on the console, so it cannot be written to a
  stick (the alert says so). The console keeps the five newest.
- If the file is needed, the issue will say how to get it off the card (it needs a computer that can read the card's
  Linux partition, so usually a technician's help).
- The file holds **no Wi-Fi password** and no other secret: the console leaves out its Wi-Fi settings and blanks
  anything in the logs that looks like a password.

### Send a diagnostic report

When the console is connected to the internet (Wi-Fi or Ethernet), a technician can send a report straight from it,
with its logs. They open **DIAGNOSTIC UPLOAD**, type a short description of what happened (and, if you like, your
company and first name), and tap **SEND**. STOP and the run column keep working meanwhile.

> [!IMPORTANT]
> **The description and the diagnostic summary are published on GitHub as a public issue.** The summary holds the
> versions, the press model and firmware, the license state (never a license number), recent errors and alert
> titles. **Your company, your first name, the console's device identity and the logs bundle are never published.**
> The console says so on the form before you send. Do not type names, license numbers, Wi-Fi names or passwords into
> the description.

- The logs go with the report privately: only KHC reads them. They hold no Wi-Fi password or network name, no license
  number and no other secret, and errors keep only where they happened, never their messages.
- When it is done, the console shows the ticket number, for example **Ticket KHC-20261002-7F3K sent: GitHub issue
  #42.** On a console without a license it shows **Received (ticket …). We'll review it.**: KHC reads it first and
  then publishes it. Give the ticket number if you write to us about it.
- A console can send a few reports a day. If it says it is not connected to the internet, connect it (**CONSOLE
  SETTINGS → WI-FI**) and tap **TRY AGAIN**.

## For technicians

Operators never need these.

- **`PRESS-CONSOLE.txt`** on the card's boot partition (readable from any computer) describes the card: what runs at
  start-up and the screen and sound settings.
- The console has a **read-only diagnostic view** for support sessions. A technician opens it; it never sends anything
  to the press.
- If a number pad titled **Technician: debug and demo mode** appears by accident, tap **CANCEL** (or wait a minute: it
  closes by itself). It changes nothing on the press, and STOP keeps working while it is open.
- If a **DEMO — NO PRESS CONNECTED** banner shows, the console is simulating a press: nothing on the screen comes from
  your press. Restarting the console turns it off.
