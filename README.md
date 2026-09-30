# Mark 7 console apps for any Android tablet (standalone)

Mark 7's own console software for its automated reloading presses, repackaged so it installs on an ordinary Android
tablet as normal apps. No root and no Mark 7 installer are needed, and nothing on the tablet is modified.

**Unofficial.** This is not made, endorsed or supported by Mark 7 Reloading. Mark 7's software and names belong to
Mark 7. It is shared as-is, with no warranty, for owners of Mark 7 presses.

> **Safety.** This software drives real machinery. Keep your hands clear of the press whenever it can move, keep the
> console's power switch within reach, and switch the console off if the press does not stop. Behaviour is Mark 7's own;
> only the USB connection code was changed (below). It has been tested in an emulator against a simulated press; test it
> carefully on your own press before relying on it.

## What is in the release

| File | What it is |
|---|---|
| `mark7-crashreporter-standalone.apk` | Mark 7's crash reporter (unchanged, re-signed) |
| `mark7-launcher-standalone.apk` | Mark 7's launcher and its USB service: **the only app that was changed** (see below) |
| `mark7-reloader-standalone.apk` | Mark 7's reloader: the press control app (unchanged, re-signed) |
| `mark7-firmup-standalone.apk` | Mark 7's firmware updater (unchanged, re-signed) |
| `SHA256SUMS.txt` | checksums of the four files |

All four are signed with the same key (certificate SHA-256
`a057c4077d0e5dd5ae009c96adc704a6a79c9e333413f2c645e0fed070b11c59`). Android only installs an update over a copy
signed with the same key, so uninstall any other copy of these apps first (for example one taken from a Mark 7
tablet).

Check a download on a computer: `shasum -a 256 -c SHA256SUMS.txt` (macOS/Linux) or `Get-FileHash` (Windows).

## What was changed, and why

On Mark 7's own tablet, the apps are installed into the system by an installer that roots the tablet, and the launcher
grants itself USB access through a system-only call. On a normal tablet that call is not allowed, so the console's
port never opens. In this build the launcher asks for USB access the normal Android way instead ("Allow
M7Launcher to access …?"), and it also gets an app-drawer icon. Features that need root (installing apps through
SOFTWARE UPDATE, "Turn off tablet") show a message instead of failing silently. Nothing else changed: the press
commands, sensors, STOP and every screen are Mark 7's.

## Install

You need a tablet with USB host support (most have it; you will usually need a USB OTG adapter for the console's
micro-USB cable).

### From a computer with adb (works on every Android version)

Enable Developer options and USB debugging on the tablet, connect it, then install **in this order**:

```sh
adb install -r -g mark7-crashreporter-standalone.apk
adb install -r -g mark7-launcher-standalone.apk
adb install -r -g mark7-reloader-standalone.apk
adb install -r -g mark7-firmup-standalone.apk
```

- **Android 14 and later:** add `--bypass-low-target-sdk-block` to the crashreporter, launcher and firmup lines
  (these apps were built for old Android versions, which Android 14+ otherwise refuses). On Android 14+ they cannot be
  installed from a file manager.
- The crash reporter must be installed first: the other apps open it when something goes wrong.

### From the tablet (Android 13 and earlier)

Copy the four files to the tablet and open them in a file manager, in the order above. Allow "Install unknown apps"
for the file manager when asked; if Play Protect warns, choose "Install anyway". On first start Android may say an app
"was built for an older version of Android": tap OK. Leave the Storage permission on (the firmware updater needs it).

## First connection

1. Open **M7Launcher** from the app drawer. (It can also be chosen as the Home screen, but it does not have to be.
   If Android asks which Home app to use, you can keep the tablet's own.)
2. Plug in the console. Android asks **"Allow M7Launcher to access …?"** or **"Open M7Launcher to handle …?"**.
   Tick **Always open** / **Use by default** where offered, and tap **OK**.
3. **Answer that question before tapping LOADER.** If you tap LOADER first, the reloader gives up at once and shows
   "Close App"; close it and open it again.
4. Tap **LOADER**. From here on it is Mark 7's app.

If you tapped Cancel, unplug and replug the cable to be asked again.

## Firmware updates

FIRMWARE UPDATE works as on Mark 7's tablet: put the firmware file `___Mark7_mot.hex` in the root of the tablet's
storage or of an SD card. Do not plug or unplug any other USB device while a firmware update runs.

## Things to know

- **Do not plug other USB devices in while the press runs.** Mark 7's code re-opens the console connection whenever a
  USB-serial device is attached, and re-opening it resets the press controller. With a USB hub, plug nothing else in
  mid-cycle.
- **SOFTWARE UPDATE** (installing apps) and **Turn off tablet** need root, so on a normal tablet they only show a
  message. Use the tablet's power button to turn it off.
- **One console app at a time.** Another app that talks to the press over USB cannot use the console while this
  launcher is installed and enabled. To switch, disable it (`adb shell pm disable-user com.mark7reloading.M7Launcher`;
  `pm enable` brings it back) or uninstall it.
- **Never install Mark 7's own tablet installer** ("systemupdate") on your tablet: it roots the tablet and rewrites
  system files.

## Uninstall

Uninstall the four apps from Android's app settings, or:

```sh
adb uninstall com.mark7reloading.firmup
adb uninstall com.mark7reloading.automaticreloader
adb uninstall com.mark7reloading.M7Launcher
adb uninstall com.mark7reloading.crashreporter
```
