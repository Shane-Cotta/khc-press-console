# Alerts

Everything the press reports, and every problem the console sees, becomes an alert. Alerts start after you tap
ACCEPT. The newest is shown first; CRITICAL alerts always come first, then the press's own stops, then the rest. An
alert never covers the RUN / END CYCLE / SINGLE / STOP column, except a CRITICAL one, which leaves STOP uncovered.

With sounds on, each new alert plays a short sound by its kind, and a CRITICAL alert sounds an alarm every few seconds
until it is closed ([Console settings](console-settings.md#sound)).

## Kinds of alert

| Kind | Looks like | Examples | What to do |
|---|---|---|---|
| **Information** | a dialog | Run ended, Stopping at end of cycle, Not now (a refused tap, with the reason) | Read it, tap OK |
| **Warning** | a dialog | Calibration failed, Refused by the press, Primers low, Connection reset, Neutral | Read it, fix the cause, tap OK |
| **Stop** | a dialog | Stopped, Jam: Digital Clutch, TorqueSense, Machine Guard open, Remote Stop, DecapSense, SwageSense, BulletSense, Primer Orientation, Index, Powder check | The press has stopped. Make it safe, clear the cause, check for a double charge where the alert says so |
| **CRITICAL** | full screen, red | STOP NOT CONFIRMED, PRESS NOT ANSWERING, PRESS KEPT MOVING, TOUCHSCREEN NOT WORKING | **Switch off the console power now** |

![A stop alert over the press screen, with NEUTRAL and OK](../images/screen-alert-stop.png)

Stop alerts offer:

- **NEUTRAL:** switches the motor off so the press can be moved by hand (RUN then needs a new calibration);
- **CLEAR CASE** (SwageSense): raises the tool head to release the case. It moves the press, even with the guard open;
- **OK:** closes the alert.

After a **Jam**, **TorqueSense** or **SwageSense** stop, the alert says what to check for a **double charge** on your
press (for example station 5 on an Apex 10 Evolution). Do it before you continue.

## CRITICAL alerts

![PRESS NOT ANSWERING: a full-screen red alert ending "Switch off the console power now", with STOP and CONSOLE IS OFF](../images/screen-alert-critical.png)

A CRITICAL alert means the console cannot be sure the press is under control. Every CRITICAL alert ends with
**"Switch off the console power now."** **Do it**, then tap **CONSOLE IS OFF** to close the alert. STOP stays
tappable on it.

| Alert | What happened |
|---|---|
| **STOP NOT CONFIRMED** | The press did not confirm a STOP within about a second. The console reset the press controller through the USB cable. |
| **PRESS NOT ANSWERING** | The press did not answer RUN, SINGLE CYCLE or END CYCLE within about a second. With its motor fault line held, the press can step the motor without answering anything, not even STOP or the Remote Stop. The console reset the press controller. |
| **PRESS KEPT MOVING** | The press moved after it reported a stop. The console sent STOP, and resets the controller if that STOP is not confirmed. |
| **TOUCHSCREEN NOT WORKING** | The touch screen stopped responding: STOP on the screen cannot work. Use the remote stop, or switch off the console power if the press is moving. This alert closes with OK, and by itself when the touch screen is back. |

**Why switch the power off?** The Mark 7 press console has **no separate emergency-stop button**. Its power switch is
the only hard stop. The console's controller reset normally stops the motor, but when the press has stopped answering,
only the power switch is certain. Switch it off, wait, and check the press before you switch it on again and
reconnect.

## Not now

If you tap something the press cannot do at that moment (RUN before calibrating, CALIBRATE while running, a setting
while the press calibrates), the console shows **Not now** with the reason, and sends nothing. A move that had to wait
more than a second behind something slow is also dropped with Not now, rather than moving the press late.
