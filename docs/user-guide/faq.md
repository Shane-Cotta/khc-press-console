# FAQ

### Is KHC Press Console made by Mark 7?

No. It is made by KHC Precision, an independent maker, and is **not made, endorsed or supported by Mark 7
Reloading**. Ask questions here, not Mark 7. Its controls use the same press functions, so an experienced
operator will find them straightforward; see the [trademark note](../../README.md#trademarks).

### Is it safe to use?

It is a **BETA** for real machinery, and it has **not yet been run on a real press**. It was built with safety first
(STOP on every screen, CRITICAL alerts with the controller reset, RUN only after calibration, interlocks active at every
connection), and tested against simulators that include Mark 7's real firmware. Treat every session as a test, and
read [Safety](../../SAFETY.md).

### Do I have to change my press firmware?

No. KHC Press Console works with the firmware your press shipped with. The KHC primer-learn patch is optional
([Firmware](firmware.md)).

### Can I go back to Mark 7's tablet?

Yes. KHC Press Console changes nothing on the press except when you flash firmware yourself. Unplug the Pi and plug Mark 7's
tablet back into the press console's micro-USB port. (If you flashed the KHC patch, Mark 7's app shows its version, one
higher than Mark 7's; flash Mark 7's original back first if you prefer.)

### Does it work on Mark 7's own tablet, or on a Raspberry Pi 3?

Not in this BETA. It runs on a Raspberry Pi 4 or 5 with a 10.1-inch 1920x1200 HDMI touch screen.

### Does it need the internet?

No. The press never needs a network. Wi-Fi or Ethernet is used only to check for and download updates, and the
console app itself has no network access. Without a network, update from a USB stick.

### Why do I have to tap ACCEPT (or CONNECT) every time?

So that nothing reaches the press until a person has decided to connect, and to remind everyone that connecting
restarts the press controller. Mark 7's app works the same way. When you plug the press in, the **Press detected**
question is that step: tap CONNECT.

### Why must I calibrate after every connection?

Connecting restarts the press controller, and the press keeps its calibration only in memory. RUN stays locked until
it has calibrated again. Use an empty shell plate.

### Why did my Remote Stop / guard bypass come back on?

On purpose: Remote Stop, the Machine Guard and Index torque (TorqueSense™) are switched ACTIVE at every connection, so a bypass never
carries over by mistake ([Sensors and interlocks](sensors-and-interlocks.md)).

### The screen told me to switch off the console power. Was that necessary?

Yes. A CRITICAL alert means the console could not confirm that the press stopped or is answering. The console's power
switch is the only hard stop the press has ([Alerts](alerts.md#critical-alerts)).

### Can the console update itself without asking?

No. It checks for updates and installs them only when you tap the buttons, and never while the press is busy.

### Can I go back to an older version?

Yes, as long as it is not below the safety minimum: SOFTWARE UPDATE lists older versions with INSTALL or SWITCH TO
([Software updates](software-updates.md)).

### Are my settings kept when I update?

Yes, a software update keeps them. Writing a new SD card does not.

### Can I copy my settings to another console?

Not easily in this BETA: the settings file is saved on the console's card, because the console never writes to USB
sticks. A settings file on a USB stick can be imported.

### A number pad titled "Technician: debug and demo mode" appeared.

That is the way into the technicians' menu (a read-only diagnostic view, and a demo mode that simulates a press). Tap
**CANCEL**, or wait a minute and it closes by itself. It changes nothing on the press, and STOP keeps working.

### A banner says "DEMO — NO PRESS CONNECTED".

A technician turned on demo mode: the console is simulating a press, and nothing it shows comes from your press.
Restarting the console turns it off (it is always off at start), or ask the technician to turn it off.

### Can I use Raspberry Pi Imager's settings (user, Wi-Fi, SSH)?

No: answer **No** to OS customisation. Set up Wi-Fi on the console's own Wi-Fi screen instead
([Installing](install.md#os-customisation-answer-no)). The card has no user account and no SSH server: there is
nothing to log in to.

### Is the source code available?

Not in this repository. See the [Terms of use](../../TERMS.md).
