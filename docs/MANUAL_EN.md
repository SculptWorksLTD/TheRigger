# The Rigger — Manual

## What it does

The Rigger is a switchboard between your radios and the programs on your computer.

Normally a radio's CAT port can be used by only one program at a time: if WSJT-X opens it, the logger can no longer find it. The Rigger changes that. The Rigger is the only one talking to the radio and it gives every program a connection of its own. So WSJT-X, the logger, the contest program, CWIU1MVI, the SDR program and the others all work together on the same radio without getting in each other's way.

In short:

- **it finds radios on its own**: plug in the USB cable and the radio appears, with no ports, speeds or models to choose;
- **several radios at once**: each one has its own connections;
- **every connection programs use**: Hamlib, flrig, TCI, OmniRig (Windows), Ham Radio Deluxe, network CAT and serial ports (Mac and Linux);
- **it updates itself** and speaks 7 languages.

The Rigger never transmits by itself and never changes anything on the radio: it only does what the programs ask.

## Installation

Download the file for your system from the **Releases** page of the project on GitHub (SculptWorksLTD/TheRigger).

### Windows

1. Download `The-Rigger-…-Windows.zip`.
2. Open the zip and drag **The Rigger.exe** into a folder of yours, for example *Documents › The Rigger*. Do not leave it inside the zip or in a temporary Downloads folder.
3. Double-click **The Rigger.exe**.
4. If *Windows protected your PC* appears, click **More info** and then **Run anyway**. This happens only the first time.

Nothing else to install: no OmniRig, no com0com, no Hamlib.

### macOS

1. Download `The-Rigger-…-Mac.pkg` if your Mac has an Apple chip (M1, M2, M3, M4), or `The-Rigger-…-Mac-Intel.pkg` for an Intel Mac.
2. Open the file and follow the installer: The Rigger goes into **Applications**.
3. If the Mac says it cannot open it: right-click the file › **Open**, or *System Settings › Privacy & Security › Open Anyway*.

From then on The Rigger updates itself.

## First start

At start-up the welcome window with the credits appears: press **Start · 73**.

Connect the radio with the USB cable and switch it on. Within a few seconds The Rigger finds it: it tries the USB ports, the protocol (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817) and the speed, then recognises the model. You do not have to set anything.

When the radio appears in the **Radios** tab it is ready: to set up each program see the chapter **Instructions for programs** in this manual.

## The window

The window has three tabs, chosen at the top in the middle:

- **Radios**: the radios found, with frequency, mode, connected programs and addresses;
- **Manual**: this manual, with the index on the left;
- **Settings**: language, start-up, updates, ports and information.

At the top right there are two buttons:

- **Hide** (down arrow): hides the window. On a Mac The Rigger stays in the menu bar, near the clock: click the icon and choose *Show The Rigger*. On Windows the window goes to the taskbar.
- **Power** (⏻): quits The Rigger. Connected programs lose the radio until you open it again.

At the bottom there is the status bar: the light is green when at least one radio is connected, yellow when there is a warning. The button with the circular arrow searches for radios again. The version is on the right.

You can resize the window by dragging its edges.

## Radios tab

Every radio found has a card of its own.

### Header

- **Power button** (left): turns the radio on or off *inside The Rigger*. When off, The Rigger closes its USB port and leaves it free, for example for the manufacturer's program or a firmware update. Press again to take it back. The real radio is not switched off.
- **Name**: the model, with a number if you have two identical radios (for example *IC-7300 2*).
- **Status**: *connected* (it answers), *offline* (cable unplugged or radio off) or *off* (turned off in The Rigger).

### Display

- **Frequency** of the VFO in use, in large digits, with the **mode** next to it (USB, LSB, CW, CW-R, RTTY, AM, FM, USB-D, LSB-D, FM-D).
- **A** and **B**: which VFO is in use.
- **SPLIT**: lit when the radio is in split.
- **TX**: turns red when the radio transmits.
- Below: the frequency of the other VFO and the **S-meter** bar.

The display follows the radio in real time, both when you turn the knob and when a program changes the frequency.

### Radio details

The grey line shows model, USB port, speed and, if the radio is on in The Rigger, its number (**Rig 1**, **Rig 2**…). The number is used by OmniRig and Ham Radio Deluxe.

### Connected programs

