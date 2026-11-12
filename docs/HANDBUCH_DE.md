# The Rigger — Handbuch

## Was es macht

The Rigger ist eine Vermittlungsstelle zwischen deinen Funkgeräten und den Programmen auf dem Computer.

Normalerweise kann den CAT-Port eines Funkgeräts nur ein Programm gleichzeitig benutzen: Öffnet WSJT-X ihn, findet das Logbuch ihn nicht mehr. Mit The Rigger ist das anders. The Rigger spricht als Einziger mit dem Funkgerät und gibt jedem Programm eine eigene Verbindung. So arbeiten WSJT-X, das Logbuch, das Contest-Programm, CWIU1MVI, das SDR-Programm und die anderen zusammen am selben Funkgerät, ohne sich zu stören.

Kurz gesagt:

- **findet Funkgeräte selbst**: USB-Kabel einstecken, und das Funkgerät erscheint, ohne Port, Geschwindigkeit oder Modell zu wählen;
- **mehrere Funkgeräte gleichzeitig**: jedes hat seine eigenen Verbindungen;
- **alle Verbindungen, die Programme nutzen**: Hamlib, flrig, TCI, OmniRig (Windows), Ham Radio Deluxe, Netzwerk-CAT und serielle Ports (Mac und Linux);
- **aktualisiert sich selbst** und spricht 7 Sprachen.

The Rigger sendet nie von sich aus und ändert nichts am Funkgerät: Es tut nur, was die Programme verlangen.

## Installation

Lade die Datei für dein System von der Seite **Releases** des Projekts auf GitHub herunter (SculptWorksLTD/TheRigger).

### Windows

1. `The-Rigger-…-Windows.zip` herunterladen.
2. Das Zip öffnen und **The Rigger.exe** in einen eigenen Ordner ziehen, zum Beispiel *Dokumente › The Rigger*. Nicht im Zip oder in einem temporären Download-Ordner lassen.
3. Doppelklick auf **The Rigger.exe**.
4. Erscheint *Der Computer wurde durch Windows geschützt*, auf **Weitere Informationen** und dann **Trotzdem ausführen** klicken. Das passiert nur beim ersten Mal.

Sonst ist nichts zu installieren: kein OmniRig, kein com0com, kein Hamlib.

### macOS

1. `The-Rigger-…-Mac.pkg` herunterladen, wenn dein Mac einen Apple-Chip hat (M1, M2, M3, M4), oder `The-Rigger-…-Mac-Intel.pkg` für einen Intel-Mac.
2. Die Datei öffnen und der Installation folgen: The Rigger landet in **Programme**.
3. Wenn der Mac sie nicht öffnen will: Rechtsklick auf die Datei › **Öffnen**, oder *Systemeinstellungen › Datenschutz & Sicherheit › Trotzdem öffnen*.

Von da an aktualisiert sich The Rigger selbst.

## Erster Start

Beim Start erscheint das Willkommensfenster mit den Credits: **Los geht’s · 73** drücken.

Das Funkgerät mit dem USB-Kabel anschließen und einschalten. Nach wenigen Sekunden findet The Rigger es: Es probiert die USB-Ports, das Protokoll (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817) und die Geschwindigkeit und erkennt dann das Modell. Du musst nichts einstellen.

Sobald das Funkgerät im Reiter **Funkgeräte** erscheint, ist es bereit: Wie jedes Programm einzustellen ist, steht im Kapitel **Anleitungen für Programme** dieses Handbuchs.

## Das Fenster

Das Fenster hat drei Reiter, oben in der Mitte:

- **Funkgeräte**: die gefundenen Funkgeräte mit Frequenz, Betriebsart und verbundenen Programmen;
- **Handbuch**: dieses Handbuch, mit dem Inhaltsverzeichnis links;
- **Einstellungen**: Sprache, Start, Updates, Ports und Info.

Oben rechts gibt es zwei Tasten:

- **Ausblenden** (Pfeil nach unten): versteckt das Fenster. Auf dem Mac bleibt The Rigger in der Menüleiste neben der Uhr: Symbol anklicken und *The Rigger anzeigen* wählen. Unter Windows geht das Fenster in die Taskleiste.
- **Aus** (⏻): beendet The Rigger. Verbundene Programme verlieren das Funkgerät, bis du es wieder öffnest.

