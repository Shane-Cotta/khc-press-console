# Terms of use

Version 2026-10-05

These terms are an agreement between you and KHC Precision LLC, the maker of KHC Press Console ("we", "us"). They apply to KHC Press Console: the console app, the SD card images, the app update packages, the KHC patch definitions and the other files published on its releases page (together, "the software").

The console shows these terms when it first starts, and again whenever they change. It does not connect to a press until you tap **I AGREE**. If you do not agree, do not use the software.

## 1. Who may use the software

You must be 18 or older. If you use the software for a business, a club or another organization, you accept these terms for it and confirm that you are allowed to.

## 2. Your license

We grant you a personal, non-exclusive, non-transferable license to use the software with your own reloading press: during the 10-day trial, and then on each Raspberry Pi activated into a seat of a license you have bought (activated with the license number on the console, or from your phone with the code the console shows). One seat holds one Raspberry Pi. You may move a seat to another Raspberry Pi as the console allows (RELEASE SEAT). The software is licensed to you, not sold.

You may share the link to the releases page. You may not sell, rent or share license numbers, or get around the trial or the license check.

## 3. Payment, refunds and ending a license

The price is stated in the quote or invoice you receive when you buy it; refunds follow our refund policy at khcprecision.com/refunds#licenses. If a payment is refunded or reversed, or if you break these terms, we may end the license; its consoles then stop connecting to the press at the next license check that reaches our server. STOP never depends on the license.

## 4. BETA software