The list of programs using this radio, each with a light:

- **green**: the program is talking to the radio;
- **yellow**: the program is connected but is not asking anything right now.

On the right is the connection it uses (for example `tcp:4532`, `flrig`, `TCI`, a serial port). Click it to copy its address.

### Addresses for programs

All the ways a program can connect to this radio, with the address to type into the program. Click an address to copy it. The explanations are in the chapter **The connections**.

### Buttons

- **Test connection**: pretends to be a program and reads the frequency through every connection (serial port, Hamlib, flrig, network CAT, TCI). Every line with **✓** works, every line with **✗** has a problem. The test only reads: it never transmits and never changes anything.

### Search radios again

The **Search radios again** button (top right of the tab, or the circular arrow at the bottom) checks all USB ports again right away. Use it after switching on a radio The Rigger did not see, or after closing a program that was holding the port.

## The connections

The Rigger opens all these connections for every radio at once. Each program uses the one it knows, and several programs can share the same connection.

| Connection | Address (first radio) | Second radio | Systems |
|---|---|---|---|
| Hamlib NET rigctl | 127.0.0.1:4532 | 127.0.0.1:4534 | all |
| flrig | 127.0.0.1:12345 | 127.0.0.1:12346 | all |
| TCI | 127.0.0.1:40001 | 127.0.0.1:40002 | all |
| Network CAT (Kenwood TS-2000) | 127.0.0.1:4600 | 127.0.0.1:4601 | all |
| Ham Radio Deluxe | 127.0.0.1:7809 (radio 1) | same port, radio 2 | all |
| OmniRig | Rig 1 | Rig 2 | Windows |
| Serial ports | /tmp/TheRigger/… | /tmp/TheRigger/… | Mac and Linux |

If a port is already taken by another program (for example a real flrig or rigctld already running), The Rigger uses the next free one: you always find the exact address in the Radios tab.

### Hamlib NET rigctl

The connection of WSJT-X, JTDX, JS8Call, FreeDV, Gpredict, CQRLOG, KLog, MacLoggerDX, Pat and every program that uses Hamlib.

In the program choose **Hamlib NET rigctl** as the rig (in some programs *NET rigctl* or *rigctld*, Hamlib model number 2) and the address shown as the server, for example `127.0.0.1:4532`. Set PTT to **CAT**.

### flrig

The Rigger answers exactly like flrig (W1HKJ). It is the connection of fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog and Cloudlog), WFDlogger and every program with a *FLRig* option.

In the program choose **FLRig**, address `127.0.0.1` and port `12345` (second radio `12346`). You do not need to install flrig.

### TCI

The Rigger answers like a TCI transceiver (the Expert Electronics protocol). It is used by N1MM Logger+, JTDX, MSHV, Log4OM, QLog, Swisslog, DXLog and others.

In the program choose **TCI** and the address `127.0.0.1:40001` (second radio `40002`). The Rigger's TCI carries frequencies, mode, PTT and split; audio stays on the radio's sound card as always.

### OmniRig (Windows only)

The Rigger takes the place of OmniRig: **you do not need to install OmniRig**. In the program choose **OmniRig** and then **Rig 1** for the first radio switched on in The Rigger or **Rig 2** for the second.

It works with Log4OM, DXLog.net, HDSDR, SDR Console, CW Skimmer, UcxLog, Swisslog, MixW, QARTest, VarAC and every program that uses OmniRig, both 32-bit and 64-bit. If a program asks for OmniRig while The Rigger is closed, Windows opens The Rigger by itself, hidden.

If the real OmniRig is installed too, programs still find The Rigger, except those started *as administrator*: start them normally. Do not run both at the same time on the same radio.

### Ham Radio Deluxe

The Rigger answers like *HRD Rig Control*. It serves HRD Logbook, DM-780 and the programs that connect to Ham Radio Deluxe (also WSJT-X and JTDX with the *Ham Radio Deluxe* choice).

In the program set the server `127.0.0.1` port `7809`. Radios have the same names as in The Rigger and are numbered 1, 2, 3… in the order of the Radios tab.

### Network CAT (TCP)

An address that behaves like the radio's serial port. It suits programs that can connect to a radio over TCP, such as N1MM Logger+ and MSHV.