Unten ist die Statusleiste: Die Lampe ist grün, wenn mindestens ein Funkgerät verbunden ist, gelb bei einem Hinweis. Die Taste mit dem Kreispfeil sucht erneut nach Funkgeräten. Rechts steht die Version.

Die Fenstergröße lässt sich durch Ziehen an den Rändern ändern.

## Reiter Funkgeräte

Jedes gefundene Funkgerät hat eine eigene Karte.

### Kopfzeile

- **Ein-/Aus-Taste** (links): schaltet das Funkgerät *in The Rigger* ein oder aus. Ausgeschaltet schließt The Rigger seinen USB-Port und gibt ihn frei, zum Beispiel für das Programm des Herstellers oder ein Firmware-Update. Erneut drücken, um es zurückzunehmen. Das echte Funkgerät wird nicht ausgeschaltet.
- **Name**: das Modell, mit einer Nummer, wenn du zwei gleiche Geräte hast (zum Beispiel *IC-7300 2*).
- **Zustand**: *verbunden* (antwortet), *getrennt* (Kabel abgezogen oder Funkgerät aus) oder *aus* (in The Rigger ausgeschaltet).

### Anzeige

- **Frequenz** des benutzten VFO, groß, mit der **Betriebsart** daneben (USB, LSB, CW, CW-R, RTTY, AM, FM, USB-D, LSB-D, FM-D).
- **A** und **B**: welcher VFO benutzt wird.
- **SPLIT**: leuchtet, wenn das Funkgerät im Split ist.
- **TX**: wird rot, wenn das Funkgerät sendet.
- Darunter: die Frequenz des anderen VFO und der Balken des **S-Meters**.

Die Anzeige folgt dem Funkgerät in Echtzeit, sowohl beim Drehen am Knopf als auch wenn ein Programm die Frequenz ändert.

### Gerätedaten

Die graue Zeile zeigt Modell, USB-Port, Geschwindigkeit und, wenn das Gerät in The Rigger eingeschaltet ist, seine Nummer (**Rig 1**, **Rig 2**…). Die Nummer brauchen OmniRig und Ham Radio Deluxe.

### Verbundene Programme

Die Liste der Programme, die dieses Funkgerät benutzen, jedes mit einer Lampe:

- **grün**: das Programm spricht mit dem Funkgerät;
- **gelb**: das Programm ist verbunden, fragt aber gerade nichts.

Rechts steht die benutzte Verbindung (zum Beispiel `tcp:4532`, `flrig`, `TCI`, ein serieller Port). Anklicken kopiert ihre Adresse.

### Tasten

- **Verbindung testen**: tut so, als wäre es ein Programm, und liest die Frequenz über jede Verbindung (serieller Port, Hamlib, flrig, Netzwerk-CAT, TCI). Jede Zeile mit **✓** funktioniert, jede Zeile mit **✗** hat ein Problem. Der Test liest nur: Er sendet nie und ändert nichts.

### Funkgeräte erneut suchen

Die Taste **Funkgeräte erneut suchen** (oben rechts im Reiter oder der Kreispfeil unten) prüft sofort alle USB-Ports neu. Benutze sie, nachdem du ein Funkgerät eingeschaltet hast, das The Rigger nicht gesehen hat, oder nachdem du ein Programm geschlossen hast, das den Port belegt hatte.

## Die Verbindungen

The Rigger öffnet für jedes Funkgerät alle diese Verbindungen gleichzeitig. Jedes Programm benutzt die, die es kennt, und mehrere Programme können dieselbe Verbindung teilen.

| Verbindung | Adresse (erstes Gerät) | Zweites Gerät | Systeme |
|---|---|---|---|
| Hamlib NET rigctl | 127.0.0.1:4532 | 127.0.0.1:4534 | alle |
| flrig | 127.0.0.1:12345 | 127.0.0.1:12346 | alle |
| TCI | 127.0.0.1:40001 | 127.0.0.1:40002 | alle |
| Netzwerk-CAT (Kenwood TS-2000) | 127.0.0.1:4600 | 127.0.0.1:4601 | alle |
| Ham Radio Deluxe | 127.0.0.1:7809 (Gerät 1) | gleicher Port, Gerät 2 | alle |
| OmniRig | Rig 1 | Rig 2 | Windows |
| Serielle Ports | /tmp/TheRigger/… | /tmp/TheRigger/… | Mac und Linux |

