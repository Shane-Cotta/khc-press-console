# Foot pedal

A USB foot pedal can start **SINGLE CYCLE**, one cycle per press, so your hands are free to place cases and
projectiles. **It does nothing else, and it is never a stop:** STOP, the remote stop and the console's power switch
are the stops.

> The foot pedal has been tested with the console's simulators, not yet with a real USB pedal on a Raspberry Pi.

## Which pedals work

Any USB foot pedal that acts as a **keyboard** (it "types" a key when pressed) and can be set to a key that keyboards
rarely send. Best: a pedal you can program to **F13 to F24**. Escape, Enter, Space, Tab, Backspace, Delete, the arrows,
and the modifier and lock keys cannot be learned. Plug it into any USB port of the Pi.

The console recognises **the learned pedal itself**, by its USB identity and serial number (or the USB port it is in):
the same key typed on another keyboard does not fire SINGLE CYCLE. A pedal moved to another USB port (or one without a
serial number, replaced by another unit) must be learned again.

## Setting it up

![The foot pedal page: ON/OFF, the learned key, LEARN KEY, the auto-disarm minutes](../images/screen-pedal.png)

1. **CONSOLE SETTINGS → FOOT PEDAL.** Switch **USB foot pedal** **ON** (it is off on a new console).
2. Tap **LEARN KEY** and press the pedal once. The page shows the learned key. **CLEAR** forgets it; **CANCEL LEARN**
   stops learning.
3. Set **Auto-disarm**: the pedal disarms itself after this many minutes without a press (5 to 30).

## Arming it, every session

The pedal works only while it is **armed**, and arming is never remembered: not across connections, restarts or a
settings import.

1. Connect, accept and **CALIBRATE** as usual.
2. On the **Control** tab, tap **ARM PEDAL** (orange).
3. Read the confirmation **"Arm the foot pedal?"** ("Your hands will be free while the press moves. Keep them clear of
   the shell plate and dies: the pedal starts a full stroke. The pedal is not a stop: STOP, the remote stop and the
   console power switch are.") and tap **I UNDERSTAND: ARM**. It is asked once per connection.
4. The status bar shows **PEDAL ARMED** (purple). Each pedal press now starts one SINGLE CYCLE, with the same checks
   as the SINGLE button. **DISARM PEDAL** disarms it.

| | |
|---|---|
| ![The confirmation before arming](../images/screen-press-evolution-pedal-confirm.png) | ![PEDAL ARMED in the status bar, and DISARM PEDAL on the Control tab](../images/screen-press-evolution-pedal-armed.png) |

**Arming is refused** (with the reason) before a calibration, while the Remote Stop or the Machine Guard is bypassed,
while a CRITICAL alert is open, away from the press screen, and on a press without SINGLE (the 1050 LTE).

## When it disarms itself

The pedal disarms on: **any STOP** (at the moment you touch it), any stop alert or CRITICAL alert, **NEUTRAL**, a
connection reset or disconnect, a refused command or a fault, bypassing the Remote Stop or the Machine Guard, losing the
calibration, the touch screen failing, **leaving the press screen**, and the auto-disarm time without a press. Then arm
it again on the Control tab.

A pedal press is ignored while a question is open on the press screen (a bypass confirmation, the number pad). Each
press must be released before the next one counts, holding the pedal down does not repeat, and two presses closer
than about three quarters of a second count once. A refused pedal press shows one **Not now (pedal)** alert with the
reason.
