# Terms of use

These terms apply to KHC Press Console: the SD card images, the app update packages, the press firmware images and the other
files published in this repository and on its releases page (together, "the software"). By downloading, installing
or using the software, you agree to them.

## 1. Free to download and use

You may download, install and use the software free of charge, for your own use with your own equipment. To share it
with others, please share a link to this repository's releases page, so that they get the current files, these
terms and the safety information.

## 2. BETA software

The software is a **BETA**: it is still being tested, and parts of it have not yet been verified on real hardware
(see [Safety](SAFETY.md#not-yet-verified-on-real-hardware)). It may contain errors that affect how your press
behaves. Do not use it if you are not prepared to treat every session as a test.

## 3. No warranty

The software is provided **"as is"**, without warranty of any kind, express or implied, including but not limited to
the warranties of merchantability, fitness for a particular purpose and non-infringement. There is no guarantee that
it works, that it is free of errors, or that it is safe for your equipment.

## 4. No liability

To the fullest extent permitted by law, the authors and publishers of the software are not liable for any claim,
damages or other liability, including injury, damage to equipment, ammunition or property, or loss of data, whether
in contract, tort or otherwise, arising from or in connection with the software or its use.

## 5. Your responsibility on real machinery

The software controls a reloading press, a machine with a servo motor, pinch points, primers and powder. You are
solely responsible for operating your press safely: for keeping its power switch, stop controls and safety devices
working and within reach, for checking that they stop the press, for the components you load, and for following the
press maker's instructions. Read [Safety](SAFETY.md) before you use the software.

## 6. Not affiliated with Mark 7, Lyman or Dillon

The software is an independent project. It is not made, authorized, supported or endorsed by Mark 7 Reloading, Lyman
Products Corporation or Dillon Precision Products, and it is not a product of any of them.

Mark 7, Apex 10, Evolution, Revolution, BulletSense, PrimerSense, DecapSense, SwageSense, TorqueSense, PowderCheck and
other Mark 7 names are trademarks of Lyman Products Corporation; Dillon, Super 1050, XL 750 and RL 1100 are trademarks
of Dillon Precision Products. Evo, Revo and Apex refer to those Mark 7 presses, and 650/750 and 1050/1100 to the Dillon
presses Mark 7's drives fit. KHC Precision is not affiliated with, sponsored by, or endorsed by either company; the
names are used only to describe compatibility. No logo, trade dress or product of Mark 7 Reloading, Lyman or Dillon is
part of the software.

Check with the press maker how using unofficial software affects your warranty or support.

## 7. Press firmware in the software

The software no longer contains Mark 7's original press firmware images. It contains the KHC primer-learn patch
builds for the Evo and the Revo, which are derived from Mark 7's firmware: each is Mark 7's original image with a
few bytes changed (the Primer Orientation fix and the version number). The vendor firmware, including the parts of it
contained in the KHC builds, remains the property of its owner. It is included only so that the software can work
with the presses it was made for (interoperability). These terms grant you no rights in the vendor firmware.

## 8. Updates

The console can download and install updates from this repository's releases when you ask it to. Updates are
checked against the published checksums but are **not digitally signed** in this BETA (see
[Safety](SAFETY.md#software-updates)). Install updates only from this repository's releases page, or from a USB stick
you prepared yourself from it.

## 9. Source code

The KHC Press Console app is distributed in compiled form (native machine code) inside the SD card image and the update
packages. Its source code is not published and it remains the authors' copyright. Apart from using it as described
in section 1, these terms give you no license to copy, modify, redistribute, decompile or reverse engineer the KHC
Press Console app, except where the law allows it regardless of these terms.

## 10. Third-party components

The SD card image is built on Raspberry Pi OS (Debian) and includes third-party open-source components, which remain
under their own licenses. Among them: the Linux kernel and many Debian packages (GPL and other free licenses),
Python (Python Software Foundation License), skia-python and Skia (BSD 3-Clause), pyserial (BSD 3-Clause),
python-evdev (BSD 3-Clause), kms++ (Mozilla Public License 2.0), the IBM Plex fonts (SIL Open Font License 1.1)
and the Roboto fonts (Apache License 2.0). The card's
boot partition holds `SOURCES.txt`, which says where the source code of those components can be obtained, and the
console's ABOUT screen lists the licences. Nothing in these terms limits your rights under those licenses.

## 11. Changes

These terms may change with future releases. The version in this repository at the time you download a release
applies to that release.