Ist ein Port schon von einem anderen Programm belegt (zum Beispiel ein echtes flrig oder rigctld), nimmt The Rigger den nächsten freien: Die genaue Adresse zeigt *Verbindung testen* auf der Karte des Funkgeräts.

### Hamlib NET rigctl

Die Verbindung von WSJT-X, JTDX, JS8Call, FreeDV, Gpredict, CQRLOG, KLog, MacLoggerDX, Pat und allen Programmen, die Hamlib nutzen.

Im Programm als Funkgerät **Hamlib NET rigctl** wählen (in manchen Programmen *NET rigctl* oder *rigctld*, Hamlib-Modell Nummer 2) und als Server die angezeigte Adresse, zum Beispiel `127.0.0.1:4532`. PTT auf **CAT**.

### flrig

The Rigger antwortet genau wie flrig (W1HKJ). Es ist die Verbindung von fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog und Cloudlog), WFDlogger und allen Programmen mit der Option *FLRig*.

Im Programm **FLRig** wählen, Adresse `127.0.0.1` und Port `12345` (zweites Gerät `12346`). flrig muss nicht installiert werden.

### TCI

The Rigger antwortet wie ein TCI-Gerät (das Protokoll von Expert Electronics). Es wird von N1MM Logger+, JTDX, MSHV, Log4OM, QLog, Swisslog, DXLog und anderen benutzt.

Im Programm **TCI** und die Adresse `127.0.0.1:40001` wählen (zweites Gerät `40002`). Das TCI von The Rigger überträgt Frequenzen, Betriebsart, PTT und Split; das Audio bleibt wie immer auf der Soundkarte des Funkgeräts.

### OmniRig (nur Windows)

The Rigger nimmt den Platz von OmniRig ein: **OmniRig muss nicht installiert werden**. Im Programm **OmniRig** wählen und dann **Rig 1** für das erste in The Rigger eingeschaltete Funkgerät oder **Rig 2** für das zweite.

Das funktioniert mit Log4OM, DXLog.net, HDSDR, SDR Console, CW Skimmer, UcxLog, Swisslog, MixW, QARTest, VarAC und allen Programmen, die OmniRig benutzen, mit 32 wie mit 64 Bit. Fragt ein Programm nach OmniRig, während The Rigger geschlossen ist, öffnet Windows The Rigger selbst, ausgeblendet.

Ist auch das echte OmniRig installiert, finden die Programme trotzdem The Rigger, außer solche, die *als Administrator* gestartet wurden: starte sie normal. Lass nicht beide gleichzeitig am selben Funkgerät laufen.

### Ham Radio Deluxe

The Rigger antwortet wie *HRD Rig Control*. Es dient HRD Logbook, DM-780 und den Programmen, die sich mit Ham Radio Deluxe verbinden (auch WSJT-X und JTDX mit der Wahl *Ham Radio Deluxe*).

Im Programm den Server `127.0.0.1` Port `7809` einstellen. Die Geräte heißen wie in The Rigger und sind in der Reihenfolge des Reiters Funkgeräte mit 1, 2, 3… nummeriert.

### Netzwerk-CAT (TCP)

Eine Adresse, die sich wie der serielle Port des Funkgeräts verhält. Geeignet für Programme, die sich über TCP mit einem Funkgerät verbinden können, wie N1MM Logger+ und MSHV.

Im Programm als Funkgerät **das echte Modell** (zum Beispiel *IC-7100*) oder **Kenwood TS-2000** wählen und als Port die angezeigte Adresse, zum Beispiel `127.0.0.1:4600`. PTT auf **CAT**.

### Serielle Ports (Mac und Linux)

