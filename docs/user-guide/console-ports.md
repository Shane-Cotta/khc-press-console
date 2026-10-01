# Console ports

The Mark 7 press console has seven sensor ports (4-cavity 2x2 connectors), the micro-USB port for the console (the
Raspberry Pi), the USB-A port and 8-pin connector for the ClearPath motor, and the power connectors. Which sensor goes
into which port depends on the press. The tables below come from Mark 7's manuals; the console shows the same
information under **CONSOLE SETTINGS → CONSOLE PORTS** (or **CONSOLE PORTS** on the press screen's Settings tab), for
your connected press or for a press family you pick. That screen only shows text: nothing is sent to the press.

| | |
|---|---|
| ![Console ports of an Evolution](../images/screen-ports-evolution.png) | ![Choosing a press family before connecting](../images/screen-ports-1050-picker.png) |

## Before you plug anything in

- **Connect and disconnect sensors with the console switched off.**
- **DecapSense must be plugged in before the console connects:** the press looks for it only when it starts, and
  every connection restarts it.
- **On a 1050, port 2 is SwageSense:** never connect a DIY Primer Orientation sensor there.
- No manual gives a pinout of the ports. Do not wire anything of your own to them without checking with a meter.
- **Never plug anything into the USB-A port except the ClearPath motor's cable.**

## Apex 10 Evolution

(from the Apex 10 / Evolution AutoDrive manual)

| Port | Sensor | Note |
|---|---|---|
| 1 | PrimerSense + SwageSense | SwageSense plugs into a pigtail off the PrimerSense cable. Remove the PrimerSense battery when it is connected. |
| 2 | Primer Orientation | Optional. Learned at each CALIBRATE: its checks run only once it has been learned. |
| 3 | BulletSense | Laser sensor, powered by the console. |
| 4 | Powder Check (PowderSense) | Optical powder check. |
| 5 | DecapSense | Optical spent-primer sensor. Plug it in before the console connects. |
| 6 | Remote Stop | Wired remote stop, optional. |
| 7 | Powder Measure | Digital Powder Measure communication cable. |

## Revolution

(from the Revolution manual)

| Port | Sensor | Note |
|---|---|---|
| 1 | SwageSense | Microswitch on the swage back-up. The Revolution's low-primer switch goes to the vibratory controller, not here. |
| 2 | Primer Orientation | Optional. Learned at each CALIBRATE. |
| 3 | BulletSense | With a clear plate, RUN or SINGLE CYCLE must raise the BulletSense alert. |
| 4 | Digital Powder Check | Rod at station 7. Test with an empty and a double charge. |
| 5 | DecapSense | Under station 2. Plug it in before the console connects. |
| 6 | Remote Stop | Wired remote stop, optional. |
| 7 | Powder Measure | Communication cable to the measure's electronics box. |

## 1050 PRO, 1050 X, 1050 LTE

(from the 1050 PRO AutoDrive manual)

| Port | Sensor | Note |
|---|---|---|
| 1 | PrimerSense | Microswitch on the Dillon low-primer alarm. |
| 2 | SwageSense | Microswitch at station 3. **Never plug a DIY Primer Orientation sensor in here.** |
| 3 | BulletSense | With a clear plate, RUN or SINGLE CYCLE must raise the BulletSense alert. |
| 4 | Mark 7 PowderCheck | Optical powder check. |
| 5 | DecapSense | Plug it in before the console connects. Clean it every 500-700 rounds with compressed air; no solvents. |
| 6 | Safety Shield + Remote Stop | The shield cable has a pigtail for the remote stop. RUN, END CYCLE and SINGLE CYCLE are refused while the shield is open; JOG is not. |
| 7 | PowderSense | Mark 7 cable to the Dillon powder check at station 6. |

## 650 X, 650 PRO (and 750)

(from the 650 X & PRO AutoDrive manual)

| Port | Sensor | Note |
|---|---|---|
| 1 | PrimerSense | Microswitch on the Dillon low-primer alarm. |
| 2 | (unused) | The manual lists no sensor here. |
| 3 | BulletSense | Set its height with the platform at home, after a calibration. |
| 4 | (unused) | The manual lists no sensor here. |
| 5 | DecapSense (standard) | Mounts under the platform. Plug it in before the console connects. |
| 6 | Remote Stop | Wired remote stop, optional. |
| 7 | PowderSense | The Dillon powder check switch. |

## The other connectors (every model)

| Connector | What it is |
|---|---|
| Micro-USB | **The link to the console.** A USB-A to micro-USB data cable from here to a USB port of the Raspberry Pi. |
| USB-A | **Motor USB**, to the back of the ClearPath motor. Nothing else, ever. |
| 8-pin | Motor signal cable, into the top of the motor. |
| AC inlet with ON/OFF | Mains power. **The switch is the press's hard stop.** |
| Motor 6-pin | Motor DC power. Never switch the console on without it, and never plug or unplug it with the power on. |
| Tablet DC | Power for Mark 7's tablet. The Raspberry Pi uses its own power supply. |

The Evolution PRO, the Duals and the GAP PRO get their family's table (their own manuals were not available).