In the program choose **the real model** (for example *IC-7100*) or **Kenwood TS-2000** as the rig, and the address shown as the port, for example `127.0.0.1:4600`. PTT on **CAT**.

### Serial ports (Mac and Linux)

For programs that insist on a serial port, The Rigger creates a few virtual ports for every radio, for example `/tmp/TheRigger/IC-7100-1`, `/tmp/TheRigger/IC-7100-2`…

In the program choose the **real model** or **Kenwood TS-2000** as the rig, the port shown, **any** speed, handshake **none**, PTT **CAT**.

Each port recognises the program's language on its own: Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 or TS-2000. If you choose the real model, every command reaches the radio, including the special ones. With TS-2000, frequency, mode, PTT and split work.

One program per port: The Rigger gives each program a different port. The number of ports per radio is changed in Settings (from 1 to 16).

On Windows The Rigger does not create virtual COM ports: use the other connections, which need no drivers.

### CWIU1MVI

CWIU1MVI finds The Rigger by itself: in CWIU1MVI's radio list choose **The Rigger · radio name**. Nothing else to set.

## Instructions for programs

Here are the steps for the most used programs. Addresses are those of the first radio: for other radios copy them from the Radios tab.

### WSJT-X, JTDX, JS8Call, WSJT-Z

1. *File › Settings › Radio*.
2. **Rig**: *Hamlib NET rigctl*.
3. **Network Server**: `127.0.0.1:4532`.
4. **PTT Method**: *CAT*.
5. **Mode**: *Data/Pkt* if you want the radio in USB-D, otherwise *USB*.
6. **Split Operation**: *Rig* or *Fake It*, as you prefer.
7. Press **Test CAT**: it turns green. Then **OK**.

### fldigi

1. *Configure › Config dialog › Rig Control › flrig*.
2. Tick **Connect to flrig**, address `127.0.0.1`, port `12345`.
3. Untick *Hamlib* and *RigCAT* if they are ticked.
4. **Save** and close: fldigi's frequency follows the radio.

### Log4OM 2 (Windows)

1. *Settings › CAT interface*.
2. **CAT engine**: *OmniRig*. **Rig**: *Rig 1* (or *Rig 2* for the second radio).
3. Tick **Autostart** and press **Connect**.

You do not need to install OmniRig. Alternatively choose *Hamlib* › *Connect to active HAMLIB interface* with port `4532`.

### N1MM Logger+ (Windows)

1. *Config › Configure Ports, Mode Control, Winkey, etc… › Hardware*.
2. On a port line choose **TCP**, **Radio**: *IC-7100* (the real model) or *Kenwood TS-2000*.
3. Press **Set** and enter address `127.0.0.1` port `4600`.
4. Turn on **PTT via Radio Command**.
5. **OK**: the frequency appears at the bottom left.

Alternatively N1MM can use **TCI** with `127.0.0.1:40001`.

### HRD Logbook and DM-780 (Windows)

In the radio connection window choose server `127.0.0.1` port `7809` and press **Connect**. There is no need to open *HRD Rig Control*: The Rigger answers.

### QLog

1. *Settings › Equipment › Rig*, add a rig.
2. **Interface**: *FLRig*, host `127.0.0.1`, port `12345` (or *Hamlib* › *NET rigctl* with `127.0.0.1:4532`).
3. Save and connect the rig from the *Equipment* menu.

### MacLoggerDX (Mac)

1. *Prefs › Radio*.
2. Choose **Hamlib rigctld**, host `127.0.0.1`, port `4532`.
3. Turn on **Radio VFO** in the control window.

Alternatively choose the real radio model and a port in `/tmp/TheRigger/`.

### RUMlogNG and SkookumLogger (Mac)

In the radio preferences choose the **real model** (or Kenwood TS-2000) and a port in `/tmp/TheRigger/`, for example `/tmp/TheRigger/IC-7100-2`, any speed.

### Wavelog and Cloudlog (with WaveLogGate)

In WaveLogGate open *Config › Radio*, choose **FLRig**, host `127.0.0.1`, port `12345`, and save. Wavelog receives frequency and mode and can change them.

### HAMRS, Not1MM, WFDlogger

In the rig control settings choose **FLRig**, host `127.0.0.1`, port `12345`.

### MSHV

*Options › Radio and Network Configuration*: choose **TCI** and the address `127.0.0.1:40001`.

