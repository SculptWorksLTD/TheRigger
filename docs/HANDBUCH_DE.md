# The Rigger — Handbuch

## Was es macht

The Rigger ist eine Vermittlungsstelle zwischen deinen Funkgeräten und den Programmen auf dem Computer. Normalerweise kann die serielle Schnittstelle eines Funkgeräts nur von einem Programm gleichzeitig benutzt werden. The Rigger spricht als einziges mit dem Funkgerät und gibt jedem Programm eine eigene Verbindung. So arbeiten WSJT-X, das Logprogramm, das Contestprogramm und alle anderen gemeinsam am selben Funkgerät, ohne sich zu stören.

Es verwaltet mehrere Funkgeräte gleichzeitig, unter Windows und macOS.

## Installation

Lade die Datei für dein System von der Seite **Releases** des Projekts auf GitHub herunter.

- **Windows**: `therigger-windows-amd64.exe` starten. Erscheint „Der Computer wurde durch Windows geschützt“, *Weitere Informationen › Trotzdem ausführen* wählen.
- **macOS**: `TheRigger-macOS-arm64.zip` (Mac mit Apple-Chip) oder `TheRigger-macOS-amd64.zip` (Intel-Mac) entpacken und *The Rigger* in den Ordner Programme ziehen. Beim ersten Mal: Rechtsklick › *Öffnen*.

Danach aktualisiert sich The Rigger selbst und startet automatisch mit dem Computer.

## Erster Start

Beim Start erscheint das Willkommensfenster mit den Credits. Drücke **Los geht's · 73**.

Schließe das Funkgerät mit dem USB-Kabel an und schalte es ein. Nach wenigen Sekunden erkennt The Rigger es selbst: Es probiert die USB-Anschlüsse, das Protokoll und die Geschwindigkeit aus und findet das Modell. Einzustellen gibt es nichts.

## Das Fenster

Das Fenster zeigt nur das Nötige:

- **eine Zeile pro Funkgerät** mit einer Leuchte: grün, wenn das Funkgerät verbunden ist und antwortet, grau, wenn es aus oder abgesteckt ist;
- **unter jedem Funkgerät die verbundenen Programme**, jedes mit eigener Leuchte: grün, wenn es mit dem Funkgerät spricht, gelb, wenn es den Port geöffnet hat, aber ruht.

Steht unter einem Funkgerät „kein Programm verbunden“, benutzt es gerade kein Programm.

Oben gibt es drei Knöpfe: **?** (so verbindest du die Programme, und dieses Handbuch), **⚙** (Einstellungen) und **⏻** (beendet The Rigger).

Das Schließen des Fensters beendet The Rigger nicht: Es bleibt im Infobereich neben der Uhr, und die Programme bleiben verbunden. Zum erneuten Öffnen auf das Symbol klicken und *Fenster anzeigen* wählen.

## Programme verbinden

Drücke **?**: Für jedes Programm sagt dir The Rigger genau, was einzustellen ist, mit bereits gewähltem Port. Der Knopf **Kopieren** kopiert den Portnamen oder die Adresse, damit du sie im Programm einfügen kannst.

Es gibt zwei Verbindungsarten:

1. **Hamlib NET rigctl**: für WSJT-X, JTDX, JS8Call, fldigi, CQRLOG und andere Programme, die es unterstützen. Im Programm als Funkgerät *Hamlib NET rigctl* und als Server die angezeigte Adresse wählen (zum Beispiel `127.0.0.1:4532`). Beliebig viele Programme können sich damit verbinden.
2. **Serieller Port**: für Log4OM, N1MM Logger+, HRD, Logger32, DXLab Commander, MixW und alle anderen. Im Programm als Funkgerät **das echte Modell deines Funkgeräts** (zum Beispiel Icom IC-7100) oder **Kenwood TS-2000** und den angezeigten Port wählen. Baudrate beliebig, kein Handshake, PTT über CAT.
   - Unter Windows sind es normale `COM`-Ports.
   - Auf dem Mac liegen sie in `/tmp/TheRigger/`, zum Beispiel `/tmp/TheRigger/IC-7100-1`.

