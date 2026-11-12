# The Rigger — Manuale

## Cosa fa

The Rigger fa da centralino tra le tue radio e i programmi del computer.

Di solito la porta CAT di una radio la può usare un solo programma alla volta: se WSJT-X la apre, il logger non la trova più. Con The Rigger è diverso. The Rigger è l'unico a parlare con la radio e offre a ogni programma un collegamento suo. Così WSJT-X, il logger, il programma da contest, CWIU1MVI, il programma SDR e gli altri lavorano insieme sulla stessa radio senza disturbarsi.

In breve:

- **trova le radio da solo**: colleghi il cavo USB e la radio compare, senza scegliere porte, velocità o modelli;
- **più radio insieme**: ognuna ha i suoi collegamenti;
- **tutti i collegamenti che usano i programmi**: Hamlib, flrig, TCI, OmniRig (Windows), Ham Radio Deluxe, CAT via rete e porte seriali (Mac e Linux);
- **si aggiorna da solo** e parla 7 lingue.

The Rigger non trasmette mai di sua iniziativa e non cambia nulla nella radio: esegue solo quello che chiedono i programmi.

## Installazione

Scarica il file per il tuo sistema dalla pagina **Releases** del progetto su GitHub (SculptWorksLTD/TheRigger).

### Windows

1. Scarica `The-Rigger-…-Windows.zip`.
2. Apri lo zip e trascina **The Rigger.exe** in una cartella tua, per esempio *Documenti › The Rigger*. Non lasciarlo dentro lo zip né nella cartella Download temporanea.
3. Fai doppio clic su **The Rigger.exe**.
4. Se compare *PC protetto da Windows*, premi **Ulteriori informazioni** e poi **Esegui comunque**. Succede solo la prima volta.

Non serve installare altro: niente OmniRig, niente com0com, niente Hamlib.

### macOS

1. Scarica `The-Rigger-…-Mac.pkg` se il tuo Mac ha un chip Apple (M1, M2, M3, M4), oppure `The-Rigger-…-Mac-Intel.pkg` se è un Mac Intel.
2. Apri il file e segui l'installazione: The Rigger finisce in **Applicazioni**.
3. Se il Mac dice che non può aprirlo: tasto destro sul file › **Apri**, oppure *Impostazioni di Sistema › Privacy e sicurezza › Apri comunque*.

Da quel momento The Rigger si aggiorna da solo.

## Primo avvio

All'avvio compare la finestra di benvenuto con i crediti: premi **Inizia · 73**.

Collega la radio con il cavo USB e accendila. Entro pochi secondi The Rigger la trova: prova le porte USB, il protocollo (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817) e la velocità, poi riconosce il modello. Non devi impostare niente.

Quando la radio compare nella scheda **Radio** è pronta: per impostare ogni programma guarda il capitolo **Istruzioni per i programmi** di questo manuale.

## La finestra

La finestra è divisa in tre schede, che scegli in alto al centro:

- **Radio**: le radio trovate, con frequenza, modo e programmi collegati;
- **Manuale**: questo manuale, con l'indice a sinistra;
- **Impostazioni**: lingua, avvio, aggiornamenti, porte e informazioni.

In alto a destra ci sono due tasti:

- **Riduci** (freccia verso il basso): nasconde la finestra. Su Mac The Rigger resta nella barra in alto, vicino all'orologio: clicca l'icona e scegli *Mostra The Rigger*. Su Windows la finestra va nella barra delle applicazioni.
- **Spegni** (⏻): chiude The Rigger. I programmi collegati perdono la radio finché non lo riapri.

In basso c'è la barra di stato: la luce è verde quando almeno una radio è collegata, gialla quando c'è un avviso. Il tasto con la freccia circolare cerca di nuovo le radio. A destra trovi la versione.

La finestra si può ingrandire e rimpicciolire trascinando i bordi.

## Scheda Radio

Ogni radio trovata ha una scheda tutta sua.

### Intestazione

