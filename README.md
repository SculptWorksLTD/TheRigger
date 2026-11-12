# The Rigger

Gestore CAT per radioamatori: collega tutte le radio USB e le condivide con tutti i programmi, contemporaneamente. Sostituisce OmniRig ed è fatto per non doverci mai mettere le mani.

**Windows · macOS** Si scarica dalla pagina [Releases](../../releases/latest).

## Cosa fa

- **Trova le radio da solo**: scansiona le porte USB e prova CI-V, CAT testuale e CAT binario Yaesu a tutte le velocità. Riconosce il modello. Se scolleghi e ricolleghi il cavo, la radio si ricollega da sola.
- **Tutte le radio insieme**, senza il limite di due di OmniRig.
- **Tutti i collegamenti che usano i programmi, insieme, per ogni radio**:
  - **Hamlib NET rigctl** (`127.0.0.1:4532`, `4534`…): WSJT-X, JTDX, JS8Call, FreeDV, Gpredict, CQRLOG, MacLoggerDX…
  - **flrig** (`127.0.0.1:12345`, `12346`…): fldigi, QLog, Not1MM, HAMRS, Wavelog/Cloudlog (WaveLogGate)…
  - **TCI** (`127.0.0.1:40001`, `40002`…): N1MM Logger+, JTDX, MSHV, Log4OM…
  - **OmniRig** (Windows, Rig 1 e Rig 2): Log4OM, DXLog.net, HDSDR, SDR Console, CW Skimmer, Swisslog… senza installare OmniRig.
  - **Ham Radio Deluxe** (`127.0.0.1:7809`): HRD Logbook, DM-780…
  - **CAT via rete** (`127.0.0.1:4600`…): come la porta seriale della radio, per N1MM Logger+ e simili.
  - **Porte seriali virtuali** (Mac e Linux, `/tmp/TheRigger/…`): ogni porta riconosce da sola il linguaggio del programma (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 o Kenwood TS-2000).
- **La finestra dice come impostare ogni programma**: più di 40 programmi, con il menu dove si imposta e l'indirizzo già pronto da copiare.
- **Driver USB automatici**: su Windows, se colleghi una radio senza driver, The Rigger scarica quello ufficiale firmato e lo installa. Su Mac i driver sono già nel sistema.
- **Nessun conflitto**: un solo processo parla con la radio, mette in coda i comandi e risponde a tutti dalla memoria. Il PTT ha la precedenza.
- **Leggerissimo**: un solo programma nativo di pochi MB.
- **Si aggiorna da solo** dalle release GitHub, all'avvio, e si riavvia da solo.

## Radio supportate

| Famiglia | Protocollo | Esempi |
|---|---|---|
| Icom (e compatibili CI-V: Xiegu…) | CI-V | IC-7100, IC-7300, IC-705, IC-7610, IC-9700, IC-905, IC-7760, IC-7851, IC-9100, IC-7000, IC-718, IC-706… |
| Kenwood | CAT testuale | TS-2000, TS-480, TS-590S/SG, TS-890S, TS-990S, TS-870S, TS-570… |
| Elecraft | CAT testuale | K3, KX2, KX3, K4 |
| Yaesu moderne | CAT testuale | FTX-1, FT-991/A, FTDX10, FT-710, FTDX101, FT-891, FTDX3000, FTDX5000… |
| Yaesu classiche | CAT binario 5 byte | FT-817, FT-818, FT-857, FT-897 |
| FlexRadio | CAT di SmartSDR | serie 6000 |
| Altre compatibili Kenwood | CAT testuale | Lab599 TX-500, QRP Labs QDX/QMX, (tr)uSDX, molte SDR |

## Lingue e manuale

Interfaccia in 7 lingue: italiano, English, français, Deutsch, español, português, 日本語.

Manuale: [Italiano](docs/MANUALE_IT.md) · [English](docs/MANUAL_EN.md) · [Français](docs/MANUEL_FR.md) · [Deutsch](docs/HANDBUCH_DE.md) · [Español](docs/MANUAL_ES.md) · [Português](docs/MANUAL_PT.md) · [日本語](docs/MANUAL_JA.md)

## Uso

1. Scarica dalla pagina [Releases](../../releases/latest) il file per il tuo sistema:
   - **Windows**: `The-Rigger-…-Windows.zip` (apri lo zip e avvia `The Rigger.exe`)
   - **Mac con chip Apple**: `The-Rigger-…-Mac.pkg` · **Mac Intel**: `The-Rigger-…-Mac-Intel.pkg`
2. Collega la radio. Nient'altro.
3. Apri la scheda **Programmi**: per ogni programma c'è il collegamento da usare, il menu dove impostarlo e l'indirizzo da copiare.

Su macOS, se il Mac blocca l'installer: tasto destro sul file → Apri.

## Licenza

The Rigger è un programma di Enrico Migliorati (IU1MVI). Tutti i diritti riservati.
L'uso è libero e gratuito per tutti gli OM; è vietato copiarlo, modificarlo, decompilarlo e ridistribuirlo senza il permesso dell'autore. Vedi [LICENSE](LICENSE).

La compatibilità OmniRig usa l'interfaccia pubblica (type library) di OmniRig di Alex Shovkoplyas, VE3NEA, distribuita con licenza MIT.
