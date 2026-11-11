# The Rigger — Manuale

## Cosa fa

The Rigger fa da centralino tra le tue radio e i programmi del computer. Di solito la porta seriale di una radio la può usare un solo programma alla volta. The Rigger è l'unico a parlare con la radio e a ogni programma dà un collegamento tutto suo, così WSJT-X, il logger, il programma da contest e gli altri lavorano insieme sulla stessa radio senza disturbarsi.

Funziona con più radio collegate allo stesso tempo, su Windows e macOS.

## Installazione

Scarica il file per il tuo sistema dalla pagina **Releases** del progetto su GitHub.

- **Windows**: avvia `The-Rigger-…-Setup.exe` e segui l'installazione. Se compare "PC protetto da Windows", scegli *Ulteriori informazioni › Esegui comunque*.
- **macOS**: apri `The-Rigger-…-Mac.pkg` (Mac con chip Apple) oppure `The-Rigger-…-Mac-Intel.pkg` (Mac Intel): The Rigger viene installato in Applicazioni. Se il Mac lo blocca: tasto destro sul file › *Apri*.

Da quel momento The Rigger si aggiorna da solo e parte da solo all'accensione del computer.

## Primo avvio

All'avvio compare la finestra di benvenuto con i crediti. Premi **Inizia · 73**.

Collega la radio con il cavo USB e accendila. Entro pochi secondi The Rigger la riconosce da solo: prova le porte USB, il protocollo e la velocità, e trova il modello. Non devi impostare niente.

## La finestra

La finestra mostra soltanto ciò che serve:

- **una riga per ogni radio**, con una luce: verde se la radio è collegata e risponde, grigia se è spenta o scollegata;
- **sotto ogni radio, i programmi collegati**, ciascuno con la sua luce: verde se sta parlando con la radio, gialla se ha la porta aperta ma è fermo.

Se sotto una radio leggi "nessun programma collegato", nessun programma la sta usando.

In alto ci sono tre pulsanti: **?** (come collegare i programmi e questo manuale), **⚙** (impostazioni) e **⏻** (chiude The Rigger).

Chiudere la finestra non spegne The Rigger: resta nell'area di notifica, vicino all'orologio, e i programmi restano collegati. Per riaprirla, clicca l'icona e scegli *Mostra finestra*.

## Collegare i programmi

Premi **?**: per ogni programma The Rigger ti dice esattamente cosa impostare, con la porta già scelta. Il pulsante **Copia** copia il nome della porta o l'indirizzo, così lo incolli nel programma.

Ci sono due tipi di collegamento:

1. **Hamlib NET rigctl**: per WSJT-X, JTDX, JS8Call, fldigi, CQRLOG e gli altri programmi che lo supportano. Nel programma scegli come radio *Hamlib NET rigctl* e come server l'indirizzo indicato (per esempio `127.0.0.1:4532`). Su questo indirizzo possono collegarsi tutti i programmi che vuoi.
2. **Porta seriale**: per Log4OM, N1MM Logger+, HRD, Logger32, DXLab Commander, MixW e tutti gli altri. Nel programma scegli come radio **il modello vero della tua radio** (per esempio Icom IC-7100) oppure **Kenwood TS-2000**, e la porta indicata. La velocità può essere qualsiasi, il controllo di flusso (handshake) nessuno, il PTT via CAT.
   - Su Windows le porte sono normali porte `COM`.
   - Su Mac si trovano in `/tmp/TheRigger/`, per esempio `/tmp/TheRigger/IC-7100-1`.

**Riconoscimento automatico**: ogni porta riconosce da sola il linguaggio del programma (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 oppure TS-2000). Se nel programma scegli il modello vero, i comandi arrivano direttamente alla radio e funzionano tutte le sue funzioni. Se scegli Kenwood TS-2000 funzionano le funzioni comuni: frequenza, modo, PTT e split. Con le radio Yaesu, la primissima volta che un programma impostato su TS-2000 usa una porta, il PTT può non partire alla prima trasmissione: dalla seconda in poi funziona, e la porta se lo ricorda.