Für Programme, die unbedingt einen seriellen Port wollen, legt The Rigger für jedes Funkgerät einige virtuelle Ports an, zum Beispiel `/tmp/TheRigger/IC-7100-1`, `/tmp/TheRigger/IC-7100-2`…

Im Programm das **echte Modell** oder **Kenwood TS-2000** wählen, den angezeigten Port, **beliebige** Geschwindigkeit, Handshake **keiner**, PTT **CAT**.

Jeder Port erkennt die Sprache des Programms selbst: Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 oder TS-2000. Mit dem echten Modell erreichen alle Befehle das Funkgerät, auch die besonderen. Mit TS-2000 funktionieren Frequenz, Betriebsart, PTT und Split.

Ein Programm pro Port: The Rigger gibt jedem Programm einen anderen Port. Die Anzahl der Ports pro Funkgerät stellst du in den Einstellungen ein (1 bis 16).

Unter Windows legt The Rigger keine virtuellen COM-Ports an: Benutze die anderen Verbindungen, die keine Treiber brauchen.

### CWIU1MVI

CWIU1MVI findet The Rigger selbst: in der Funkgeräteliste von CWIU1MVI **The Rigger · Name des Funkgeräts** wählen. Sonst ist nichts einzustellen.

## Anleitungen für Programme

Hier die Schritte für die meistbenutzten Programme. Die Adressen gelten für das erste Funkgerät: für die anderen siehe die Tabelle im Kapitel *Die Verbindungen*.

### WSJT-X, JTDX, JS8Call, WSJT-Z

1. *File › Settings › Radio*.
2. **Rig**: *Hamlib NET rigctl*.
3. **Network Server**: `127.0.0.1:4532`.
4. **PTT Method**: *CAT*.
5. **Mode**: *Data/Pkt*, wenn das Funkgerät in USB-D gehen soll, sonst *USB*.
6. **Split Operation**: *Rig* oder *Fake It*, wie du willst.
7. **Test CAT** drücken: er wird grün. Dann **OK**.

### fldigi

1. *Configure › Config dialog › Rig Control › flrig*.
2. **Connect to flrig** ankreuzen, Adresse `127.0.0.1`, Port `12345`.
3. *Hamlib* und *RigCAT* abwählen, falls angekreuzt.
4. **Save** und schließen: Die Frequenz von fldigi folgt dem Funkgerät.

### Log4OM 2 (Windows)

1. *Settings › CAT interface*.
2. **CAT engine**: *OmniRig*. **Rig**: *Rig 1* (oder *Rig 2* für das zweite Funkgerät).
3. **Autostart** ankreuzen und **Connect** drücken.

OmniRig muss nicht installiert werden. Alternativ *Hamlib* › *Connect to active HAMLIB interface* mit Port `4532` wählen.

### N1MM Logger+ (Windows)

1. *Config › Configure Ports, Mode Control, Winkey, etc… › Hardware*.
2. In einer Port-Zeile **TCP** wählen, **Radio**: *IC-7100* (das echte Modell) oder *Kenwood TS-2000*.
3. **Set** drücken und Adresse `127.0.0.1` Port `4600` eingeben.
4. **PTT via Radio Command** einschalten.
5. **OK**: Unten links erscheint die Frequenz.

Alternativ kann N1MM **TCI** mit `127.0.0.1:40001` benutzen.

### HRD Logbook und DM-780 (Windows)

Im Fenster für die Funkgeräteverbindung den Server `127.0.0.1` Port `7809` wählen und **Connect** drücken. *HRD Rig Control* muss nicht geöffnet werden: The Rigger antwortet.

### QLog

1. *Settings › Equipment › Rig*, ein Funkgerät hinzufügen.
2. **Interface**: *FLRig*, Host `127.0.0.1`, Port `12345` (oder *Hamlib* › *NET rigctl* mit `127.0.0.1:4532`).
3. Speichern und das Funkgerät im Menü *Equipment* verbinden.

### MacLoggerDX (Mac)

1. *Prefs › Radio*.
2. **Hamlib rigctld** wählen, Host `127.0.0.1`, Port `4532`.
3. Im Steuerfenster **Radio VFO** einschalten.

Alternativ das echte Modell des Funkgeräts und einen Port aus `/tmp/TheRigger/` wählen.