- **Tasto di accensione** (a sinistra): accende o spegne la radio *dentro The Rigger*. Spenta, The Rigger chiude la sua porta USB e la lascia libera, per esempio per il programma del costruttore o per aggiornare il firmware. Premi di nuovo per riprenderla. La radio vera non si spegne.
- **Nome**: il modello, con un numero se hai due radio uguali (per esempio *IC-7300 2*).
- **Stato**: *collegata* (risponde), *scollegata* (cavo staccato o radio spenta) oppure *spenta* (spenta in The Rigger).

### Display

- **Frequenza** del VFO in uso, in grande, con il **modo** accanto (USB, LSB, CW, CW-R, RTTY, AM, FM, USB-D, LSB-D, FM-D).
- **A** e **B**: quale VFO è in uso.
- **SPLIT**: acceso quando la radio è in split.
- **TX**: diventa rosso quando la radio trasmette.
- Sotto: la frequenza dell'altro VFO e la barra dello **S-meter**.

Il display segue la radio in tempo reale, sia quando giri la manopola sia quando un programma cambia frequenza.

### Dati della radio

La riga grigia dice modello, porta USB, velocità e, se la radio è accesa in The Rigger, il suo numero (**Rig 1**, **Rig 2**…). Il numero serve per OmniRig e Ham Radio Deluxe.

### Programmi collegati

L'elenco dei programmi che stanno usando questa radio, ognuno con una luce:

- **verde**: il programma sta parlando con la radio;
- **gialla**: il programma è collegato ma in questo momento non chiede niente.

A destra c'è il collegamento che usa (per esempio `tcp:4532`, `flrig`, `TCI`, una porta seriale). Cliccalo per copiarne l'indirizzo.

### Pulsanti

- **Prova collegamento**: fa finta di essere un programma e legge la frequenza attraverso ogni collegamento (porta seriale, Hamlib, flrig, CAT via rete, TCI). Ogni riga con **✓** funziona, ogni riga con **✗** ha un problema. La prova legge soltanto: non trasmette e non cambia nulla.

### Cerca di nuovo le radio

Il tasto **Cerca di nuovo le radio** (in alto a destra della scheda, oppure la freccia circolare in basso) ricontrolla subito tutte le porte USB. Usalo dopo aver acceso una radio che The Rigger non vedeva, o dopo aver chiuso un programma che teneva occupata la porta.

## I collegamenti

The Rigger apre per ogni radio tutti questi collegamenti insieme. Ogni programma usa quello che conosce, e più programmi possono usare lo stesso collegamento.

| Collegamento | Indirizzo (prima radio) | Seconda radio | Sistemi |
|---|---|---|---|
| Hamlib NET rigctl | 127.0.0.1:4532 | 127.0.0.1:4534 | tutti |
| flrig | 127.0.0.1:12345 | 127.0.0.1:12346 | tutti |
| TCI | 127.0.0.1:40001 | 127.0.0.1:40002 | tutti |
| CAT via rete (Kenwood TS-2000) | 127.0.0.1:4600 | 127.0.0.1:4601 | tutti |
| Ham Radio Deluxe | 127.0.0.1:7809 (radio 1) | stessa porta, radio 2 | tutti |
| OmniRig | Rig 1 | Rig 2 | Windows |
| Porte seriali | /tmp/TheRigger/… | /tmp/TheRigger/… | Mac e Linux |

Se una porta è già occupata da un altro programma (per esempio flrig vero o rigctld già aperti), The Rigger usa la successiva libera: l'indirizzo esatto lo vedi premendo *Prova collegamento* nella scheda della radio.

### Hamlib NET rigctl

È il collegamento di WSJT-X, JTDX, JS8Call, FreeDV, Gpredict, CQRLOG, KLog, MacLoggerDX, Pat e di tutti i programmi che usano Hamlib.

Nel programma scegli come radio **Hamlib NET rigctl** (in alcuni programmi *NET rigctl* o *rigctld*, modello Hamlib numero 2) e come server l'indirizzo indicato, per esempio `127.0.0.1:4532`. Come PTT scegli **CAT**.

### flrig

The Rigger risponde esattamente come flrig (W1HKJ). È il collegamento di fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog e Cloudlog), WFDlogger e di tutti i programmi che hanno la voce *FLRig*.

Nel programma scegli **FLRig**, indirizzo `127.0.0.1` e porta `12345` (seconda radio `12346`). Non serve installare flrig.

