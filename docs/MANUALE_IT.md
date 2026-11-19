# The Rigger — Manuale

## In breve

The Rigger è l'unico a parlare con la radio e dà a ogni programma un collegamento suo: WSJT-X, logger, contest e SDR lavorano insieme sulla stessa radio. Trova le radio da solo, ne gestisce più di una e si aggiorna da solo. Non trasmette mai di sua iniziativa.

## Installazione

**Windows**: scarica `The-Rigger-Windows.zip`, metti **The Rigger.exe** in una cartella tua (per esempio *Documenti*) e aprilo. Se compare *PC protetto da Windows*: **Ulteriori informazioni › Esegui comunque**. Non serve installare OmniRig, com0com o Hamlib. Il collegamento sul Desktop si crea da solo.

**Mac**: scarica `The-Rigger-Mac.pkg` (chip Apple) o `The-Rigger-Mac-Intel.pkg` (Intel) e installalo. Se il Mac non lo apre: *Impostazioni di Sistema › Privacy e sicurezza › Apri comunque*.

## Primo avvio

Collega la radio con il cavo USB e accendila: in pochi secondi compare nella scheda **Radio**. Non c'è niente da impostare in The Rigger. Poi imposta i programmi come qui sotto.

## Collegare i programmi

Tre regole valgono per tutti i modi:

- **PTT** sempre su **CAT** (o *PTT via comando radio*), mai RTS o DTR.
- Indirizzo sempre **127.0.0.1** (il tuo computer).
- Dopo aver impostato premi **Test**, **Connect** o **OK** nel programma.

Scegli il modo che il tuo programma conosce:

| Modo | Cosa imposti | Programmi |
|---|---|---|
| Hamlib | *Hamlib NET rigctl* · `127.0.0.1:4532` | WSJT-X, JTDX, JS8Call, MacLoggerDX, Gpredict, CQRLOG, VarAC |
| flrig | *FLRig* · `127.0.0.1` porta `12345` | fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog, Cloudlog) |
| TCI | *TCI* · `127.0.0.1:40001` | N1MM Logger+, MSHV, Log4OM, DXLog |
| OmniRig (Windows) | *OmniRig* · *Rig 1* | Log4OM, HDSDR, SDR Console, CW Skimmer, MMSSTV, UcxLog |
| Ham Radio Deluxe | server `127.0.0.1` porta `7809` | HRD Logbook, DM-780 |
| DXLab Commander | `127.0.0.1` porta `52002` | BBLogger |
| CAT via rete | modello vero o *Kenwood TS-2000* · `127.0.0.1:4600` | N1MM Logger+, DXLab Commander (modello *Thetis*) |
| Porte seriali (Mac) | modello vero · porta `/tmp/TheRigger/…` · velocità qualsiasi | RUMlogNG, SkookumLogger |

### Hamlib (WSJT-X e simili)

1. **Rig**: *Hamlib NET rigctl* (in alcuni programmi *rigctld*, modello 2).
2. **Server**: `127.0.0.1:4532`.
3. **PTT**: *CAT*. In WSJT-X premi **Test CAT**: diventa verde.

### flrig

1. Scegli **FLRig** (in fldigi: *Rig Control › flrig › Connect to flrig*).
2. Indirizzo `127.0.0.1`, porta `12345`. Non serve installare flrig.

### TCI

1. Scegli **TCI**, indirizzo `127.0.0.1:40001`.
2. L'audio resta sulla scheda audio della radio come sempre.

### OmniRig (solo Windows)

1. Scegli **OmniRig**, poi **Rig 1** (seconda radio **Rig 2**). Non installare il vero OmniRig.
2. Apri i programmi normalmente, non *come amministratore*.

### Ham Radio Deluxe

1. Server `127.0.0.1`, porta `7809`, premi **Connect**. Non serve aprire HRD Rig Control.
2. MMTTY e MMVARI: copia il plugin gratuito **HRDPTT.mmr** nella cartella del programma e scegli **HRDPTT** come porta.

### DXLab Commander (BBLogger)