### RUMlogNG und SkookumLogger (Mac)

In den Funkgeräte-Einstellungen das **echte Modell** (oder Kenwood TS-2000) und einen Port aus `/tmp/TheRigger/` wählen, zum Beispiel `/tmp/TheRigger/IC-7100-2`, beliebige Geschwindigkeit.

### Wavelog und Cloudlog (mit WaveLogGate)

In WaveLogGate *Config › Radio* öffnen, **FLRig** wählen, Host `127.0.0.1`, Port `12345`, und speichern. Wavelog erhält Frequenz und Betriebsart und kann sie ändern.

### HAMRS, Not1MM, WFDlogger

In den Einstellungen der Funkgerätesteuerung **FLRig** wählen, Host `127.0.0.1`, Port `12345`.

### MSHV

*Options › Radio and Network Configuration*: **TCI** und die Adresse `127.0.0.1:40001` wählen.

### HDSDR, SDR Console, CW Skimmer (Windows)

**OmniRig** wählen (in HDSDR *Options › CAT to Radio (Omni-Rig)*, in SDR Console *Radio › External Radio*, in CW Skimmer *Setup › Radio*) und dann **Rig 1**.

### Gpredict

*Edit › Preferences › Interfaces › Radios › Add new*: Host `localhost`, Port `4532`, Typ *RX + TX* oder was du brauchst.

### CQRLOG (Linux)

*Preferences › TRX control*: *Run rigctld* abwählen, **Rig model**: *2 Hamlib NET rigctl*, **Device**: `127.0.0.1:4532`.

### VarAC (Windows)

*Settings › Rig control*: **OmniRig** und *Rig 1* wählen, oder **Hamlib (rigctld)** mit `127.0.0.1` Port `4532`.

### DXLab Commander (Windows)

Commander kann weder OmniRig noch Hamlib benutzen, aber über das Netzwerk mit Thetis sprechen: The Rigger antwortet wie Thetis.

1. *Config › Ports*, Feld des Funkgeräts: **Model**: *Thetis*.
2. **Communicate via TCP** ankreuzen, **IP Address** `127.0.0.1`, **IP Port** `4600` (zweites Gerät `4601`).
3. Konfiguration schließen: Commander zeigt die Frequenz, und mit ihm DXKeeper, SpotCollector und der Rest der DXLab-Suite.

### N3FJP ACLog und N3FJP-Contestprogramme (Windows)

Die N3FJP-Programme können ein Funkgerät ohne COM-Port nicht teilen, haben aber eine Netzwerkschnittstelle: The Rigger nutzt sie selbst und sendet Band, Betriebsart und Frequenz des ersten eingeschalteten Funkgeräts.

1. *Settings › Rig Interface*: **None** wählen.
2. *Settings › Application Program Interface*: **TCP API Enabled (Server)** ankreuzen, Port `1100`.
3. Fertig: Band, Betriebsart und Frequenz füllen sich selbst aus. The Rigger loggt nie QSOs für dich.

So kann ACLog die Frequenz des Funkgeräts nicht ändern (zum Beispiel durch Klick auf einen Spot).

### MMSSTV, MMTTY und MMVARI (Windows)

- **MMSSTV**: *Option › Setup › TX › Radio command*, **OmniRig** und *Rig 1* wählen.
- **MMTTY und MMVARI**: das kostenlose Plugin **HRDPTT.mmr** herunterladen (es lässt die MM-Programme mit Ham Radio Deluxe sprechen), in den Programmordner kopieren, dann *Option › Setup › TX › Radio command* und als Port **HRDPTT** wählen. The Rigger antwortet wie Ham Radio Deluxe, also läuft die PTT über The Rigger.

### Programme, die nur einen COM-Port wollen (Windows)

Logger32, Win-Test, Winlink Express und SatPC32 kennen nur COM-Ports, die unter Windows einen von Microsoft signierten Treiber brauchen: Mit diesen Programmen lässt sich The Rigger vorerst nicht benutzen. Das kannst du stattdessen nehmen, alles kostenlos oder schon mit The Rigger nutzbar:

| Statt | Nimm | Verbindung |
|---|---|---|
| Logger32 | Log4OM 2, Swisslog, UcxLog, QLog oder die DXLab-Suite | OmniRig, Hamlib, flrig oder Thetis (Commander) |
| Win-Test | N1MM Logger+, DXLog.net oder QARTest | Netzwerk-CAT / TCI, OmniRig |
| Winlink Express | Pat Winlink, oder Winlink Express ohne Funkgerätesteuerung (Frequenz von Hand) | Hamlib |
| SatPC32 | Gpredict | Hamlib |

### Programme, die nicht in der Liste stehen

Schau, welche Verbindung das Programm kennt:

- hat es *Hamlib*, *NET rigctl* oder *rigctld*, nimm Hamlib (`127.0.0.1:4532`);
- hat es *FLRig*, nimm flrig (`127.0.0.1:12345`);
- hat es *TCI*, nimm TCI (`127.0.0.1:40001`);
- hat es *OmniRig* (Windows), nimm OmniRig *Rig 1*;
- hat es *Ham Radio Deluxe*, nimm `127.0.0.1:7809`;
- verbindet es sich über TCP mit einem Funkgerät, nimm Netzwerk-CAT (`127.0.0.1:4600`) mit dem echten Modell oder Kenwood TS-2000;
- will es nur einen seriellen Port (Mac und Linux), nimm einen Port aus `/tmp/TheRigger/`.

## Mehrere Funkgeräte gleichzeitig

The Rigger verwaltet alle Funkgeräte, die du anschließt. Jedes Funkgerät hat:

- seine eigenen Adressen (andere Ports, siehe die Tabelle im Kapitel *Die Verbindungen*);
- seine Nummer (**Rig 1**, **Rig 2**…) für OmniRig und Ham Radio Deluxe, nach der Reihenfolge im Reiter Funkgeräte, wobei nur eingeschaltete Geräte zählen.

Zwei Geräte desselben Modells heißen zum Beispiel *IC-7300* und *IC-7300 2*.

## Ein Funkgerät in The Rigger ausschalten

Die Ein-/Aus-Taste auf der Karte eines Funkgeräts schaltet es **nur in The Rigger** aus: Der USB-Port wird frei und die Verbindungen dieses Geräts schließen sich. Das braucht man, wenn ein anderes Programm direkt mit dem Funkgerät arbeiten muss, zum Beispiel das Programm des Herstellers oder ein Firmware-Update.

The Rigger merkt sich die Wahl auch nach einem Neustart. Erneut drücken, um das Funkgerät zurückzunehmen.

## Einstellungen

### Allgemein

- **Sprache**: *Automatisch* nimmt die Sprache des Systems; sonst Italienisch, Englisch, Französisch, Deutsch, Spanisch, Portugiesisch oder Japanisch wählen. Das ganze Fenster, das Handbuch und die Programmanleitungen ändern sich sofort.
- **Automatisch starten**: The Rigger öffnet sich beim Start des Computers selbst, so sind die Funkgeräte vor den Programmen bereit.

### Updates

- **Automatische Updates**: Bei jedem Start prüft The Rigger, ob es eine neue Version gibt. Wenn ja, lädt es sie herunter, installiert sie und startet in wenigen Sekunden selbst neu; die Programme verbinden sich selbst wieder.
- **Nach Updates suchen**: prüft sofort. Die Zeile darunter sagt, was passiert (*du hast schon die neueste Version*, *lade Update…*).

Kleine Korrekturen am Fenster kommen sofort, auch ohne Neustart.

### Ports und Treiber

- **Serielle Ports pro Funkgerät** (Mac und Linux): wie viele virtuelle Ports pro Funkgerät angelegt werden, 1 bis 16. Gilt sofort; Ports, die ein Programm benutzt, werden nie entfernt.
- **USB-Treiber automatisch** (Windows): Schließt du ein Funkgerät ohne Treiber an, installiert The Rigger den offiziellen (siehe *USB-Treiber*).

### Info

Version, Credits und die Taste, um IU1MVI mit PayPal einen Kaffee zu spendieren.

## USB-Treiber