The software is a **BETA**: it is still being tested, and parts of it have not yet been verified on real hardware (see [Safety](SAFETY.md#not-yet-verified-on-real-hardware)). It may contain errors that affect how your press behaves. Do not use it if you are not prepared to treat every session as a test.

## 5. Reloading is dangerous: you accept the risk

Reloading ammunition and operating a powered press are inherently dangerous. A fault in the software, the press, its firmware, the Raspberry Pi, a cable, a sensor or the components you load can make the press move unexpectedly, fail to stop, or make defective ammunition. That can cause serious injury, death, or damage to equipment and property.

**You use the software at your own risk, and you knowingly and voluntarily accept all of these risks.**

## 6. The safety essentials

- **The press console's power switch is the only hard stop.** Keep it within reach whenever the press is powered. STOP on the screen is a message over a USB cable, not an emergency stop.
- Switch off the console power at once when the screen shows a CRITICAL alert, when the press does not stop as soon as you tap STOP, press the remote stop or open the guard, or when anything is not as you expect.
- Before you load components, check that STOP, the remote stop and the guard stop the press. Use an empty shell plate for your first sessions, after every software or firmware update and after any change of hardware.
- Calibrate after every connection. Keep your hands out of the press whenever it can move.
- Read [the full safety guide](SAFETY.md), published with the software, before you use it.

## 7. Your responsibilities

You alone are responsible for:
- operating your press safely and following its maker's instructions;
- keeping its power switch, guard, remote stop and other safety devices working;
- the components and load data you use, and the ammunition you make, which you must check (powder charge, primer seating, overall length) before it is fired;
- keeping other people, and children above all, away from the press while it can move;
- anyone you let use your press with the software;
- obeying the laws where you are. The software is for reloading for your own use. Making ammunition for sale may need a license (in the United States, a federal firearms license as a manufacturer).

## 8. No warranty

**THE SOFTWARE IS PROVIDED "AS IS" AND "AS AVAILABLE", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT.** We do not promise that it works, that it is free of errors, or that it is safe for your equipment.

## 9. Limitation of liability

**TO THE FULLEST EXTENT PERMITTED BY LAW:**
- **WE ARE NOT LIABLE FOR ANY INDIRECT, INCIDENTAL, SPECIAL, CONSEQUENTIAL, EXEMPLARY OR PUNITIVE DAMAGES, OR FOR ANY LOSS OF PROFITS, DATA, COMPONENTS, AMMUNITION, EQUIPMENT OR USE, HOWEVER CAUSED;**
- **OUR TOTAL LIABILITY FOR ALL CLAIMS ARISING FROM OR RELATING TO THE SOFTWARE OR THESE TERMS, IN CONTRACT, TORT (INCLUDING NEGLIGENCE), STRICT LIABILITY OR OTHERWISE, IS LIMITED TO THE AMOUNT YOU PAID US FOR THE SOFTWARE IN THE 12 MONTHS BEFORE THE CLAIM, OR US$50 IF YOU PAID NOTHING.**

Some places do not allow some of these limits. There, they apply as far as the law allows.

## 10. Indemnity

You agree to defend, indemnify and hold us harmless from any claim, loss or expense (including reasonable lawyers' fees) brought by anyone else that arises from your use of the software, from the ammunition you make, or from your breach of these terms.

## 11. Not affiliated with Mark 7, Lyman or Dillon

The software is an independent project. It is not made, authorized, supported or endorsed by Mark 7 Reloading, Lyman Products Corporation or Dillon Precision Products, and it is not a product of any of them.

Mark 7, Apex 10, Evolution, Revolution, BulletSense, PrimerSense, DecapSense, SwageSense, TorqueSense, PowderCheck and other Mark 7 names are trademarks of Lyman Products Corporation; Dillon, Super 1050, XL 750 and RL 1100 are trademarks of Dillon Precision Products. They are used only to describe compatibility. No logo, trade dress or product of Mark 7 Reloading, Lyman or Dillon is part of the software. Check with the press maker how using unofficial software affects your warranty or support.

## 12. Press firmware

Apart from the earlier SD card images described below, the software contains no press firmware: neither Mark 7's firmware nor any firmware made from it. It carries only the KHC patch definitions, small files that list a few bytes to change. Before it flashes a press it has identified, the console backs up the firmware that press is running; when you ask for the KHC patch, your console applies it to a backup of your own press's firmware and flashes the result to your own press. Mark 7's firmware remains the property of its owner, and these terms grant you no rights in it.

SD card images of version 0.3.0b3 or earlier, and consoles set up from them, also carry two complete KHC builds for the Evo and the Revo (Mark 7's firmware with a few bytes changed). They were included only so that the software can work with the presses it was made for (interoperability), and this section applies to them too.

## 13. Updates

The console downloads and installs updates from the releases page only when you ask it to. Updates are checked against the published checksums but are **not digitally signed** in this BETA (see [Safety](SAFETY.md#software-updates)). Install updates only from the releases page, or from a USB stick you prepared yourself from it.

## 14. The software is ours

The KHC Press Console app is distributed in compiled form (native machine code) inside the SD card image and the update packages. Its source code is not published and it remains our copyright. Apart from using it as these terms allow, you may not copy, modify, redistribute, decompile or reverse engineer the KHC Press Console app, except where the law allows it regardless of these terms.

## 15. Third-party components

The SD card image is built on Raspberry Pi OS (Debian) and includes third-party open-source components, which remain under their own licenses. Among them: the Linux kernel and many Debian packages (GPL and other free licenses), Python (Python Software Foundation License), skia-python and Skia (BSD 3-Clause), pyserial (BSD 3-Clause), python-evdev (BSD 3-Clause), kms++ (Mozilla Public License 2.0), the IBM Plex fonts (SIL Open Font License 1.1) and the Roboto fonts (Apache License 2.0). The card's boot partition holds `SOURCES.txt`, which says where the source code of those components can be obtained, and the console's ABOUT screen lists the licenses. Nothing in these terms limits your rights under those licenses.

## 16. What the console sends

The console works offline. With a network it sets its clock from internet time servers, and it contacts:
- **our license server**: to activate a license (the license number, a one-way code made from the Raspberry Pi's serial number, never the serial itself, the app version and a random key the console made); to get its seat back after the card is re-flashed or a phone has paired it (that code, that key and the console's pairing code); and, while licensed, to check in (the seat, that code and a secret key our server gave the console) by itself at most once an hour, or when you tap CHECK NOW. The phone page at khcprecision.com/activate sends the license number and the pairing code, and the pairing is kept for 24 hours. The server keeps your seat record (that code and its activation and end dates) for as long as the license exists, the customer name and notes we record when you buy, and a log of requests (the seat, the start of that code, the license's last four characters, the app version and a one-way code of the internet address) for up to 2 years. Raw internet addresses and serial numbers are never stored;
- **our diagnostics service**, only when you send a DIAGNOSTIC UPLOAD: the company, first name and description you type, that one-way code, a summary of the console and the press, and the console's logs, with Wi-Fi network names, license details, PINs and passwords removed. The description and the summary are published as an issue on the public GitHub page of KHC Press Console (for a console without an active license, only after we review it); the company and the name never are. We keep the report for 2 years and the logs privately for 180 days;
- **GitHub**, when you check for or download an update.

Our servers run on Amazon Web Services. The console's logs otherwise stay on the console, unless you save them to a USB stick yourself (SAVE LOGS). Our privacy policy at khcprecision.com/privacy explains what we keep and how to ask us to delete it.

## 17. Ending these terms

You may end these terms at any time by no longer using the software. They end by themselves if you break them. Sections 5, 7, 8, 9, 10, 14 and 19 still apply after they end.

## 18. Changes

We may change these terms with a new release. The console then shows the new terms and asks you to accept them before it next connects to the press; a press session already running is never interrupted. The terms in a release are the ones that apply to it.

## 19. General

These terms are governed by the laws of the State of California, and disputes about them are heard only in the courts of California. If a part of these terms cannot be enforced, the rest still applies. These terms, together with the terms of sale and the refund policy that apply where you bought your license, are the whole agreement between you and us about the software. If we do not enforce a part of them, we have not given it up.

## 20. Your agreement

By tapping **I AGREE** on the console you confirm that you are 18 or older, that you have read these terms, the safety essentials in section 6 included, and that you accept them. The console keeps a record of when these terms were accepted on it.