1. In BBLogger, *Preferences › CAT*: **IP** `127.0.0.1`, **Porta** `52002`, **Autostart** vuoto. Niente CatBKT.
2. Nella finestra del QSO premi **CAT ON**.

### CAT via rete

1. Come radio il **modello vero** (per esempio *IC-7100*) o **Kenwood TS-2000**, collegamento **TCP**, `127.0.0.1` porta `4600`.
2. DXLab Commander: **Model** *Thetis*, **Communicate via TCP**, `127.0.0.1` porta `4600`.

### Porte seriali (Mac)

Come radio il **modello vero** o **Kenwood TS-2000**, porta `/tmp/TheRigger/IC-7100-1` (il nome cambia con la radio), velocità qualsiasi, handshake nessuno. Una porta per programma.

### N3FJP (Windows)

*Rig Interface*: **None**. *Application Program Interface*: spunta **TCP API Enabled**, porta `1100`. Banda, modo e frequenza si compilano da soli.

### Seconda radio

| Modo | Prima radio | Seconda radio |
|---|---|---|
| Hamlib | 4532 | 4534 |
| flrig | 12345 | 12346 |
| TCI | 40001 | 40002 |
| DXLab Commander | 52002 | 52102 |
| CAT via rete | 4600 | 4601 |
| OmniRig | Rig 1 | Rig 2 |
| Ham Radio Deluxe | radio 1 | radio 2 (stessa porta 7809) |

### Programmi non in elenco

Cerca nel programma una di queste voci, in quest'ordine: *Hamlib/rigctld*, *FLRig*, *TCI*, *OmniRig*, *Ham Radio Deluxe*, *TCP*. Usa la riga corrispondente della tabella. I programmi Windows che conoscono solo le porte COM (Logger32, Win-Test, SatPC32) non si possono collegare: usa Log4OM, N1MM o Gpredict.

## La finestra

- **Radio**: le radio trovate con frequenza, modo e programmi collegati. Il tasto di accensione della scheda libera la radio per un altro programma (per esempio il programma del costruttore); la radio vera non si spegne.
- **Manuale**: questo manuale.
- **Impostazioni**: lingua, avvio automatico, *Parti nascosto*, aggiornamenti, porte e driver.

The Rigger si aggiorna da solo a ogni avvio.

## Solo Windows

- **Programmi in conflitto**: se il vero OmniRig, CatBKT, DXLab Commander, flrig, rigctld, HRD o programmi di porte COM virtuali rubano radio o porte, nella scheda Radio compare una riga gialla. **Vedi** porta all'elenco con **Chiudi…**, **Disinstalla…** o **Pulisci…** (resti di OmniRig nel registro).
- **Pulizia com0com**: *Impostazioni › Porte e driver › Pulisci…* toglie com0com e le sue porte virtuali. Leggi l'avviso, conferma e alla fine riavvia.
- **Driver USB**: se manca, The Rigger installa da solo quello ufficiale.

## Segnalazioni e idee

Il tasto con il fumetto, in alto a destra: **Qualcosa non va** o **Idea o richiesta**. Allega il diario dell'ultimo avvio. È anonimo; il nominativo è facoltativo. *Vedi esattamente cosa viene inviato* mostra tutto prima dell'invio.

## Problemi comuni

- **La radio non compare**: accendila, controlla il cavo e premi *Cerca di nuovo le radio*. Chiudi i programmi che aprono direttamente la porta USB della radio.
- **Il programma non si collega**: ricontrolla modo e indirizzo nella tabella. Se il programma era aperto prima di The Rigger, premi di nuovo *Test* o *Connect*.
- **Il PTT non va**: nel programma metti il PTT su **CAT**.
- **OmniRig non trovato**: apri The Rigger almeno una volta, poi riapri il programma (non come amministratore).

---

The Rigger · software di IU1MVI · gratuito per tutti gli OM. La compatibilità OmniRig usa l'interfaccia pubblica di OmniRig di VE3NEA (licenza MIT). Hamlib, flrig, TCI e Ham Radio Deluxe sono marchi dei rispettivi autori. 73!