### HDSDR, SDR Console, CW Skimmer (Windows)

Choose **OmniRig** (in HDSDR *Options › CAT to Radio (Omni-Rig)*, in SDR Console *Radio › External Radio*, in CW Skimmer *Setup › Radio*) and then **Rig 1**.

### Gpredict

*Edit › Preferences › Interfaces › Radios › Add new*: host `localhost`, port `4532`, type *RX + TX* or whatever you need.

### CQRLOG (Linux)

*Preferences › TRX control*: untick *Run rigctld*, **Rig model**: *2 Hamlib NET rigctl*, **Device**: `127.0.0.1:4532`.

### VarAC (Windows)

*Settings › Rig control*: choose **OmniRig** and *Rig 1*, or **Hamlib (rigctld)** with `127.0.0.1` port `4532`.

### DXLab Commander (Windows)

Commander cannot use OmniRig or Hamlib, but it can talk to Thetis over the network: The Rigger answers like Thetis.

1. *Config › Ports*, radio panel: **Model**: *Thetis*.
2. Tick **Communicate via TCP**, **IP Address** `127.0.0.1`, **IP Port** `4600` (second radio `4601`).
3. Close the configuration: Commander shows the frequency, and so do DXKeeper, SpotCollector and the rest of the DXLab suite.

### N3FJP ACLog and N3FJP contest programs (Windows)

N3FJP programs cannot share a radio without a COM port, but they have a network interface: The Rigger uses it by itself to send band, mode and frequency of the first radio that is on.

1. *Settings › Rig Interface*: choose **None**.
2. *Settings › Application Program Interface*: tick **TCP API Enabled (Server)**, port `1100`.
3. Done: band, mode and frequency fill in by themselves. The Rigger never logs QSOs for you.

This way ACLog cannot change the radio's frequency (for example by clicking a spot).

### MMSSTV, MMTTY and MMVARI (Windows)

- **MMSSTV**: *Option › Setup › TX › Radio command*, choose **OmniRig** and *Rig 1*.
- **MMTTY and MMVARI**: download the free **HRDPTT.mmr** plugin (it lets MM programs talk to Ham Radio Deluxe), copy it into the program folder, then *Option › Setup › TX › Radio command* and choose **HRDPTT** as the port. The Rigger answers like Ham Radio Deluxe, so PTT goes through The Rigger.

### Programs that only want a COM port (Windows)

Logger32, Win-Test, Winlink Express and SatPC32 only know COM ports, which on Windows need a driver signed by Microsoft: for now The Rigger cannot be used with these programs. In Winlink Express radio control is optional; instead of SatPC32 you can use Gpredict.

### Programs not listed

Look for which connection the program knows:

- if it has *Hamlib*, *NET rigctl* or *rigctld*, use Hamlib (`127.0.0.1:4532`);
- if it has *FLRig*, use flrig (`127.0.0.1:12345`);
- if it has *TCI*, use TCI (`127.0.0.1:40001`);
- if it has *OmniRig* (Windows), use OmniRig *Rig 1*;
- if it has *Ham Radio Deluxe*, use `127.0.0.1:7809`;
- if it connects to a radio over TCP, use network CAT (`127.0.0.1:4600`) with the real model or Kenwood TS-2000;
- if it only wants a serial port (Mac and Linux), use a port in `/tmp/TheRigger/`.

## Several radios at once

The Rigger handles every radio you connect. Each radio has:

- its own addresses (different ports, see the table in the chapter *The connections*);
- its own number (**Rig 1**, **Rig 2**…) for OmniRig and Ham Radio Deluxe, following the order in the Radios tab and counting only the radios that are on.

If you have two radios of the same model they are called, for example, *IC-7300* and *IC-7300 2*.

## Turning a radio off in The Rigger

The power button on a radio's card turns it off **only inside The Rigger**: the USB port is freed and that radio's connections close. Use it when another program has to use the radio directly, for example the manufacturer's program or a firmware update.

The Rigger remembers the choice after a restart too. Press the button again to take the radio back.

## Settings

### General

- **Language**: *Automatic* uses the system language; otherwise choose Italian, English, French, German, Spanish, Portuguese or Japanese. The whole window, the manual and the program instructions change at once.
- **Start automatically**: The Rigger opens by itself when the computer starts, so the radios are ready before the programs.

