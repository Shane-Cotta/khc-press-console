# Release notes template

Copy the block below into the GitHub release's description. Replace every `X.Y.Z` and fill in or delete each
bracketed part. Keep it for operators: what changed for them, what to watch for, how to update. The console's
SOFTWARE UPDATE screen shows a plain-text version of the notes (at most 4000 characters), with its first line in the
version list: start with one short, plain sentence.

---

```markdown
## KHC Press Console X.Y.Z (BETA)

[One or two sentences: what this release is about.]

> KHC Press Console is unofficial BETA software for real machinery, not made or supported by Mark 7 Reloading.
> Keep the press console's power switch within reach. Read SAFETY.md before use.

### Safety

[Delete this section if the release has no safety change.]
- **Safety fix:** [what was wrong, which versions had it, what to do: "Install this version before your next session."]
- Safety minimum: [unchanged | raised to X.Y.Z: older versions can no longer be installed]

### What's new

- [A change the operator will see, in their words.]
- [...]

### Fixed

- [A bug, as the operator saw it.]

### Press firmware

- [No change to the firmware builds. | New or changed KHC build: its name ("KHC primer-learn patch for Evo (from Mark 7 FW 19)"), which press,
  what it changes, whether it has run on a press. For the Primer Orientation fix: calibrate after every connect with
  an empty shell plate; the sensor goes in console port 2, never on a 1050/1100; re-test a sensor on a Revo.]

### Tested

- Simulators: [press models / firmware builds run in the press simulators]
- Real hardware: [Raspberry Pi 4 / Pi 5, screen, press model and firmware, what was run — or "not yet run on real
  hardware"]

### Known issues

- [Anything an operator should know before updating.]

### How to update

- **Consoles with online updates:** SOFTWARE UPDATE → CHECK FOR UPDATES → X.Y.Z → INSTALL.
- **Without a network:** copy `khc-press-console-X.Y.Z.bundle.tar.xz` to a USB stick, then SOFTWARE UPDATE → USB STICK.
- **New console, or a first-BETA console:** write `khc-press-console-X.Y.Z-rpi.img.xz` to the SD card with Raspberry Pi
  Imager (answer **No** to OS customisation). This erases the card's settings.

Check downloads against `SHA256SUMS.txt`.

### Files

| File | For |
|---|---|
| `khc-press-console-X.Y.Z-rpi.img.xz` | the SD card image (Raspberry Pi 4 and 5) |
| `khc-press-console-X.Y.Z-rpi.img.xz.sha256`, `SHA256SUMS.txt` | checksums |
| `khc-press-console-X.Y.Z-rpi.packages.txt` | every software package on the card |
| `khc-press-console-X.Y.Z.bundle.tar.xz` | the app update package (USB updates) |
| `khc-*.json` | the KHC firmware patch definitions (no firmware image is released) |
| `khc-press-console-index.json` | the update list the consoles read |
```