### TCI

The Rigger risponde come un apparato TCI (il protocollo di Expert Electronics). Lo usano N1MM Logger+, JTDX, MSHV, Log4OM, QLog, Swisslog, DXLog e altri.

Nel programma scegli **TCI** e l'indirizzo `127.0.0.1:40001` (seconda radio `40002`). Il TCI di The Rigger porta frequenze, modo, PTT e split; l'audio resta sulla scheda audio della radio come sempre.

### OmniRig (solo Windows)

The Rigger prende il posto di OmniRig: **non devi installare OmniRig**. Nel programma scegli **OmniRig** e poi **Rig 1** per la prima radio accesa in The Rigger o **Rig 2** per la seconda.

Funziona con Log4OM, DXLog.net, HDSDR, SDR Console, CW Skimmer, UcxLog, Swisslog, MixW, QARTest, VarAC e con tutti i programmi che usano OmniRig, sia a 32 che a 64 bit. Se un programma chiede OmniRig quando The Rigger è chiuso, Windows apre The Rigger da solo, ridotto.

Se hai anche l'OmniRig vero installato, i programmi trovano comunque The Rigger, tranne quelli avviati *come amministratore*: avviali normalmente. Non lasciare aperti tutti e due insieme sulla stessa radio.

### Ham Radio Deluxe

The Rigger risponde come *HRD Rig Control*. Serve a HRD Logbook, DM-780 e ai programmi che si collegano a Ham Radio Deluxe (anche WSJT-X e JTDX con la scelta *Ham Radio Deluxe*).

Nel programma imposta il server `127.0.0.1` porta `7809`. Le radio si chiamano come in The Rigger e sono numerate 1, 2, 3… nell'ordine della scheda Radio.

### CAT via rete (TCP)

Un indirizzo che si comporta come la porta seriale della radio. Va bene per i programmi che sanno collegarsi a una radio via TCP, come N1MM Logger+ e MSHV.

Nel programma scegli come radio **il modello vero** (per esempio *IC-7100*) oppure **Kenwood TS-2000**, e come porta l'indirizzo indicato, per esempio `127.0.0.1:4600`. Il PTT va su **CAT**.

### Porte seriali (Mac e Linux)

Per i programmi che vogliono per forza una porta seriale, The Rigger crea per ogni radio alcune porte virtuali, per esempio `/tmp/TheRigger/IC-7100-1`, `/tmp/TheRigger/IC-7100-2`…

Nel programma scegli come radio il **modello vero** oppure **Kenwood TS-2000**, la porta indicata, velocità **qualsiasi**, handshake **nessuno**, PTT **CAT**.

Ogni porta riconosce da sola il linguaggio del programma: Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 oppure TS-2000. Se scegli il modello vero arrivano alla radio tutti i comandi, anche quelli speciali. Con TS-2000 funzionano frequenza, modo, PTT e split.

Un programma per porta: The Rigger dà a ogni programma una porta diversa. Il numero di porte per radio si cambia nelle Impostazioni (da 1 a 16).

Su Windows The Rigger non crea porte COM virtuali: usa gli altri collegamenti, che non hanno bisogno di driver.

### CWIU1MVI

CWIU1MVI trova The Rigger da solo: nell'elenco delle radio di CWIU1MVI scegli **The Rigger · nome della radio**. Non c'è altro da impostare.

## Istruzioni per i programmi

Qui i passaggi per i programmi più usati. Gli indirizzi sono quelli della prima radio: per le altre radio guarda la tabella nel capitolo *I collegamenti*.

### WSJT-X, JTDX, JS8Call, WSJT-Z

1. *File › Settings › Radio*.
2. **Rig**: *Hamlib NET rigctl*.
3. **Network Server**: `127.0.0.1:4532`.
4. **PTT Method**: *CAT*.
5. **Mode**: *Data/Pkt* se vuoi che la radio vada in USB-D, altrimenti *USB*.
6. **Split Operation**: *Rig* o *Fake It*, come preferisci.
7. Premi **Test CAT**: diventa verde. Poi **OK**.

### fldigi

