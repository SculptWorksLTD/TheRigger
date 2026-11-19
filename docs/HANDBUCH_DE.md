# The Rigger — Handbuch

## Kurz gesagt

The Rigger spricht als Einziger mit dem Funkgerät und gibt jedem Programm eine eigene Verbindung: WSJT-X, Logbuch-, Contest- und SDR-Programme arbeiten gemeinsam am selben Funkgerät. Er findet die Funkgeräte selbst, verwaltet mehrere und aktualisiert sich selbst. Er sendet nie von sich aus.

## Installation

**Windows**: `The-Rigger-Windows.zip` herunterladen, **The Rigger.exe** in einen eigenen Ordner legen (zum Beispiel *Dokumente*) und öffnen. Erscheint *Der Computer wurde durch Windows geschützt*: **Weitere Informationen › Trotzdem ausführen**. OmniRig, com0com oder Hamlib müssen nicht installiert werden. Die Verknüpfung auf dem Desktop entsteht von selbst.

**Mac**: `The-Rigger-Mac.pkg` (Apple-Chip) oder `The-Rigger-Mac-Intel.pkg` (Intel) herunterladen und installieren. Öffnet der Mac es nicht: *Systemeinstellungen › Datenschutz & Sicherheit › Trotzdem öffnen*.

## Erster Start

Das Funkgerät mit dem USB-Kabel anschließen und einschalten: nach wenigen Sekunden erscheint es im Reiter **Funkgeräte**. In The Rigger ist nichts einzustellen. Danach die Programme wie unten einstellen.

## Programme verbinden

Drei Regeln gelten für alle Arten:

- **PTT** immer auf **CAT** (oder *PTT per Funkgerätebefehl*), nie RTS oder DTR.
- Adresse immer **127.0.0.1** (dein eigener Computer).
- Nach dem Einstellen im Programm **Test**, **Connect** oder **OK** drücken.

Wähle die Art, die dein Programm kennt:

| Art | Was du einstellst | Programme |
|---|---|---|
| Hamlib | *Hamlib NET rigctl* · `127.0.0.1:4532` | WSJT-X, JTDX, JS8Call, MacLoggerDX, Gpredict, CQRLOG, VarAC |
| flrig | *FLRig* · `127.0.0.1` Port `12345` | fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog, Cloudlog) |
| TCI | *TCI* · `127.0.0.1:40001` | N1MM Logger+, MSHV, Log4OM, DXLog |
| OmniRig (Windows) | *OmniRig* · *Rig 1* | Log4OM, HDSDR, SDR Console, CW Skimmer, MMSSTV, UcxLog |
| Ham Radio Deluxe | Server `127.0.0.1` Port `7809` | HRD Logbook, DM-780 |
| DXLab Commander | `127.0.0.1` Port `52002` | BBLogger |
| Netzwerk-CAT | echtes Modell oder *Kenwood TS-2000* · `127.0.0.1:4600` | N1MM Logger+, DXLab Commander (Modell *Thetis*) |
| Serielle Ports (Mac) | echtes Modell · Port `/tmp/TheRigger/…` · beliebige Geschwindigkeit | RUMlogNG, SkookumLogger |

### Hamlib (WSJT-X und ähnliche)

1. **Rig**: *Hamlib NET rigctl* (in manchen Programmen *rigctld*, Modell 2).
2. **Server**: `127.0.0.1:4532`.
3. **PTT**: *CAT*. In WSJT-X **Test CAT** drücken: es wird grün.

### flrig

1. **FLRig** wählen (in fldigi: *Rig Control › flrig › Connect to flrig*).
2. Adresse `127.0.0.1`, Port `12345`. flrig muss nicht installiert sein.

### TCI

1. **TCI** wählen, Adresse `127.0.0.1:40001`.
2. Der Ton bleibt wie immer auf der Soundkarte des Funkgeräts.

### OmniRig (nur Windows)

1. **OmniRig** wählen, dann **Rig 1** (zweites Funkgerät **Rig 2**). Das echte OmniRig nicht installieren.
2. Programme normal starten, nicht *als Administrator*.

### Ham Radio Deluxe

1. Server `127.0.0.1`, Port `7809`, **Connect** drücken. HRD Rig Control muss nicht laufen.
2. MMTTY und MMVARI: das kostenlose Plugin **HRDPTT.mmr** in den Programmordner kopieren und **HRDPTT** als Port wählen.

### DXLab Commander (BBLogger)

1. In BBLogger, *Preferences › CAT*: **IP** `127.0.0.1`, **Port** `52002`, **Autostart** leer. Kein CatBKT.
2. Im QSO-Fenster **CAT ON** drücken.

### Netzwerk-CAT

1. Als Funkgerät das **echte Modell** (zum Beispiel *IC-7100*) oder **Kenwood TS-2000**, Verbindung **TCP**, `127.0.0.1` Port `4600`.
2. DXLab Commander: **Model** *Thetis*, **Communicate via TCP**, `127.0.0.1` Port `4600`.

