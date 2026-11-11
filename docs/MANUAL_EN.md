# The Rigger — Manual

## What it does

The Rigger is a switchboard between your radios and the programs on your computer. Normally a radio's serial port can be used by only one program at a time. The Rigger is the only one that talks to the radio, and it gives every program a connection of its own, so WSJT-X, your logger, your contest program and the others all work together on the same radio without getting in each other's way.

It handles several radios at the same time, on Windows and macOS.

## Installation

Download the file for your system from the project's **Releases** page on GitHub.

- **Windows**: run `The-Rigger-…-Setup.exe` and follow the installer. If "Windows protected your PC" appears, choose *More info › Run anyway*.
- **macOS**: open `The-Rigger-…-Mac.pkg` (Apple silicon Macs) or `The-Rigger-…-Mac-Intel.pkg` (Intel Macs): The Rigger is installed in Applications. If the Mac blocks it: right-click the file › *Open*.

From then on The Rigger updates itself and starts by itself when the computer starts.

## First start

At startup the welcome window with the credits appears. Press **Start · 73**.

Connect the radio with its USB cable and switch it on. Within a few seconds The Rigger recognises it on its own: it tries the USB ports, the protocol and the speed, and finds the model. There is nothing to set up.

## The window

The window shows only what you need:

- **one line per radio**, with a light: green if the radio is connected and answering, grey if it is off or unplugged;
- **under each radio, the connected programs**, each with its own light: green if it is talking to the radio, yellow if it has the port open but is idle.

If you read "no program connected" under a radio, no program is using it.

At the top there are three buttons: **?** (how to connect your programs, and this manual), **⚙** (settings) and **⏻** (quits The Rigger).

Closing the window does not stop The Rigger: it stays in the notification area next to the clock and your programs stay connected. To reopen it, click the icon and choose *Show window*.

## Connecting your programs

Press **?**: for each program The Rigger tells you exactly what to set, with the port already chosen. The **Copy** button copies the port name or the address so you can paste it into the program.

There are two kinds of connection:

1. **Hamlib NET rigctl**: for WSJT-X, JTDX, JS8Call, fldigi, CQRLOG and the other programs that support it. In the program choose *Hamlib NET rigctl* as the rig and the address shown as the server (for example `127.0.0.1:4532`). Any number of programs can connect to this address.
2. **Serial port**: for Log4OM, N1MM Logger+, HRD, Logger32, DXLab Commander, MixW and all the others. In the program choose **your radio's real model** (for example Icom IC-7100) or **Kenwood TS-2000** as the rig, and the port shown. Any baud rate, no handshake, PTT via CAT.
   - On Windows the ports are normal `COM` ports.
   - On Mac they are in `/tmp/TheRigger/`, for example `/tmp/TheRigger/IC-7100-1`.

**Automatic recognition**: each port recognises the program's protocol on its own (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 or TS-2000). If you choose the real model in the program, commands go straight to the radio and all of its functions work. If you choose Kenwood TS-2000, the common functions work: frequency, mode, PTT and split. With Yaesu radios, the very first time a program set to TS-2000 uses a port, PTT may not key on the first transmission: from the second one on it works, and the port remembers.

One program per port: The Rigger already assigns them so they never clash. Each radio has 4 ports, which you can raise to 16 in the settings.

### Examples

- **WSJT-X**: *Settings › Radio*: Rig *Hamlib NET rigctl*, Network Server *127.0.0.1:4532*, PTT method *CAT*.
- **Log4OM**: in the CAT settings choose the *Kenwood TS-2000* rig on the port shown for Log4OM. OmniRig is no longer needed.
- **Programs that use OmniRig** (Windows): no need to install OmniRig. The Rigger stands in for it: choose *OmniRig* in the program; *Rig 1* is the first radio switched on in The Rigger, *Rig 2* the second. If the program asks for it while The Rigger is closed, Windows opens it automatically. (Interface compatible with OmniRig by Alex Shovkoplyas VE3NEA, MIT licence.)
- **N1MM Logger+**: *Config › Configure Ports*: Radio *Kenwood TS-2000*, the COM port shown for N1MM, any speed, *DTR* and *RTS* off.

## Settings

- **Language**: automatic (the system language) or one of the seven available.
- **Start automatically**: The Rigger starts by itself when the computer starts.
- **Automatic updates**: new versions install themselves, and only when no program is using the radio.
- **Automatic USB drivers**: missing USB drivers are installed on their own.
- **Ports per radio**: from 1 to 16. Applies immediately; ports in use are never removed.

## USB drivers

- **Windows**: if you plug in a radio that has no driver, The Rigger downloads the official signed driver from Windows Update (or from the manufacturer) and installs it. Windows asks for one confirmation. It covers Silicon Labs (Icom, Yaesu, Kenwood), FTDI (Elecraft and many cables), WCH CH340 (Xiegu and cheap cables) and Prolific.
- **macOS**: the drivers are already part of the system.

The virtual COM ports on Windows use the free *com0com* driver, which The Rigger installs on its own the first time (with one Windows confirmation).

## Supported radios

- **Icom** and CI-V compatibles (Xiegu too): IC-7100, IC-7300, IC-705, IC-7610, IC-9700, IC-905, IC-7760 and others.
- **Kenwood**: TS-2000, TS-480, TS-590S/SG, TS-890S, TS-990S.
- **Elecraft**: K3, KX2, KX3, K4.
- Recent **Yaesu**: FT-991/A, FTDX10, FT-710, FTDX101, FT-891, FTDX3000 and others.
- Classic **Yaesu**: FT-817, FT-818, FT-857, FT-897.
- Other radios with Kenwood-compatible commands: Lab599 TX-500, QRP Labs QDX/QMX and many SDRs.

## Common problems

- **The radio does not appear**: check that it is on and connected with the USB cable. On Icom radios the *CI-V USB* baud rate in the radio menu must be *Auto* or a normal value; *CI-V USB Echo Back* can stay as it is.
- **A program does not connect**: press **?** and check that you chose *Kenwood TS-2000* (or *Hamlib NET rigctl*) and the right port. Two programs cannot use the same serial port.
- **A program's light is yellow**: the program opened the port but is not polling the radio. Check that CAT is enabled in the program.
- **Windows does not create the COM ports**: on some Windows 11 PCs the *com0com* driver may be blocked. In that case use the *Hamlib NET rigctl* connection, which always works.

---

The Rigger · software developed by IU1MVI · free to use for all hams. 73!