1. *Configure › Config dialog › Rig Control › flrig*.
2. Spunta **Connect to flrig**, indirizzo `127.0.0.1`, porta `12345`.
3. Togli la spunta da *Hamlib* e *RigCAT* se c'è.
4. **Save** e chiudi: la frequenza di fldigi segue la radio.

### Log4OM 2 (Windows)

1. *Settings › CAT interface*.
2. **CAT engine**: *OmniRig*. **Rig**: *Rig 1* (oppure *Rig 2* per la seconda radio).
3. Spunta **Autostart** e premi **Connect**.

Non serve installare OmniRig. In alternativa puoi scegliere *Hamlib* › *Connect to active HAMLIB interface* con porta `4532`.

### N1MM Logger+ (Windows)

1. *Config › Configure Ports, Mode Control, Winkey, etc… › Hardware*.
2. Sulla riga di una porta scegli **TCP**, **Radio**: *IC-7100* (il modello vero) oppure *Kenwood TS-2000*.
3. Premi **Set** e scrivi l'indirizzo `127.0.0.1` porta `4600`.
4. **PTT via Radio Command** (*Radio PTT via command*) acceso.
5. **OK**: in basso a sinistra compare la frequenza.

In alternativa N1MM può usare **TCI** con `127.0.0.1:40001`.

### HRD Logbook e DM-780 (Windows)

Nella finestra di collegamento alla radio scegli il server `127.0.0.1` porta `7809` e premi **Connect**. Non serve aprire *HRD Rig Control*: risponde The Rigger.

### QLog

1. *Settings › Equipment › Rig*, aggiungi una radio.
2. **Interface**: *FLRig*, host `127.0.0.1`, porta `12345` (oppure *Hamlib* › *NET rigctl* con `127.0.0.1:4532`).
3. Salva e collega la radio dal menu *Equipment*.

### MacLoggerDX (Mac)

1. *Prefs › Radio*.
2. Scegli **Hamlib rigctld**, host `127.0.0.1`, porta `4532`.
3. Attiva **Radio VFO** nella finestra di controllo.

In alternativa scegli il modello vero della radio e una porta di `/tmp/TheRigger/`.

### RUMlogNG e SkookumLogger (Mac)

Nelle preferenze della radio scegli il **modello vero** della radio (o Kenwood TS-2000) e una porta di `/tmp/TheRigger/`, per esempio `/tmp/TheRigger/IC-7100-2`, velocità qualsiasi.

### Wavelog e Cloudlog (con WaveLogGate)

In WaveLogGate apri *Config › Radio*, scegli **FLRig**, host `127.0.0.1`, porta `12345`, e salva. Wavelog riceverà frequenza e modo e potrà cambiarli.

### HAMRS, Not1MM, WFDlogger

Nelle impostazioni del controllo radio scegli **FLRig**, host `127.0.0.1`, porta `12345`.

### MSHV

*Options › Radio and Network Configuration*: scegli **TCI** e l'indirizzo `127.0.0.1:40001`.

### HDSDR, SDR Console, CW Skimmer (Windows)

Scegli **OmniRig** (in HDSDR *Options › CAT to Radio (Omni-Rig)*, in SDR Console *Radio › External Radio*, in CW Skimmer *Setup › Radio*) e poi **Rig 1**.

### Gpredict

*Edit › Preferences › Interfaces › Radios › Add new*: host `localhost`, porta `4532`, tipo *RX + TX* o quello che ti serve.

### CQRLOG (Linux)

*Preferences › TRX control*: togli la spunta da *Run rigctld*, **Rig model**: *2 Hamlib NET rigctl*, **Device**: `127.0.0.1:4532`.

### VarAC (Windows)

*Settings › Rig control*: scegli **OmniRig** e *Rig 1*, oppure **Hamlib (rigctld)** con `127.0.0.1` porta `4532`.

### DXLab Commander (Windows)

Commander non sa usare OmniRig né Hamlib, ma sa parlare via rete con Thetis: The Rigger risponde come Thetis.

1. *Config › Ports*, pannello della radio: **Model**: *Thetis*.
2. Spunta **Communicate via TCP**, **IP Address** `127.0.0.1`, **IP Port** `4600` (seconda radio `4601`).
3. Chiudi la configurazione: Commander mostra la frequenza, e con lui DXKeeper, SpotCollector e il resto della suite DXLab.