**Automatische Erkennung**: Jeder Port erkennt das Protokoll des Programms von selbst (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 oder TS-2000). Wählst du im Programm das echte Modell, gehen die Befehle direkt ans Funkgerät und alle seine Funktionen stehen zur Verfügung. Wählst du Kenwood TS-2000, funktionieren die gemeinsamen Funktionen: Frequenz, Betriebsart, PTT und Split. Bei Yaesu-Geräten kann die PTT beim allerersten Mal, wenn ein auf TS-2000 eingestelltes Programm einen Port benutzt, beim ersten Durchgang ausbleiben: ab dem zweiten funktioniert sie, und der Port merkt es sich.

Ein Programm pro Port: The Rigger teilt sie schon so zu, dass sie sich nie in die Quere kommen. Jedes Funkgerät hat 4 Ports, in den Einstellungen bis zu 16.

### Beispiele

- **WSJT-X**: *Einstellungen › Funkgerät*: Funkgerät *Hamlib NET rigctl*, Netzwerkserver *127.0.0.1:4532*, PTT *CAT*.
- **Log4OM**: in der CAT-Konfiguration das Funkgerät *Kenwood TS-2000* am für Log4OM angezeigten Port wählen. OmniRig wird nicht mehr gebraucht.
- **N1MM Logger+**: *Config › Configure Ports*: Radio *Kenwood TS-2000*, der für N1MM angezeigte COM-Port, beliebige Geschwindigkeit, *DTR* und *RTS* aus.

## Einstellungen

- **Sprache**: automatisch (die des Systems) oder eine der sieben verfügbaren.
- **Automatisch starten**: The Rigger startet von selbst mit dem Computer.
- **Automatische Updates**: neue Versionen installieren sich selbst, und nur, wenn kein Programm das Funkgerät benutzt.
- **USB-Treiber automatisch**: fehlende USB-Treiber werden selbst installiert.
- **Ports pro Funkgerät**: von 1 bis 16. Gilt sofort; belegte Ports werden nie entfernt.

## USB-Treiber

- **Windows**: Schließt du ein Funkgerät ohne Treiber an, lädt The Rigger den offiziellen, signierten Treiber von Windows Update (oder vom Hersteller) und installiert ihn. Windows fragt einmal nach. Abgedeckt sind Silicon Labs (Icom, Yaesu, Kenwood), FTDI (Elecraft und viele Kabel), WCH CH340 (Xiegu und günstige Kabel) und Prolific.
- **macOS**: Die Treiber sind bereits Teil des Systems.

Die virtuellen COM-Ports unter Windows nutzen den kostenlosen Treiber *com0com*, den The Rigger beim ersten Mal selbst installiert (mit einer Windows-Bestätigung).

## Unterstützte Funkgeräte

- **Icom** und CI-V-kompatible (auch Xiegu): IC-7100, IC-7300, IC-705, IC-7610, IC-9700, IC-905, IC-7760 und weitere.
- **Kenwood**: TS-2000, TS-480, TS-590S/SG, TS-890S, TS-990S.
- **Elecraft**: K3, KX2, KX3, K4.
- Aktuelle **Yaesu**: FT-991/A, FTDX10, FT-710, FTDX101, FT-891, FTDX3000 und weitere.
- Klassische **Yaesu**: FT-817, FT-818, FT-857, FT-897.
- Andere Funkgeräte mit Kenwood-kompatiblen Befehlen: Lab599 TX-500, QRP Labs QDX/QMX und viele SDRs.

## Häufige Probleme

- **Das Funkgerät erscheint nicht**: Prüfe, ob es eingeschaltet und mit dem USB-Kabel verbunden ist. Bei Icom muss die Baudrate *CI-V USB* im Menü des Funkgeräts auf *Auto* oder einem normalen Wert stehen; *CI-V USB Echo Back* kann bleiben, wie es ist.
- **Ein Programm verbindet sich nicht**: Drücke **?** und prüfe, ob du *Kenwood TS-2000* (oder *Hamlib NET rigctl*) und den richtigen Port gewählt hast. Zwei Programme können nicht denselben seriellen Port nutzen.
- **Die Leuchte eines Programms ist gelb**: Das Programm hat den Port geöffnet, fragt das Funkgerät aber nicht ab. Prüfe, ob CAT im Programm aktiviert ist.
- **Windows erstellt die COM-Ports nicht**: Auf manchen PCs mit Windows 11 kann der Treiber *com0com* blockiert sein. Nutze dann die Verbindung *Hamlib NET rigctl*, die immer funktioniert.

---

The Rigger · Software entwickelt von IU1MVI · frei und kostenlos für alle Funkamateure. 73!
