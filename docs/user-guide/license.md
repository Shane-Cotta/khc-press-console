# The trial and your license

KHC Press Console is an evaluation release. A new card runs as a **10-day trial**. A **license number** activates the
Raspberry Pi for good, and from then on it works without Wi-Fi. You can type the number on the console, or **enter it on
your phone** by scanning the code the console shows.

**STOP always works,** whatever the license says. Without a valid trial or license the console only refuses to
**connect** to a press or to **start a firmware flash**. It never interrupts a press that is already connected and
running. A press left **DO NOT OPERATE** by a failed flash can always be flashed again. It stays disconnected
afterwards until the console has a trial or a license.

## The first start

After the card's first start the console asks two things:

1. **Wi-Fi.** Set up Wi-Fi now, or tap **SKIP**. Wi-Fi is needed only to activate a license.
2. **Checking for a license.** If this Raspberry Pi was licensed before (you wrote a new card for it), the console
   finds its license by itself once it is online and says **License restored**. There is nothing else to do.
3. **License or trial.**

![The first-start choice: ENTER LICENSE or START 10-DAY TRIAL](../images/screen-first-run.png)

- **ENTER LICENSE** activates this Raspberry Pi into one seat of your license. It needs the internet once.
- **ACTIVATE WITH YOUR PHONE** shows a code to scan: see "Activating with your phone" below.
- **START 10-DAY TRIAL** starts the trial at once, with or without Wi-Fi. No license number is needed.
- **LATER** goes to the home screen. Both choices stay on **CONSOLE SETTINGS**, **LICENSE**, and the press cannot
  be connected until you pick one.

## The trial

The trial runs for **10 days**. The home screen shows the days left, and so does the **LICENSE** page.

![The LICENSE page during the trial](../images/screen-license-trial.png)

- With Wi-Fi at any time, the console counts calendar days. Without Wi-Fi it counts the time it has been switched on,
  because the Raspberry Pi has no battery clock. Setting the clock does not extend the trial.
- When the trial ends, the press can no longer be connected. Enter a license number to carry on. Writing a new card
  also starts a new trial.

## Activating a license

1. Connect Wi-Fi (**CONSOLE SETTINGS**, **WI-FI**).
2. Open **CONSOLE SETTINGS**, **LICENSE**, and tap **ENTER LICENSE**.
3. Type the license number, for example `M7-XXXXX-XXXXX-XXXXX-XXXXX`. The dashes are added for you, and the last
   symbol is a check: a mistyped number is caught before anything is sent.
4. Tap **ACTIVATE**.

![Typing a license number](../images/screen-license-entry.png)

When it succeeds, the **LICENSE** page shows **Licensed** and the license's last four symbols. The console now works **offline for
good**. While Wi-Fi happens to be connected it checks in with the license service, so a seat released by the
license's owner takes effect then.

**The license number is never stored on the console** and never appears in its logs or in **SAVE LOGS**.

## Activating with your phone

No typing on the console, and the console does not need Wi-Fi of its own: your phone can share its internet.

![The LICENSE page with the code to scan](../images/screen-license-phone.png)

1. Open **CONSOLE SETTINGS**, **LICENSE** (or the first-start screen). It shows **ACTIVATE WITH YOUR PHONE** and a
   square code.
2. Scan the code with your phone's camera. A page opens: type your license number there and tap **ACTIVATE**. The
   page says **Ready**.
3. Connect the console to the internet **once, within 24 hours**: tap **WI-FI** and pick your shop's Wi-Fi, or use
   your phone's hotspot (below).
4. The console activates by itself, usually within a minute, and shows **Licensed**. From then on it works offline.

**No camera on your phone?** Type the number on the console instead (**ENTER LICENSE**).

### Using your phone's hotspot

If the shop has no Wi-Fi, let the console use your phone's internet for a minute:

- **iPhone:** Settings, **Personal Hotspot**, turn on **Allow Others to Join**. Note the Wi-Fi password shown there.
- **Android:** Settings, **Network** (or **Connections**), **Hotspot**, turn it on. Note its name and password.

Then on the console tap **WI-FI**, pick your phone's hotspot and type its password. Once the console says
**Licensed** you can turn the hotspot off. (Connecting the phone by USB cable is not supported.)

## A new SD card in a licensed console

If you write a new card for a Raspberry Pi that was already licensed, you do not need the license number. Once the
console is online (Wi-Fi or your phone's hotspot) it gets its license back by itself and says **License restored**.
This works with cards written from version 0.3.0b3 on.

![The license restored after Wi-Fi](../images/screen-first-run-restored.png)

### What the messages mean

| Message | What to do |
|---|---|
| Connect to Wi-Fi first. | Set up Wi-Fi, then try again. |
| That is not a valid license number. | Check the number and type it again. |
| License number not recognized. | Check the number with whoever gave it to you. |
| All seats on this license are in use. | Release a seat on another console, or ask for more seats. |
| This license has been revoked. | Contact whoever gave you the license. |
| This console's license could not be restored. Enter your license number. | Type the license number on the console (ENTER LICENSE). |
| The license server is busy. | Try again in a few minutes. |

## Seats: one license, several consoles

A license has one or more **seats**. Each seat belongs to **one Raspberry Pi**: to the Pi itself, not to the SD card.

- **A new card in the same Pi** gets that Pi's own seat back: by itself once online (cards from 0.3.0b3 on), or when
  you enter the number again. It does not use a second seat.
- **The card moved to a different Pi** counts as a new console. It needs a free seat.
- **Moving a seat to another Pi:** on the old console, with Wi-Fi, open **CONSOLE SETTINGS**, **LICENSE**, tap
  **RELEASE SEAT** and confirm. Then enter the number on the new console. After a release the old console no longer
  connects to a press, and its trial does not come back.
- **A console that is broken or lost** cannot release its seat. Ask whoever gave you the license to free it.

![Releasing a seat asks first](../images/screen-license-release-confirm.png)