### N3FJP ACLog e programmi contest N3FJP (Windows)

I programmi N3FJP non sanno condividere la radio senza una porta COM, ma hanno un'interfaccia di rete: The Rigger la usa da solo per mandare banda, modo e frequenza della prima radio accesa.

1. *Settings › Rig Interface*: scegli **None**.
2. *Settings › Application Program Interface*: spunta **TCP API Enabled (Server)**, porta `1100`.
3. Fatto: i campi banda, modo e frequenza si compilano da soli. The Rigger non registra mai QSO al posto tuo.

ACLog in questo modo non può cambiare la frequenza della radio (per esempio cliccando uno spot).

### MMSSTV, MMTTY e MMVARI (Windows)

- **MMSSTV**: *Option › Setup › TX › Radio command*, scegli **OmniRig** e *Rig 1*.
- **MMTTY e MMVARI**: scarica il plugin gratuito **HRDPTT.mmr** (fa parlare i programmi MM con Ham Radio Deluxe), copialo nella cartella del programma, poi *Option › Setup › TX › Radio command* e come porta scegli **HRDPTT**. The Rigger risponde come Ham Radio Deluxe, quindi il PTT passa da The Rigger.

### Programmi che vogliono solo una porta COM (Windows)

Logger32, Win-Test, Winlink Express e SatPC32 conoscono solo le porte COM, che su Windows richiedono un driver firmato da Microsoft: con questi programmi The Rigger per ora non si può usare. Ecco con cosa sostituirli, tutti gratuiti o già collegabili a The Rigger:

| Invece di | Usa | Collegamento |
|---|---|---|
| Logger32 | Log4OM 2, Swisslog, UcxLog, QLog o la suite DXLab | OmniRig, Hamlib, flrig o Thetis (Commander) |
| Win-Test | N1MM Logger+, DXLog.net o QARTest | CAT via rete / TCI, OmniRig |
| Winlink Express | Pat Winlink, oppure Winlink Express senza controllo radio (frequenza a mano) | Hamlib |
| SatPC32 | Gpredict | Hamlib |

### Programmi non in elenco

Guarda nel programma quale collegamento conosce:

- se ha *Hamlib*, *NET rigctl* o *rigctld* usa Hamlib (`127.0.0.1:4532`);
- se ha *FLRig* usa flrig (`127.0.0.1:12345`);
- se ha *TCI* usa TCI (`127.0.0.1:40001`);
- se ha *OmniRig* (Windows) usa OmniRig *Rig 1*;
- se ha *Ham Radio Deluxe* usa `127.0.0.1:7809`;
- se si collega a una radio via TCP usa la CAT via rete (`127.0.0.1:4600`) con il modello vero o Kenwood TS-2000;
- se vuole solo una porta seriale (Mac e Linux) usa una porta di `/tmp/TheRigger/`.

## Più radio insieme

The Rigger gestisce tutte le radio che colleghi. Ogni radio ha:

- i suoi indirizzi (porte diverse, vedi la tabella nel capitolo *I collegamenti*);
- il suo numero (**Rig 1**, **Rig 2**…) per OmniRig e Ham Radio Deluxe, in base all'ordine nella scheda Radio contando solo le radio accese.

Se hai due radio dello stesso modello si chiamano per esempio *IC-7300* e *IC-7300 2*.

## Spegnere una radio in The Rigger

Il tasto di accensione nella scheda di una radio la spegne **solo dentro The Rigger**: la porta USB si libera e i collegamenti di quella radio si chiudono. Serve quando un altro programma deve usare la radio direttamente, per esempio il programma del costruttore o un aggiornamento del firmware.

The Rigger ricorda la scelta anche dopo un riavvio. Premi di nuovo il tasto per riprendere la radio.

## Impostazioni

### Generale

- **Lingua**: *Automatica* usa la lingua del sistema; altrimenti scegli fra italiano, inglese, francese, tedesco, spagnolo, portoghese e giapponese. Cambia subito tutta la finestra, il manuale e le istruzioni dei programmi.
- **Avvio automatico**: The Rigger si apre da solo quando accendi il computer, così le radio sono pronte prima dei programmi.