Un programma per porta: The Rigger le assegna già in modo che non si scontrino. Ogni radio ha 4 porte, che puoi portare fino a 16 nelle impostazioni.

### Esempi

- **WSJT-X**: *Impostazioni › Radio*: Radio *Hamlib NET rigctl*, Server *127.0.0.1:4532*, PTT *CAT*.
- **Log4OM**: nella configurazione CAT scegli la radio *Kenwood TS-2000* sulla porta indicata per Log4OM. OmniRig non serve più.
- **Programmi che usano OmniRig** (Windows): non serve installare OmniRig. The Rigger si presenta al suo posto: nel programma scegli *OmniRig*, *Rig 1* è la prima radio accesa in The Rigger, *Rig 2* la seconda. Se il programma lo chiede quando The Rigger è chiuso, Windows lo apre da solo. (Interfaccia compatibile con OmniRig di Alex Shovkoplyas VE3NEA, licenza MIT.)
- **N1MM Logger+**: *Config › Configure Ports*: Radio *Kenwood TS-2000*, porta COM indicata per N1MM, velocità qualsiasi, *DTR* e *RTS* spenti.

## Impostazioni

- **Lingua**: automatica (quella del sistema) oppure una delle sette disponibili.
- **Avvio automatico**: The Rigger parte da solo all'accensione del computer.
- **Aggiornamenti automatici**: le nuove versioni si installano da sole, e solo quando nessun programma sta usando la radio.
- **Driver USB automatici**: installa da solo i driver USB che mancano.
- **Porte per radio**: da 1 a 16. Vale subito; le porte in uso non vengono mai tolte.

## Driver USB

- **Windows**: se colleghi una radio che non ha il driver, The Rigger scarica quello ufficiale firmato da Windows Update (o dal produttore) e lo installa. Windows chiede una conferma. Copre Silicon Labs (Icom, Yaesu, Kenwood), FTDI (Elecraft e molti cavi), WCH CH340 (Xiegu e cavi economici) e Prolific.
- **macOS**: i driver sono già inclusi nel sistema.

Le porte COM virtuali di Windows usano il driver gratuito *com0com*, che The Rigger installa da solo la prima volta (con una conferma di Windows).

## Radio supportate

- **Icom** e compatibili CI-V (anche Xiegu): IC-7100, IC-7300, IC-705, IC-7610, IC-9700, IC-905, IC-7760 e gli altri.
- **Kenwood**: TS-2000, TS-480, TS-590S/SG, TS-890S, TS-990S.
- **Elecraft**: K3, KX2, KX3, K4.
- **Yaesu** recenti: FT-991/A, FTDX10, FT-710, FTDX101, FT-891, FTDX3000 e gli altri.
- **Yaesu** classiche: FT-817, FT-818, FT-857, FT-897.
- Altre radio con comandi compatibili Kenwood: Lab599 TX-500, QRP Labs QDX/QMX e molte SDR.

## Problemi comuni

- **La radio non compare**: controlla che sia accesa e collegata con il cavo USB. Sulle Icom, nel menu della radio, la velocità *CI-V USB* deve essere su *Auto* o su un valore normale, e *CI-V USB Echo Back* può restare com'è.
- **Il programma non si collega**: premi **?** e controlla di aver scelto *Kenwood TS-2000* (o *Hamlib NET rigctl*) e la porta giusta. Due programmi non possono usare la stessa porta seriale.
- **La luce del programma è gialla**: il programma ha aperto la porta ma non interroga la radio. Controlla nel programma che il CAT sia attivo.
- **Windows non crea le porte COM**: su alcuni PC con Windows 11 il driver *com0com* può essere bloccato. In quel caso usa il collegamento *Hamlib NET rigctl*, che funziona sempre.

---

The Rigger · software sviluppato da IU1MVI · uso libero e gratuito per tutti gli OM. 73!