- **Windows**: Schließt du ein Funkgerät ohne Treiber an, lädt The Rigger den offiziellen signierten Treiber (von Windows Update oder vom Hersteller) und installiert ihn. Windows fragt nur einmal nach. Abgedeckt sind Silicon Labs CP210x (Icom, Yaesu, Kenwood), FTDI (Elecraft und viele Kabel), WCH CH340 (Xiegu und günstige Kabel) und Prolific.
- **macOS**: Die Treiber sind schon im System, nichts zu tun.

## Unterstützte Funkgeräte

| Marke | Modelle |
|---|---|
| Icom | IC-7100, IC-7300, IC-7300MK2, IC-705, IC-7610, IC-7760, IC-9700, IC-905, IC-7851, IC-7800, IC-7700, IC-7600, IC-7410, IC-7200, IC-7000, IC-9100, IC-746PRO, IC-7400, IC-756 (alle), IC-718, IC-706 (alle), IC-703, IC-910H und die anderen CI-V-Geräte, Empfänger IC-R8600, IC-R75, IC-R30 |
| Xiegu | G90, X6100, X6200, X5105, X108G (Icom-CI-V-Protokoll) |
| Kenwood | TS-890S, TS-990S, TS-590S/SG, TS-2000, TS-480, TS-870S, TS-570, TS-850, TS-450S, TS-690S und die anderen mit CAT-Befehlen |
| Elecraft | K3, K3S, K4, KX2, KX3 |
| Yaesu | FTX-1, FTDX10, FTDX101D/MP, FT-710, FT-991/991A, FT-891, FTDX3000, FTDX5000, FTDX1200, FT-950, FT-2000, FT-450/450D, FTDX9000 |
| Klassische Yaesu | FT-817, FT-818, FT-857, FT-897 |
| FlexRadio | Serie 6000 über den CAT-Port von SmartSDR |
| Kenwood-kompatibel | Lab599 TX-500, QRP Labs QDX/QMX, (tr)uSDX, Malachite und viele SDRs |

Icom-Geräte, deren CI-V-Adresse im Menü geändert wurde, werden trotzdem gefunden.

## com0com-Bereinigung (Windows)

### Was passiert

Jeder Schritt wird im Fenster von The Rigger angezeigt. Gesucht wird com0com, den kostenlosen Treiber, der Paare virtueller COM-Ports anlegt, und dann: deinstalliert ihn, entfernt alle seine virtuellen Ports (auch die „Geister“-Ports, die der Geräte-Manager nicht zeigt), entfernt seinen Treiber aus Windows und gibt die COM-Nummern frei, die diese Ports belegt hatten. Bevor etwas geändert wird, zeigt es, was gefunden wurde, und fragt nach; am Ende bietet es einen Neustart an.

### Wozu

Mit der Zeit hinterlässt com0com Dutzende oder Hunderte virtueller Ports und reservierter COM-Nummern: neue USB-Ports bekommen sehr hohe Nummern, Windows zeigt ständig Fehler, Funkprogramme kommen durcheinander und der PC wird langsamer. The Rigger nutzt keine virtuellen COM-Ports (die Programme verbinden sich über OmniRig, Hamlib, flrig, TCI, HRD oder Netzwerk-CAT: siehe Handbuch), daher wird com0com nicht mehr gebraucht.

### Risiken

Administratorrechte sind nötig. Programme, die com0com benutzen, funktionieren mit diesen Ports nicht mehr: zum Beispiel ein Port-Splitter oder zwei Programme, die über virtuelle Ports verbunden sind. Echte COM-Ports (Funkgeräte, USB-Seriell-Kabel) werden nicht angefasst. Das lässt sich nicht rückgängig machen: Wenn du com0com wieder brauchst, musst du es neu installieren. Schließe vorher die Programme, die COM-Ports benutzen. Nutzung auf eigene Gefahr: der Autor haftet nicht für Probleme.

### So geht’s

**Einstellungen → Ports und Treiber → com0com-Bereinigung → Bereinigen…** (die Taste ist nur aktiv, wenn com0com auf dem PC ist). Lies den Hinweis, setze den Haken bei *Gelesen und verstanden* und drücke **Bereinigung starten**. Windows fragt nach Administratorrechten: mit **Ja** bestätigen. Die Schritte erscheinen im selben Fenster von The Rigger; nach der Suche **Weiter** drücken (oder **Abbrechen**, um nichts zu ändern). Am Ende **Jetzt neu starten** oder **Schließen** drücken. Wenn das Fenster meldet, dass Geräte übrig sind, PC neu starten und die Bereinigung wiederholen.