### Aggiornamenti

- **Aggiornamenti automatici**: a ogni avvio The Rigger controlla se c'è una versione nuova. Se c'è, la scarica, la installa e si riavvia da solo in pochi secondi; i programmi si ricollegano da soli.
- **Cerca aggiornamenti**: controlla subito. La riga sotto dice cosa succede (*hai già l'ultima versione*, *scarico l'aggiornamento…*).

Le piccole correzioni della finestra arrivano in un attimo anche senza riavviare.

### Porte e driver

- **Porte seriali per radio** (Mac e Linux): quante porte virtuali creare per ogni radio, da 1 a 16. Vale subito; le porte che un programma sta usando non vengono mai tolte.
- **Driver USB automatici** (Windows): se colleghi una radio senza driver, The Rigger installa quello ufficiale (vedi *Driver USB*).

### Informazioni

Versione, crediti e il pulsante per offrire un caffè a IU1MVI con PayPal.

## Driver USB

- **Windows**: se colleghi una radio che non ha il driver, The Rigger scarica quello ufficiale firmato (da Windows Update o dal produttore) e lo installa. Windows chiede una conferma una volta sola. Copre Silicon Labs CP210x (Icom, Yaesu, Kenwood), FTDI (Elecraft e molti cavi), WCH CH340 (Xiegu e cavi economici) e Prolific.
- **macOS**: i driver sono già nel sistema, non serve niente.

## Radio supportate

| Marca | Modelli |
|---|---|
| Icom | IC-7100, IC-7300, IC-7300MK2, IC-705, IC-7610, IC-7760, IC-9700, IC-905, IC-7851, IC-7800, IC-7700, IC-7600, IC-7410, IC-7200, IC-7000, IC-9100, IC-746PRO, IC-7400, IC-756 (tutte), IC-718, IC-706 (tutte), IC-703, IC-910H e le altre CI-V, ricevitori IC-R8600, IC-R75, IC-R30 |
| Xiegu | G90, X6100, X6200, X5105, X108G (protocollo Icom CI-V) |
| Kenwood | TS-890S, TS-990S, TS-590S/SG, TS-2000, TS-480, TS-870S, TS-570, TS-850, TS-450S, TS-690S e le altre con comandi CAT |
| Elecraft | K3, K3S, K4, KX2, KX3 |
| Yaesu | FTX-1, FTDX10, FTDX101D/MP, FT-710, FT-991/991A, FT-891, FTDX3000, FTDX5000, FTDX1200, FT-950, FT-2000, FT-450/450D, FTDX9000 |
| Yaesu classiche | FT-817, FT-818, FT-857, FT-897 |
| FlexRadio | serie 6000 attraverso la porta CAT di SmartSDR |
| Compatibili Kenwood | Lab599 TX-500, QRP Labs QDX/QMX, (tr)uSDX, Malachite e molte SDR |

Le Icom con l'indirizzo CI-V cambiato nel menu vengono trovate lo stesso.

## Pulizia com0com (Windows)

### Cosa fa

Mostra ogni passo nella finestra di The Rigger. Cerca com0com, il driver gratuito che crea coppie di porte COM virtuali, e poi: lo disinstalla, toglie tutte le sue porte virtuali (anche quelle “fantasma” che Gestione dispositivi non mostra), toglie il suo driver da Windows e libera i numeri COM che quelle porte tenevano occupati. Prima di toccare qualcosa ti mostra cosa ha trovato e chiede conferma; alla fine propone il riavvio.

### Perché usarla

Col tempo com0com lascia decine o centinaia di porte virtuali e numeri COM prenotati: le nuove porte USB prendono numeri altissimi, Windows mostra errori a ripetizione, i programmi radio si confondono e il PC rallenta. The Rigger non usa porte COM virtuali (i programmi si collegano con OmniRig, Hamlib, flrig, TCI, HRD o CAT via rete: vedi il Manuale), quindi com0com non serve più.

### Rischi

