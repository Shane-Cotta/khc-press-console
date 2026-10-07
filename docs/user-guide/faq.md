# FAQ

Short answers. The guide has the details: [user guide](README.md).

### Is KHC Press Console made by Mark 7?

No. It is made by KHC Precision, an independent maker, and is **not made, endorsed or supported by Mark 7
Reloading**. Ask us, not Mark 7. See the trademark note in the [README](../../README.md).

### Which presses does it support?

The Evo (Mark 7 Apex 10 Evolution), the Revo (Revolution), the Evo PRO, the Evo Dual, the Revo Dual, the GAP PRO, and
Mark 7's drives for the Dillon 650/750 (PRO, X) and 1050/1100 (PRO, X, LTE). What each one has:
[The press tabs](press-tabs.md).

### Is it safe to use?

It is a **BETA** for real machinery. It was built with safety first (STOP on every screen, CRITICAL alerts with a
controller reset, RUN only after calibration, interlocks active at every connection) and tested mostly against press
simulators, including Mark 7's real firmware, and used on a real Apex 10 Evolution and a real Revolution. Nothing is
validated yet: the KHC primer-learn patch is still under test, and the 650/750 and 1050/1100 have not been run with
it at all. Treat every session as a test, and read [Safety](../../SAFETY.md).

### Do I have to change my press firmware?

No. It works with the firmware your press shipped with. The KHC primer-learn patch is optional
([Press firmware](firmware.md)).

### Can I go back to Mark 7's tablet?

Yes. KHC Press Console changes nothing on the press unless you flash firmware yourself. Plug Mark 7's tablet back into
the press console's micro-USB port. If you applied the KHC patch, Mark 7's app shows its version (one higher than
Mark 7's); restore your backup first if you prefer ([Restoring a backup](firmware.md#restoring-a-backup)).

### Does it run on Mark 7's own tablet, or on a Raspberry Pi 3?

Not in this BETA. It runs on a Raspberry Pi 4 or 5 with a 10.1-inch 1920x1200 HDMI touch screen
([Installing](install.md)).

### Does it need the internet?

The press never needs a network. The console uses the internet only to activate a license, check for and download
updates, and send a diagnostic report. A trial or an activated license works offline, and updates can come from a USB
stick ([The trial and your license](license.md), [Software updates and Wi-Fi](software-updates.md)).

### Why do I have to tap ACCEPT (or CONNECT) every time?

So that nothing reaches the press until a person has decided to connect, and to remind everyone that connecting
restarts the press controller ([The home screen](home-screen.md)).

### Why must I calibrate after every connection?

Connecting restarts the press controller, and the press keeps its calibration only in memory. RUN stays locked until
it has calibrated again, with an empty shell plate ([CALIBRATE](calibrate-and-run.md#calibrate)).

### Why did my Remote Stop or guard bypass come back on?

On purpose: Remote Stop, the Machine Guard and Index torque are switched ACTIVE at every connection, so a bypass never
carries over by mistake ([Sensors and interlocks](sensors-and-interlocks.md)).

### The screen told me to switch off the console power. Was that necessary?

Yes. A CRITICAL alert means the console could not confirm that the press stopped or is answering. The press console's
power switch is the only hard stop the press has ([CRITICAL alerts](alerts.md#critical-alerts)).

### Can the console update itself without asking?

No. It looks for new versions by itself (about once a day while online, and never during a press session) and shows
**UPDATE AVAILABLE** on the home screen, but it installs only when you tap **INSTALL**
([Software updates and Wi-Fi](software-updates.md)).

### Are my settings kept when I update?

Yes, a software update keeps them. Writing a new SD card does not: save them first with **SETTINGS FILE**
([Console settings](console-settings.md#settings-file-export-and-import)).

### Can I copy my settings to another console?

Not easily in this BETA: the settings file is saved on the console's card, because the console never writes to USB
sticks. A settings file on a USB stick can be imported.

### Does the foot pedal stop the press?

No. It only starts SINGLE CYCLE. STOP, the remote stop and the power switch are the stops ([Foot pedal](foot-pedal.md)).

### A number pad titled "Technician: debug and demo mode" appeared.

Tap **CANCEL**, or wait a minute and it closes by itself. It changes nothing on the press, and STOP keeps working.

### A DEMO banner says no press is connected.

The banner reads **DEMO — NO PRESS CONNECTED**. A technician turned on demo mode: the console is simulating a press, and nothing it shows comes from your press.
Restarting the console turns it off, or ask the technician to.

### Can I use Raspberry Pi Imager's settings (user, Wi-Fi, SSH)?

No: answer **No** to OS customisation, and set up Wi-Fi on the console's own Wi-Fi screen instead
([Installing](install.md)).

### Is the source code available?

No. See the [Terms of use](../../TERMS.md).

### How do I get help?

See [Reporting a problem](troubleshooting.md#reporting-a-problem).