### Updates

- **Automatic updates**: at every start The Rigger checks for a new version. If there is one, it downloads it, installs it and restarts by itself in a few seconds; programs reconnect by themselves.
- **Check for updates**: checks right now. The line below says what is happening (*you already have the latest version*, *downloading update…*).

Small fixes to the window arrive in a moment, even without restarting.

### Ports and drivers

- **Serial ports per radio** (Mac and Linux): how many virtual ports to create for each radio, from 1 to 16. It applies immediately; ports in use by a program are never removed.
- **Automatic USB drivers** (Windows): if you connect a radio without a driver, The Rigger installs the official one (see *USB drivers*).

### About

Version, credits and the button to buy IU1MVI a coffee with PayPal.

## USB drivers

- **Windows**: if you connect a radio with no driver, The Rigger downloads the official signed one (from Windows Update or the manufacturer) and installs it. Windows asks for confirmation only once. It covers Silicon Labs CP210x (Icom, Yaesu, Kenwood), FTDI (Elecraft and many cables), WCH CH340 (Xiegu and cheap cables) and Prolific.
- **macOS**: the drivers are already in the system, nothing to do.

## Supported radios

| Brand | Models |
|---|---|
| Icom | IC-7100, IC-7300, IC-7300MK2, IC-705, IC-7610, IC-7760, IC-9700, IC-905, IC-7851, IC-7800, IC-7700, IC-7600, IC-7410, IC-7200, IC-7000, IC-9100, IC-746PRO, IC-7400, IC-756 (all), IC-718, IC-706 (all), IC-703, IC-910H and the other CI-V radios, receivers IC-R8600, IC-R75, IC-R30 |
| Xiegu | G90, X6100, X6200, X5105, X108G (Icom CI-V protocol) |
| Kenwood | TS-890S, TS-990S, TS-590S/SG, TS-2000, TS-480, TS-870S, TS-570, TS-850, TS-450S, TS-690S and the others with CAT commands |
| Elecraft | K3, K3S, K4, KX2, KX3 |
| Yaesu | FTX-1, FTDX10, FTDX101D/MP, FT-710, FT-991/991A, FT-891, FTDX3000, FTDX5000, FTDX1200, FT-950, FT-2000, FT-450/450D, FTDX9000 |
| Classic Yaesu | FT-817, FT-818, FT-857, FT-897 |
| FlexRadio | 6000 series through the SmartSDR CAT port |
| Kenwood-compatible | Lab599 TX-500, QRP Labs QDX/QMX, (tr)uSDX, Malachite and many SDRs |

Icom radios whose CI-V address was changed in the menu are found anyway.

## Troubleshooting

**The radio does not appear.** Check that it is on and connected with the USB cable, then press *Search radios again*. If another program opened the radio's USB port before The Rigger, close it: The Rigger must own the port. On Icom radios the *CI-V USB Baud Rate* should be *Auto* or a normal value.

**On Windows the radio does not appear and the driver is missing.** Keep *Automatic USB drivers* on and confirm Windows' request. If that is not enough, install the cable maker's driver and press *Search radios again*.

**The program does not connect.** Check in this manual that you chose the right connection and copy the exact address from the Radios tab (one click copies it). Then press *Test connection*: if every line has ✓, The Rigger works and the problem is in the program's settings.

**The program's light is yellow.** The program is connected but is not asking the radio anything. Check in the program that CAT control is enabled (there is often a *Connect* or *Enable* button).

**PTT does not work.** In the program PTT must be set to **CAT** (or *PTT via Radio Command*), not RTS or DTR.

**An OmniRig program says OmniRig is missing.** The Rigger must have been opened at least once on this computer. Open it, then reopen the program.

**A port is already used by another program.** If flrig, rigctld or another program holds the same ports, The Rigger takes the next free one: copy the exact address from the Radios tab.

**I want to use the radio with the manufacturer's program.** Turn the radio off in The Rigger with its power button: the USB port is freed.

---

The Rigger · software developed by IU1MVI · free to use for all hams.
OmniRig compatibility uses the public interface of OmniRig by Alex Shovkoplyas, VE3NEA (MIT licence). Hamlib, flrig, TCI and Ham Radio Deluxe are trademarks of their respective owners. 73!