### Serielle Ports (Mac)

Als Funkgerät das **echte Modell** oder **Kenwood TS-2000**, Port `/tmp/TheRigger/IC-7100-1` (der Name folgt dem Funkgerät), beliebige Geschwindigkeit, kein Handshake. Ein Port pro Programm.

### N3FJP (Windows)

*Rig Interface*: **None**. *Application Program Interface*: **TCP API Enabled** anhaken, Port `1100`. Band, Betriebsart und Frequenz füllen sich selbst aus.

### Mehrere Funkgeräte (bis 10 und mehr)

Jedes Funkgerät hat eigene Adressen: Funkgerät 1 ist das erste im Reiter Funkgeräte, Funkgerät 2 das zweite und so weiter. Für die weiteren den angegebenen Schritt addieren.

| Art | Funkgerät 1 | Funkgerät 2 | Funkgerät 3 | Jedes weitere | Funkgerät 10 |
|---|---|---|---|---|---|
| Hamlib | 4532 | 4534 | 4536 | +2 | 4550 |
| flrig | 12345 | 12346 | 12347 | +1 | 12354 |
| TCI | 40001 | 40002 | 40003 | +1 | 40010 |
| DXLab Commander | 52002 | 52102 | 52202 | +100 | 52902 |
| Netzwerk-CAT | 4600 | 4601 | 4602 | +1 | 4609 |
| Ham Radio Deluxe | Funkgerät 1 | Funkgerät 2 | Funkgerät 3 | gleicher Port 7809 | Funkgerät 10 |
| OmniRig | Rig 1 | Rig 2 | — | nur 2: das ist die Grenze von OmniRig | — |

Zwei gleiche Funkgeräte heißen zum Beispiel *IC-7300* und *IC-7300 2*. Bei mehr als zwei Funkgeräten sehen OmniRig-Programme nur die ersten beiden: für die anderen Hamlib, flrig oder TCI nehmen.

### Programme, die nicht in der Liste stehen

Suche im Programm eine dieser Optionen, in dieser Reihenfolge: *Hamlib/rigctld*, *FLRig*, *TCI*, *OmniRig*, *Ham Radio Deluxe*, *TCP*. Nimm die passende Zeile der Tabelle. Windows-Programme, die nur COM-Ports kennen (Logger32, Win-Test, SatPC32), lassen sich nicht verbinden: nimm Log4OM, N1MM oder Gpredict.

## Das Fenster

- **Funkgeräte**: die gefundenen Funkgeräte mit Frequenz, Betriebsart und verbundenen Programmen. Die Ein-Taste der Karte gibt das Funkgerät für ein anderes Programm frei (zum Beispiel die Software des Herstellers); das echte Funkgerät bleibt an.
- **Handbuch**: dieses Handbuch.
- **Einstellungen**: Sprache, automatischer Start, *Versteckt starten*, Updates, Ports und Treiber.

The Rigger aktualisiert sich bei jedem Start selbst.

## Nur Windows

- **Störende Programme**: nehmen das echte OmniRig, CatBKT, DXLab Commander, flrig, rigctld, HRD oder Software für virtuelle COM-Ports das Funkgerät oder die Ports weg, erscheint im Reiter Funkgeräte eine gelbe Zeile. **Ansehen** öffnet die Liste mit **Schließen…**, **Deinstallieren…** oder **Bereinigen…** (Reste von OmniRig in der Registry).
- **com0com-Bereinigung**: *Einstellungen › Ports und Treiber › Bereinigen…* entfernt com0com und seine virtuellen Ports. Hinweis lesen, bestätigen und am Ende neu starten.
- **USB-Treiber**: fehlt einer, installiert The Rigger selbst den offiziellen.

## Meldungen und Ideen

Die Sprechblasen-Taste oben rechts: **Etwas funktioniert nicht** oder **Idee oder Wunsch**. Das Protokoll des letzten Starts anhängen. Es ist anonym; das Rufzeichen ist freiwillig. *Genau ansehen, was gesendet wird* zeigt alles vor dem Senden.

## Häufige Probleme

- **Das Funkgerät erscheint nicht**: einschalten, Kabel prüfen und *Funkgeräte erneut suchen* drücken. Programme schließen, die den USB-Port des Funkgeräts direkt öffnen.
- **Das Programm verbindet sich nicht**: Art und Adresse in der Tabelle nochmals prüfen. War das Programm vor The Rigger offen, nochmals *Test* oder *Connect* drücken.
- **PTT geht nicht**: im Programm PTT auf **CAT** stellen.
- **OmniRig nicht gefunden**: The Rigger mindestens einmal öffnen, dann das Programm neu öffnen (nicht als Administrator).

---

The Rigger · Software von IU1MVI · kostenlos für alle Funkamateure. Die OmniRig-Kompatibilität nutzt die öffentliche OmniRig-Schnittstelle von VE3NEA (MIT-Lizenz). Hamlib, flrig, TCI und Ham Radio Deluxe sind Marken ihrer jeweiligen Inhaber. 73!
