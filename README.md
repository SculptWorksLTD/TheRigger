# The Rigger

Gestore CAT per radioamatori: collega tutte le radio USB e le condivide con tutti i programmi, contemporaneamente. Sostituisce OmniRig ed è fatto per non doverci mai mettere le mani.

**Windows · macOS** Si scarica dalla pagina [Releases](../../releases/latest).

## Cosa fa

- **Trova le radio da solo**: scansiona le porte USB e prova CI-V, CAT testuale e CAT binario Yaesu a tutte le velocità. Riconosce il modello. Se scolleghi e ricolleghi il cavo, la radio si ricollega da sola.
- **Tutte le radio insieme**, senza il limite di due di OmniRig.
- **Porte seriali virtuali create in automatico**: da 1 a 16 per ogni radio, modificabili al volo. Ogni porta **riconosce da sola il linguaggio del programma**: se scegli il modello vero della radio (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817) i comandi arrivano direttamente alla radio, con tutte le sue funzioni; se scegli **Kenwood TS-2000**, che quasi tutti i programmi conoscono, funzionano le funzioni comuni.
  - macOS: `/tmp/TheRigger/IC-7100-1` … senza driver e senza permessi di amministratore.
  - Windows: normali porte `COMx`. Al primo uso The Rigger installa da solo il driver firmato com0com (Windows chiede una conferma, una volta sola).
- **Driver USB automatici**: su Windows, se colleghi una radio senza driver, The Rigger scarica quello ufficiale firmato da Windows Update (o dal produttore) e lo installa. Una sola conferma. Su Mac i driver sono già nel sistema.
- **Server Hamlib rigctld** per ogni radio (`127.0.0.1:4532`, `4534`, …). Nei programmi scegli "Hamlib NET rigctl".
- **Nessun conflitto**: un solo processo parla con la radio, mette in coda i comandi e risponde a tutti dalla memoria. Il PTT ha la precedenza.
- **Si aggiorna da solo** dalle release GitHub, e solo quando nessun programma sta usando la radio.
- **Avvio automatico** al login, nell'area di notifica.

## Radio supportate

| Famiglia | Protocollo | Esempi |
|---|---|---|
| Icom (e compatibili CI-V: Xiegu…) | CI-V | IC-7100, IC-7300, IC-705, IC-7610, IC-9700, IC-905, IC-7760… |
| Kenwood | CAT testuale | TS-2000, TS-480, TS-590S/SG, TS-890S, TS-990S |
| Elecraft | CAT testuale | K3, KX2, KX3, K4 |
| Yaesu moderne | CAT testuale | FT-991/A, FTDX10, FT-710, FTDX101, FT-891, FTDX3000… |
| Yaesu classiche | CAT binario 5 byte | FT-817, FT-818, FT-857, FT-897 |
| Altre compatibili Kenwood | CAT testuale | Lab599 TX-500, QRP Labs QDX/QMX, molte SDR |

## Lingue e manuale

Interfaccia in 7 lingue: italiano, English, français, Deutsch, español, português, 日本語.

Manuale: [Italiano](docs/MANUALE_IT.md) · [English](docs/MANUAL_EN.md) · [Français](docs/MANUEL_FR.md) · [Deutsch](docs/HANDBUCH_DE.md) · [Español](docs/MANUAL_ES.md) · [Português](docs/MANUAL_PT.md) · [日本語](docs/MANUAL_JA.md)

## Uso

1. Scarica dalla pagina [Releases](../../releases/latest) il file per il tuo sistema:
   - **Windows**: `The-Rigger-…-Setup.exe`
   - **Mac con chip Apple**: `The-Rigger-…-Mac.pkg` · **Mac Intel**: `The-Rigger-…-Mac-Intel.pkg`
2. Installalo e collega la radio. Nient'altro.
3. Premi **?** nella finestra: per ogni programma ti dice cosa impostare, con la porta già assegnata. In generale, nel tuo programma scegli la radio **Kenwood TS-2000** sulla porta che vedi nella finestra (un clic la copia), oppure **Hamlib NET rigctl** con l'indirizzo `tcp`.

Su macOS, se il Mac blocca l'installer: tasto destro sul file → Apri (il programma non è ancora firmato da Apple).

## Licenza

The Rigger è un programma di Enrico Migliorati (IU1MVI). Tutti i diritti riservati.
L'uso è libero e gratuito per tutti gli OM; è vietato copiarlo, modificarlo, decompilarlo e ridistribuirlo senza il permesso dell'autore. Vedi [LICENSE](LICENSE).
