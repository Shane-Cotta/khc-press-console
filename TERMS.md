# Terms of use

These terms apply to M7 Console: the SD card images, the app update packages, the press firmware images and the other
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

## 6. Not affiliated with Mark 7

The software is an independent project. It is not made, authorized, supported or endorsed by Mark 7 Reloading or its
owners, and it is not a Mark 7 product. "Mark 7", the Mark 7 logo, "Apex 10", "Evolution", "Revolution" and the
other press names, and "Dillon" and the Dillon press names, are the names and marks of their owners, used only to say
which presses the software works with and to give the console a familiar look. Check with the press maker how using
unofficial software affects your warranty or support.

## 7. Press firmware in the software

The software contains Mark 7's original press firmware images (for the Evolution, Revolution, 650 PRO, 1050 PRO and
1050 X), unmodified, and custom firmware images derived from the Evolution and Revolution originals. The vendor
firmware, including the parts of it contained in the custom images, remains the property of its owner. It is included
only so that the software can work with, and restore, the presses it was made for (interoperability). These terms
grant you no rights in the vendor firmware.

## 8. Updates

The console can download and install updates from this repository's releases when you ask it to. Updates are
checked against the published checksums but are **not digitally signed** in this BETA (see
[Safety](SAFETY.md#software-updates)). Install updates only from this repository's releases page, or from a USB stick
you prepared yourself from it.

## 9. Source code

The M7 Console app is distributed as readable Python inside the SD card image and the update packages, but its
source code is not published in this repository and it remains the authors' copyright. Apart from using it as
described in section 1, these terms give you no license to copy, modify or redistribute the M7 Console app's code.

## 10. Third-party components

The SD card image is built on Raspberry Pi OS (Debian) and includes third-party open-source components, which remain
under their own licenses. Among them: the Linux kernel and many Debian packages (GPL and other free licenses),
Python (Python Software Foundation License), skia-python and Skia (BSD 3-Clause), pyserial (BSD 3-Clause),
python-evdev (BSD 3-Clause), kms++ (Mozilla Public License 2.0) and the Roboto fonts (Apache License 2.0). The card's
boot partition holds `SOURCES.txt`, which says where the source code of those components can be obtained, and the
console's ABOUT screen lists the licences. Nothing in these terms limits your rights under those licenses.

## 11. Changes

These terms may change with future releases. The version in this repository at the time you download a release
applies to that release.
