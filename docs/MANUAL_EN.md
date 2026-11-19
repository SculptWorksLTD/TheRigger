# The Rigger — Manual

## In short

The Rigger is the only program that talks to the radio, and it gives every program its own connection: WSJT-X, loggers, contest and SDR software all work together on the same radio. It finds radios by itself, handles more than one and updates itself. It never transmits on its own.

## Installation

**Windows**: download `The-Rigger-Windows.zip`, put **The Rigger.exe** in a folder of yours (for example *Documents*) and open it. If *Windows protected your PC* appears: **More info › Run anyway**. No need to install OmniRig, com0com or Hamlib. The Desktop shortcut is created automatically.

**Mac**: download `The-Rigger-Mac.pkg` (Apple chip) or `The-Rigger-Mac-Intel.pkg` (Intel) and install it. If the Mac will not open it: *System Settings › Privacy & Security › Open Anyway*.

## First start

Connect the radio with the USB cable and switch it on: within a few seconds it appears in the **Radio** tab. There is nothing to set in The Rigger. Then set up your programs as below.

## Connecting programs

Three rules apply to every mode:

- **PTT** always on **CAT** (or *PTT via radio command*), never RTS or DTR.
- Address always **127.0.0.1** (your own computer).
- After setting it up, press **Test**, **Connect** or **OK** in the program.

Pick the mode your program knows:

| Mode | What you set | Programs |
|---|---|---|
| Hamlib | *Hamlib NET rigctl* · `127.0.0.1:4532` | WSJT-X, JTDX, JS8Call, MacLoggerDX, Gpredict, CQRLOG, VarAC |
| flrig | *FLRig* · `127.0.0.1` port `12345` | fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog, Cloudlog) |
| TCI | *TCI* · `127.0.0.1:40001` | N1MM Logger+, MSHV, Log4OM, DXLog |
| OmniRig (Windows) | *OmniRig* · *Rig 1* | Log4OM, HDSDR, SDR Console, CW Skimmer, MMSSTV, UcxLog |
| Ham Radio Deluxe | server `127.0.0.1` port `7809` | HRD Logbook, DM-780 |
| DXLab Commander | `127.0.0.1` port `52002` | BBLogger |
| Network CAT | real model or *Kenwood TS-2000* · `127.0.0.1:4600` | N1MM Logger+, DXLab Commander (model *Thetis*) |
| Serial ports (Mac) | real model · port `/tmp/TheRigger/…` · any speed | RUMlogNG, SkookumLogger |

### Hamlib (WSJT-X and similar)

1. **Rig**: *Hamlib NET rigctl* (in some programs *rigctld*, model 2).
2. **Server**: `127.0.0.1:4532`.
3. **PTT**: *CAT*. In WSJT-X press **Test CAT**: it turns green.

### flrig

1. Choose **FLRig** (in fldigi: *Rig Control › flrig › Connect to flrig*).
2. Address `127.0.0.1`, port `12345`. No need to install flrig.

### TCI

1. Choose **TCI**, address `127.0.0.1:40001`.
2. Audio stays on the radio's sound card as usual.

### OmniRig (Windows only)

1. Choose **OmniRig**, then **Rig 1** (second radio **Rig 2**). Do not install the real OmniRig.
2. Start programs normally, not *as administrator*.

### Ham Radio Deluxe

1. Server `127.0.0.1`, port `7809`, press **Connect**. No need to open HRD Rig Control.
2. MMTTY and MMVARI: copy the free plugin **HRDPTT.mmr** into the program folder and choose **HRDPTT** as port.

### DXLab Commander (BBLogger)

1. In BBLogger, *Preferences › CAT*: **IP** `127.0.0.1`, **Port** `52002`, **Autostart** empty. No CatBKT.
2. In the QSO window press **CAT ON**.

### Network CAT

1. As radio the **real model** (for example *IC-7100*) or **Kenwood TS-2000**, connection **TCP**, `127.0.0.1` port `4600`.
2. DXLab Commander: **Model** *Thetis*, **Communicate via TCP**, `127.0.0.1` port `4600`.

### Serial ports (Mac)

As radio the **real model** or **Kenwood TS-2000**, port `/tmp/TheRigger/IC-7100-1` (the name follows the radio), any speed, no handshake. One port per program.

### N3FJP (Windows)

*Rig Interface*: **None**. *Application Program Interface*: tick **TCP API Enabled**, port `1100`. Band, mode and frequency fill in by themselves.

### Second radio

| Mode | First radio | Second radio |
|---|---|---|
| Hamlib | 4532 | 4534 |
| flrig | 12345 | 12346 |
| TCI | 40001 | 40002 |
| DXLab Commander | 52002 | 52102 |
| Network CAT | 4600 | 4601 |
| OmniRig | Rig 1 | Rig 2 |
| Ham Radio Deluxe | radio 1 | radio 2 (same port 7809) |

### Programs not listed

Look in the program for one of these, in this order: *Hamlib/rigctld*, *FLRig*, *TCI*, *OmniRig*, *Ham Radio Deluxe*, *TCP*. Use the matching row of the table. Windows programs that only know COM ports (Logger32, Win-Test, SatPC32) cannot be connected: use Log4OM, N1MM or Gpredict.

## The window

- **Radio**: the radios found, with frequency, mode and connected programs. The power button on a card frees the radio for another program (for example the manufacturer's software); the real radio stays on.
- **Manual**: this manual.
- **Settings**: language, start at login, *Start hidden*, updates, ports and drivers.

The Rigger updates itself at every start.

## Windows only

- **Conflicting programs**: if the real OmniRig, CatBKT, DXLab Commander, flrig, rigctld, HRD or virtual COM port software steal the radio or the ports, a yellow line appears in the Radio tab. **See** opens the list with **Close…**, **Uninstall…** or **Clean up…** (OmniRig leftovers in the registry).
- **com0com cleanup**: *Settings › Ports and drivers › Clean up…* removes com0com and its virtual ports. Read the warning, confirm and restart at the end.
- **USB drivers**: if one is missing, The Rigger installs the official one by itself.

## Reports and ideas

The speech-bubble button, top right: **Something is wrong** or **Idea or request**. Attach the log of the last start. It is anonymous; the callsign is optional. *See exactly what is sent* shows everything before sending.

## Common problems

- **The radio does not appear**: switch it on, check the cable and press *Search radios again*. Close programs that open the radio's USB port directly.
- **The program does not connect**: check mode and address in the table again. If the program was open before The Rigger, press *Test* or *Connect* again.
- **PTT does not work**: set PTT to **CAT** in the program.
- **OmniRig not found**: open The Rigger at least once, then reopen the program (not as administrator).

---

The Rigger · software by IU1MVI · free for all hams. OmniRig compatibility uses the public OmniRig interface by VE3NEA (MIT license). Hamlib, flrig, TCI and Ham Radio Deluxe are trademarks of their respective owners. 73!