Serve il permesso di amministratore. I programmi che usano com0com smettono di funzionare con quelle porte: per esempio uno splitter di porte o due programmi collegati fra loro con le porte virtuali. Le porte COM vere (radio, cavi USB-seriale) non vengono toccate. L’operazione non si annulla: se ti servisse di nuovo, com0com va reinstallato. Chiudi prima i programmi che usano le porte COM. La usi a tuo rischio: l’autore non risponde di eventuali problemi.

### Come si usa

**Impostazioni → Porte e driver → Pulizia com0com → Pulisci…** (il tasto è attivo solo se com0com è sul PC). Leggi l’avviso, spunta *Ho letto e ho capito* e premi **Avvia la pulizia**. Windows chiede il permesso di amministratore: rispondi **Sì**. I passi compaiono nella stessa finestra di The Rigger; dopo la ricerca premi **Procedi** (o **Annulla** per non toccare niente). Alla fine puoi premere **Riavvia ora** oppure **Chiudi**. Se la finestra dice che restano dei dispositivi, riavvia il PC e ripeti la pulizia.

## Segnalazioni e idee

Il tasto con il fumetto, in alto a destra, serve per segnalare un problema o proporre un'idea, gratis e in forma anonima.

- **Qualcosa non va**: scrivi cosa stavi facendo, cosa ti aspettavi e cosa è successo; indica radio e programma. Di solito conviene allegare il diario dell'**ultimo avvio**; se il problema capita ogni tanto, quello degli **ultimi 7 giorni**.
- **Idea o richiesta**: una funzione nuova, un programma da collegare, una radio da aggiungere. Le idee si valutano tutte; quelle utili a molti entrano nelle versioni successive.

**Anonimato.** Non inviamo nome, nominativo, email né indirizzo IP. Prima dell'invio The Rigger toglie dal diario nome utente, nome del PC, cartelle personali e indirizzi di rete. Con *Vedi esattamente cosa viene inviato* controlli parola per parola cosa parte. Non scrivere dati personali nel testo.

Il diario è un file di testo che The Rigger tiene sul tuo computer (gli ultimi 12 avvii); parte solo se lo scegli tu.

## Problemi comuni

**La radio non compare.** Controlla che sia accesa e collegata con il cavo USB, poi premi *Cerca di nuovo le radio*. Se un altro programma ha aperto la porta USB della radio prima di The Rigger, chiudilo: la porta deve averla The Rigger. Sulle Icom la velocità *CI-V USB Baud Rate* va su *Auto* o su un valore normale.

**Su Windows la radio non compare e manca il driver.** Lascia attivo *Driver USB automatici* e conferma la richiesta di Windows. Se non basta, installa il driver del produttore del cavo e premi *Cerca di nuovo le radio*.

**Il programma non si collega.** Controlla in questo manuale di aver scelto il collegamento giusto e l'indirizzo. Poi premi *Prova collegamento* nella scheda della radio: mostra gli indirizzi esatti e, se tutte le righe hanno ✓, The Rigger funziona e il problema è nell'impostazione del programma.

**La luce del programma è gialla.** Il programma è collegato ma non chiede niente alla radio. Controlla nel programma che il controllo CAT sia attivo (spesso c'è un tasto *Connect* o *Enable*).

**Il PTT non funziona.** Nel programma il PTT deve essere su **CAT** (o *PTT via Radio Command*), non su RTS o DTR.

**Un programma OmniRig dice che OmniRig non c'è.** The Rigger deve essere stato aperto almeno una volta su questo computer. Aprilo, poi riapri il programma.

**Una porta è già usata da un altro programma.** Se hai flrig, rigctld o un altro programma che occupa le stesse porte, The Rigger prende la successiva libera: guarda l'indirizzo esatto con *Prova collegamento*.

**Voglio usare la radio con il programma del costruttore.** Spegni la radio in The Rigger con il suo tasto di accensione: la porta USB si libera.

---

The Rigger · software sviluppato da IU1MVI · uso libero e gratuito per tutti gli OM.
La compatibilità OmniRig usa l'interfaccia pubblica di OmniRig di Alex Shovkoplyas, VE3NEA (licenza MIT). Hamlib, flrig, TCI e Ham Radio Deluxe sono marchi dei rispettivi autori. 73!