## Meldungen und Ideen

Mit der Sprechblasen-Taste oben rechts meldest du ein Problem oder schlägst eine Idee vor, kostenlos und anonym.

- **Etwas funktioniert nicht**: beschreibe, was du gemacht hast, was du erwartet hast und was passiert ist; nenne Funkgerät und Programm. Meist das Protokoll des **letzten Starts** anhängen; tritt das Problem nur ab und zu auf, das der **letzten 7 Tage**.
- **Idee oder Wunsch**: eine neue Funktion, ein Programm zum Anbinden, ein Funkgerät. Alle Ideen werden geprüft; was vielen nützt, kommt in spätere Versionen.

**Anonymität.** Wir senden weder Name, Rufzeichen, E-Mail noch IP-Adresse. Vor dem Senden entfernt The Rigger Benutzername, PC-Name, persönliche Ordner und Netzwerkadressen aus dem Protokoll. Mit *Genau ansehen, was gesendet wird* prüfst du Wort für Wort, was rausgeht. Schreib keine persönlichen Daten in den Text.

Das Protokoll ist eine Textdatei, die The Rigger auf deinem Computer führt (die letzten 12 Starts); sie wird nur gesendet, wenn du es wählst.

## Häufige Probleme

**Das Funkgerät erscheint nicht.** Prüfe, ob es eingeschaltet und mit dem USB-Kabel verbunden ist, und drücke dann *Funkgeräte erneut suchen*. Hat ein anderes Programm den USB-Port des Geräts vor The Rigger geöffnet, schließe es: Den Port muss The Rigger haben. Bei Icom-Geräten sollte *CI-V USB Baud Rate* auf *Auto* oder einem normalen Wert stehen.

**Unter Windows erscheint das Funkgerät nicht und der Treiber fehlt.** *USB-Treiber automatisch* eingeschaltet lassen und die Frage von Windows bestätigen. Reicht das nicht, den Treiber des Kabelherstellers installieren und *Funkgeräte erneut suchen* drücken.

**Das Programm verbindet sich nicht.** Prüfe in diesem Handbuch die gewählte Verbindung und die Adresse. Dann auf der Karte des Funkgeräts *Verbindung testen* drücken: Es zeigt die genauen Adressen, und haben alle Zeilen ✓, funktioniert The Rigger und das Problem liegt in den Einstellungen des Programms.

**Die Lampe des Programms ist gelb.** Das Programm ist verbunden, fragt das Funkgerät aber nichts. Prüfe im Programm, ob die CAT-Steuerung aktiv ist (oft gibt es eine Taste *Connect* oder *Enable*).

**PTT funktioniert nicht.** Im Programm muss PTT auf **CAT** stehen (oder *PTT via Radio Command*), nicht auf RTS oder DTR.

**Ein OmniRig-Programm sagt, OmniRig fehlt.** The Rigger muss auf diesem Computer mindestens einmal geöffnet worden sein. Öffne es und starte dann das Programm neu.

**Ein Port wird schon von einem anderen Programm benutzt.** Belegt flrig, rigctld oder ein anderes Programm dieselben Ports, nimmt The Rigger den nächsten freien: Prüfe die genaue Adresse mit *Verbindung testen*.

**Ich will das Funkgerät mit dem Programm des Herstellers benutzen.** Schalte das Funkgerät in The Rigger mit seiner Ein-/Aus-Taste aus: Der USB-Port wird frei.

---

The Rigger · Software entwickelt von IU1MVI · frei und kostenlos für alle Funkamateure.
Die OmniRig-Kompatibilität nutzt die öffentliche Schnittstelle von OmniRig von Alex Shovkoplyas, VE3NEA (MIT-Lizenz). Hamlib, flrig, TCI und Ham Radio Deluxe sind Marken ihrer jeweiligen Inhaber. 73!
