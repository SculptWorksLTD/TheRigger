# The Rigger — Manuel

## Ce qu'il fait

The Rigger sert de standard entre vos radios et les programmes de l'ordinateur.

D'habitude, le port CAT d'une radio ne peut être utilisé que par un seul programme à la fois : si WSJT-X l'ouvre, le carnet de trafic ne le trouve plus. Avec The Rigger, c'est différent. The Rigger est le seul à parler avec la radio et il donne à chaque programme une connexion à lui. Ainsi WSJT-X, le carnet de trafic, le programme de contest, CWIU1MVI, le programme SDR et les autres travaillent ensemble sur la même radio sans se gêner.

En bref :

- **il trouve les radios tout seul** : vous branchez le câble USB et la radio apparaît, sans choisir de port, de vitesse ni de modèle ;
- **plusieurs radios en même temps** : chacune a ses propres connexions ;
- **toutes les connexions utilisées par les programmes** : Hamlib, flrig, TCI, OmniRig (Windows), Ham Radio Deluxe, CAT réseau et ports série (Mac et Linux) ;
- **il se met à jour tout seul** et parle 10 langues.

The Rigger n'émet jamais de lui-même et ne modifie rien dans la radio : il exécute seulement ce que demandent les programmes.

## Installation

Téléchargez le fichier de votre système depuis la page **Releases** du projet sur GitHub (SculptWorksLTD/TheRigger).

### Windows

1. Téléchargez `The-Rigger-…-Windows.zip`.
2. Ouvrez le zip et faites glisser **The Rigger.exe** dans un dossier à vous, par exemple *Documents › The Rigger*. Ne le laissez pas dans le zip ni dans un dossier Téléchargements temporaire.
3. Double-cliquez sur **The Rigger.exe**.
4. Si *Windows a protégé votre ordinateur* apparaît, cliquez sur **Informations complémentaires** puis **Exécuter quand même**. Cela n'arrive que la première fois.

Rien d'autre à installer : ni OmniRig, ni com0com, ni Hamlib.

### macOS

1. Téléchargez `The-Rigger-…-Mac.pkg` si votre Mac a une puce Apple (M1, M2, M3, M4), ou `The-Rigger-…-Mac-Intel.pkg` pour un Mac Intel.
2. Ouvrez le fichier et suivez l'installation : The Rigger va dans **Applications**.
3. Si le Mac refuse de l'ouvrir : clic droit sur le fichier › **Ouvrir**, ou *Réglages Système › Confidentialité et sécurité › Ouvrir quand même*.

Dès lors, The Rigger se met à jour tout seul.

## Premier démarrage

Au démarrage s'affiche la fenêtre de bienvenue avec les crédits : appuyez sur **Commencer · 73**.

Branchez la radio avec le câble USB et allumez-la. En quelques secondes, The Rigger la trouve : il essaie les ports USB, le protocole (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817) et la vitesse, puis reconnaît le modèle. Vous n'avez rien à régler.

Quand la radio apparaît dans l'onglet **Radios**, elle est prête : pour régler chaque programme, voyez le chapitre **Instructions pour les programmes** de ce manuel.

## La fenêtre

La fenêtre a trois onglets, choisis en haut au centre :

- **Radios** : les radios trouvées, avec fréquence, mode et programmes connectés ;
- **Manuel** : ce manuel, avec la table des matières à gauche ;
- **Réglages** : langue, démarrage, mises à jour, ports et informations.

En haut à droite, deux boutons :

- **Réduire** (flèche vers le bas) : cache la fenêtre. Sur Mac, The Rigger reste dans la barre des menus, près de l'horloge : cliquez sur l'icône et choisissez *Afficher The Rigger*. Sur Windows, la fenêtre va dans la barre des tâches.
- **Arrêt** (⏻) : ferme The Rigger. Les programmes connectés perdent la radio jusqu'à ce que vous le rouvriez.

En bas se trouve la barre d'état : le voyant est vert quand au moins une radio est connectée, jaune en cas d'avertissement. Le bouton à flèche circulaire recherche à nouveau les radios. La version est à droite.

Vous pouvez agrandir ou réduire la fenêtre en tirant sur ses bords.

## Onglet Radios

Chaque radio trouvée a sa propre fiche.

### En-tête

- **Bouton marche** (à gauche) : active ou désactive la radio *dans The Rigger*. Désactivée, The Rigger ferme son port USB et le laisse libre, par exemple pour le logiciel du fabricant ou une mise à jour du firmware. Appuyez de nouveau pour la reprendre. La vraie radio ne s'éteint pas.
- **Nom** : le modèle, avec un numéro si vous avez deux radios identiques (par exemple *IC-7300 2*).
- **État** : *connectée* (elle répond), *déconnectée* (câble débranché ou radio éteinte) ou *éteinte* (désactivée dans The Rigger).

### Afficheur

- **Fréquence** du VFO utilisé, en grand, avec le **mode** à côté (USB, LSB, CW, CW-R, RTTY, AM, FM, USB-D, LSB-D, FM-D).
- **A** et **B** : quel VFO est utilisé.
- **SPLIT** : allumé quand la radio est en split.
- **TX** : devient rouge quand la radio émet.
- En dessous : la fréquence de l'autre VFO et la barre du **S-mètre**.

L'afficheur suit la radio en temps réel, quand vous tournez le bouton comme quand un programme change la fréquence.

### Données de la radio

La ligne grise indique le modèle, le port USB, la vitesse et, si la radio est active dans The Rigger, son numéro (**Rig 1**, **Rig 2**…). Ce numéro sert à OmniRig et à Ham Radio Deluxe.

### Programmes connectés

La liste des programmes qui utilisent cette radio, chacun avec un voyant :

- **vert** : le programme parle avec la radio ;
- **jaune** : le programme est connecté mais ne demande rien en ce moment.

À droite figure la connexion utilisée (par exemple `tcp:4532`, `flrig`, `TCI`, un port série). Cliquez dessus pour copier son adresse.

### Boutons

- **Tester la connexion** : se fait passer pour un programme et lit la fréquence par chaque connexion (port série, Hamlib, flrig, CAT réseau, TCI). Chaque ligne avec **✓** fonctionne, chaque ligne avec **✗** a un problème. Le test ne fait que lire : il n'émet jamais et ne modifie rien.

### Rechercher à nouveau les radios

Le bouton **Rechercher à nouveau les radios** (en haut à droite de l'onglet, ou la flèche circulaire en bas) revérifie tout de suite tous les ports USB. Utilisez-le après avoir allumé une radio que The Rigger ne voyait pas, ou après avoir fermé un programme qui occupait le port.

## Les connexions

The Rigger ouvre toutes ces connexions pour chaque radio en même temps. Chaque programme utilise celle qu'il connaît, et plusieurs programmes peuvent partager la même connexion.

| Connexion | Adresse (première radio) | Deuxième radio | Systèmes |
|---|---|---|---|
| Hamlib NET rigctl | 127.0.0.1:4532 | 127.0.0.1:4534 | tous |
| flrig | 127.0.0.1:12345 | 127.0.0.1:12346 | tous |
| TCI | 127.0.0.1:40001 | 127.0.0.1:40002 | tous |
| DXLab Commander | 127.0.0.1:52002 | 127.0.0.1:52102 | tous |
| CAT réseau (Kenwood TS-2000) | 127.0.0.1:4600 | 127.0.0.1:4601 | tous |
| Ham Radio Deluxe | 127.0.0.1:7809 (radio 1) | même port, radio 2 | tous |
| OmniRig | Rig 1 | Rig 2 | Windows |
| Ports série | /tmp/TheRigger/… | /tmp/TheRigger/… | Mac et Linux |

Si un port est déjà pris par un autre programme (par exemple un vrai flrig ou rigctld déjà lancé), The Rigger utilise le suivant libre : vous voyez l'adresse exacte en appuyant sur *Tester la connexion* dans la fiche de la radio.

### Hamlib NET rigctl

La connexion de WSJT-X, JTDX, JS8Call, FreeDV, Gpredict, CQRLOG, KLog, MacLoggerDX, Pat et de tous les programmes qui utilisent Hamlib.

Dans le programme, choisissez **Hamlib NET rigctl** comme radio (dans certains programmes *NET rigctl* ou *rigctld*, modèle Hamlib numéro 2) et l'adresse indiquée comme serveur, par exemple `127.0.0.1:4532`. PTT sur **CAT**.

### flrig

The Rigger répond exactement comme flrig (W1HKJ). C'est la connexion de fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog et Cloudlog), WFDlogger et de tous les programmes qui ont l'option *FLRig*.

Dans le programme, choisissez **FLRig**, adresse `127.0.0.1` et port `12345` (deuxième radio `12346`). Inutile d'installer flrig.

### TCI

The Rigger répond comme un appareil TCI (le protocole d'Expert Electronics). Il est utilisé par N1MM Logger+, JTDX, MSHV, Log4OM, QLog, Swisslog, DXLog et d'autres.

Dans le programme, choisissez **TCI** et l'adresse `127.0.0.1:40001` (deuxième radio `40002`). Le TCI de The Rigger transporte fréquences, mode, PTT et split ; l'audio reste sur la carte son de la radio, comme toujours.

### DXLab Commander (pour BBLogger)

The Rigger répond aussi comme DXLab Commander, avec les mêmes messages réseau. BBLogger l’utilise, ainsi que, si vous le souhaitez, WSJT-X, JTDX et MSHV avec la radio *DX Lab Suite Commander*.

Adresse `127.0.0.1:52002` (deuxième radio `52102`). Fréquence, mode, PTT et split. Si le vrai DXLab Commander tourne déjà sur le PC, le port 52002 reste à lui et The Rigger ne l’utilise pas.

### OmniRig (Windows uniquement)

The Rigger prend la place d'OmniRig : **inutile d'installer OmniRig**. Dans le programme, choisissez **OmniRig** puis **Rig 1** pour la première radio active dans The Rigger ou **Rig 2** pour la deuxième.

Cela fonctionne avec Log4OM, DXLog.net, HDSDR, SDR Console, CW Skimmer, UcxLog, Swisslog, MixW, QARTest, VarAC et tous les programmes qui utilisent OmniRig, en 32 comme en 64 bits. Si un programme demande OmniRig alors que The Rigger est fermé, Windows ouvre The Rigger tout seul, réduit.

Si le vrai OmniRig est aussi installé, les programmes trouvent quand même The Rigger, sauf ceux lancés *en tant qu'administrateur* : lancez-les normalement. Ne faites pas tourner les deux en même temps sur la même radio.

### Ham Radio Deluxe

The Rigger répond comme *HRD Rig Control*. Il sert à HRD Logbook, DM-780 et aux programmes qui se connectent à Ham Radio Deluxe (aussi WSJT-X et JTDX avec le choix *Ham Radio Deluxe*).

Dans le programme, réglez le serveur `127.0.0.1` port `7809`. Les radios portent les mêmes noms que dans The Rigger et sont numérotées 1, 2, 3… dans l'ordre de l'onglet Radios.

### CAT réseau (TCP)

Une adresse qui se comporte comme le port série de la radio. Elle convient aux programmes qui savent se connecter à une radio en TCP, comme N1MM Logger+ et MSHV.

Dans le programme, choisissez **le vrai modèle** (par exemple *IC-7100*) ou **Kenwood TS-2000** comme radio, et l'adresse indiquée comme port, par exemple `127.0.0.1:4600`. PTT sur **CAT**.

### Ports série (Mac et Linux)

Pour les programmes qui exigent un port série, The Rigger crée quelques ports virtuels pour chaque radio, par exemple `/tmp/TheRigger/IC-7100-1`, `/tmp/TheRigger/IC-7100-2`…

Dans le programme, choisissez le **vrai modèle** ou **Kenwood TS-2000**, le port indiqué, vitesse **quelconque**, contrôle de flux **aucun**, PTT **CAT**.

Chaque port reconnaît tout seul le langage du programme : Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 ou TS-2000. Avec le vrai modèle, toutes les commandes arrivent à la radio, même les spéciales. Avec TS-2000, fréquence, mode, PTT et split fonctionnent.

Un programme par port : The Rigger donne à chaque programme un port différent. Le nombre de ports par radio se change dans les Réglages (de 1 à 16).

Sous Windows, The Rigger ne crée pas de ports COM virtuels : utilisez les autres connexions, qui n'ont besoin d'aucun pilote.

### CWIU1MVI

CWIU1MVI trouve The Rigger tout seul : dans la liste des radios de CWIU1MVI, choisissez **The Rigger · nom de la radio**. Rien d'autre à régler.

## Instructions pour les programmes

Voici les étapes pour les programmes les plus utilisés. Les adresses sont celles de la première radio : pour les autres, voyez le tableau du chapitre *Les connexions*.

### WSJT-X, JTDX, JS8Call, WSJT-Z

1. *File › Settings › Radio*.
2. **Rig** : *Hamlib NET rigctl*.
3. **Network Server** : `127.0.0.1:4532`.
4. **PTT Method** : *CAT*.
5. **Mode** : *Data/Pkt* si vous voulez la radio en USB-D, sinon *USB*.
6. **Split Operation** : *Rig* ou *Fake It*, comme vous préférez.
7. Appuyez sur **Test CAT** : il devient vert. Puis **OK**.

### fldigi

1. *Configure › Config dialog › Rig Control › flrig*.
2. Cochez **Connect to flrig**, adresse `127.0.0.1`, port `12345`.
3. Décochez *Hamlib* et *RigCAT* s'ils sont cochés.
4. **Save** et fermez : la fréquence de fldigi suit la radio.

### Log4OM 2 (Windows)

1. *Settings › CAT interface*.
2. **CAT engine** : *OmniRig*. **Rig** : *Rig 1* (ou *Rig 2* pour la deuxième radio).
3. Cochez **Autostart** et appuyez sur **Connect**.

Inutile d'installer OmniRig. Sinon choisissez *Hamlib* › *Connect to active HAMLIB interface* avec le port `4532`.

### N1MM Logger+ (Windows)

1. *Config › Configure Ports, Mode Control, Winkey, etc… › Hardware*.
2. Sur une ligne de port, choisissez **TCP**, **Radio** : *IC-7100* (le vrai modèle) ou *Kenwood TS-2000*.
3. Appuyez sur **Set** et saisissez l'adresse `127.0.0.1` port `4600`.
4. Activez **PTT via Radio Command**.
5. **OK** : la fréquence apparaît en bas à gauche.

N1MM peut aussi utiliser **TCI** avec `127.0.0.1:40001`.

### HRD Logbook et DM-780 (Windows)

Dans la fenêtre de connexion à la radio, choisissez le serveur `127.0.0.1` port `7809` et appuyez sur **Connect**. Inutile d'ouvrir *HRD Rig Control* : c'est The Rigger qui répond.

### QLog

1. *Settings › Equipment › Rig*, ajoutez une radio.
2. **Interface** : *FLRig*, hôte `127.0.0.1`, port `12345` (ou *Hamlib* › *NET rigctl* avec `127.0.0.1:4532`).
3. Enregistrez et connectez la radio depuis le menu *Equipment*.

### MacLoggerDX (Mac)

1. *Prefs › Radio*.
2. Choisissez **Hamlib rigctld**, hôte `127.0.0.1`, port `4532`.
3. Activez **Radio VFO** dans la fenêtre de contrôle.

Sinon choisissez le vrai modèle de la radio et un port de `/tmp/TheRigger/`.

### RUMlogNG et SkookumLogger (Mac)

Dans les préférences de la radio, choisissez le **vrai modèle** (ou Kenwood TS-2000) et un port de `/tmp/TheRigger/`, par exemple `/tmp/TheRigger/IC-7100-2`, vitesse quelconque.

### Wavelog et Cloudlog (avec WaveLogGate)

Dans WaveLogGate, ouvrez *Config › Radio*, choisissez **FLRig**, hôte `127.0.0.1`, port `12345`, et enregistrez. Wavelog reçoit la fréquence et le mode et peut les changer.

### HAMRS, Not1MM, WFDlogger

Dans les réglages de contrôle radio, choisissez **FLRig**, hôte `127.0.0.1`, port `12345`.

### MSHV

*Options › Radio and Network Configuration* : choisissez **TCI** et l'adresse `127.0.0.1:40001`.

### HDSDR, SDR Console, CW Skimmer (Windows)

Choisissez **OmniRig** (dans HDSDR *Options › CAT to Radio (Omni-Rig)*, dans SDR Console *Radio › External Radio*, dans CW Skimmer *Setup › Radio*) puis **Rig 1**.

### Gpredict

*Edit › Preferences › Interfaces › Radios › Add new* : hôte `localhost`, port `4532`, type *RX + TX* ou ce dont vous avez besoin.

### CQRLOG (Linux)

*Preferences › TRX control* : décochez *Run rigctld*, **Rig model** : *2 Hamlib NET rigctl*, **Device** : `127.0.0.1:4532`.

### VarAC (Windows)

*Settings › Rig control* : choisissez **OmniRig** et *Rig 1*, ou **Hamlib (rigctld)** avec `127.0.0.1` port `4532`.

### DXLab Commander (Windows)

Commander ne sait utiliser ni OmniRig ni Hamlib, mais il sait parler en réseau avec Thetis : The Rigger répond comme Thetis.

1. *Config › Ports*, panneau de la radio : **Model** : *Thetis*.
2. Cochez **Communicate via TCP**, **IP Address** `127.0.0.1`, **IP Port** `4600` (deuxième radio `4601`).
3. Fermez la configuration : Commander affiche la fréquence, et avec lui DXKeeper, SpotCollector et le reste de la suite DXLab.

### N3FJP ACLog et programmes de contest N3FJP (Windows)

Les programmes N3FJP ne savent pas partager une radio sans port COM, mais ils ont une interface réseau : The Rigger l'utilise tout seul pour envoyer la bande, le mode et la fréquence de la première radio active.

1. *Settings › Rig Interface* : choisissez **None**.
2. *Settings › Application Program Interface* : cochez **TCP API Enabled (Server)**, port `1100`.
3. C'est tout : bande, mode et fréquence se remplissent tout seuls. The Rigger n'enregistre jamais de QSO à votre place.

Ainsi ACLog ne peut pas changer la fréquence de la radio (par exemple en cliquant sur un spot).

### BBLogger (Windows)

BBLogger ne parle pas seul à la radio : il s’appuie sur un programme CAT externe qui utilise les messages de DXLab Commander. The Rigger prend sa place, sans CatBKT.

1. Dans BBLogger, ouvrez *Outils › Configuration/Maintenance › Preferences* (ou *Outils › Configurer le CAT*).
2. Dans le cadre **CAT**, laissez **IP** `127.0.0.1` et **Port** `52002` (deuxième radio `52102`). Inutile d’appuyer sur *Download* ou d’installer CatBKT.
3. Laissez **Autostart** vide : The Rigger est déjà ouvert.
4. Fermez la fenêtre : BBLogger affiche la fréquence et le mode de la radio, modifiables depuis la fenêtre du QSO.
5. Dans la fenêtre du QSO, appuyez sur **CAT ON** : les libellés Freq et Modo deviennent jaunes. Pour le faire automatiquement, cochez *Strumenti › ABILITA CONNESSIONE CAT*.

Si BBLogger ne lit pas la fréquence, fermez CatBKT ou DXLab Commander s’ils sont ouverts : ils occupent le port 52002.

### MMSSTV, MMTTY et MMVARI (Windows)

- **MMSSTV** : *Option › Setup › TX › Radio command*, choisissez **OmniRig** et *Rig 1*.
- **MMTTY et MMVARI** : téléchargez le plugin gratuit **HRDPTT.mmr** (il fait parler les programmes MM avec Ham Radio Deluxe), copiez-le dans le dossier du programme, puis *Option › Setup › TX › Radio command* et choisissez **HRDPTT** comme port. The Rigger répond comme Ham Radio Deluxe, donc le PTT passe par The Rigger.

### Programmes qui ne veulent qu'un port COM (Windows)

Logger32, Win-Test, Winlink Express et SatPC32 ne connaissent que les ports COM, qui sous Windows exigent un pilote signé par Microsoft : pour l'instant The Rigger ne peut pas être utilisé avec ces programmes. Voici par quoi les remplacer, tous gratuits ou déjà compatibles avec The Rigger :

| Au lieu de | Utilisez | Connexion |
|---|---|---|
| Logger32 | Log4OM 2, Swisslog, UcxLog, QLog ou la suite DXLab | OmniRig, Hamlib, flrig ou Thetis (Commander) |
| Win-Test | N1MM Logger+, DXLog.net ou QARTest | CAT réseau / TCI, OmniRig |
| Winlink Express | Pat Winlink, ou Winlink Express sans contrôle de la radio (fréquence à la main) | Hamlib |
| SatPC32 | Gpredict | Hamlib |

### Programmes absents de la liste

Regardez quelle connexion le programme connaît :

- s'il a *Hamlib*, *NET rigctl* ou *rigctld*, utilisez Hamlib (`127.0.0.1:4532`) ;
- s'il a *FLRig*, utilisez flrig (`127.0.0.1:12345`) ;
- s'il a *TCI*, utilisez TCI (`127.0.0.1:40001`) ;
- s'il a *OmniRig* (Windows), utilisez OmniRig *Rig 1* ;
- s'il a *Ham Radio Deluxe*, utilisez `127.0.0.1:7809` ;
- s'il se connecte à une radio en TCP, utilisez le CAT réseau (`127.0.0.1:4600`) avec le vrai modèle ou Kenwood TS-2000 ;
- s'il ne veut qu'un port série (Mac et Linux), utilisez un port de `/tmp/TheRigger/`.

## Plusieurs radios en même temps

The Rigger gère toutes les radios que vous branchez. Chaque radio a :

- ses propres adresses (ports différents, voir le tableau du chapitre *Les connexions*) ;
- son numéro (**Rig 1**, **Rig 2**…) pour OmniRig et Ham Radio Deluxe, selon l'ordre de l'onglet Radios en ne comptant que les radios actives.

Si vous avez deux radios du même modèle, elles s'appellent par exemple *IC-7300* et *IC-7300 2*.

## Désactiver une radio dans The Rigger

Le bouton marche de la fiche d'une radio la désactive **uniquement dans The Rigger** : le port USB se libère et les connexions de cette radio se ferment. Utile quand un autre programme doit utiliser la radio directement, par exemple le logiciel du fabricant ou une mise à jour du firmware.

The Rigger mémorise ce choix même après un redémarrage. Appuyez de nouveau sur le bouton pour reprendre la radio.

## Réglages

### Général

- **Langue** : *Automatique* utilise la langue du système ; sinon choisissez italien, anglais, français, allemand, espagnol, portugais, japonais, russe, arabe ou chinois. Toute la fenêtre, le manuel et les instructions des programmes changent aussitôt.
- **Démarrage automatique** : The Rigger s'ouvre tout seul au démarrage de l'ordinateur, ainsi les radios sont prêtes avant les programmes.

### Mises à jour

- **Mises à jour automatiques** : à chaque démarrage, The Rigger vérifie s'il existe une nouvelle version. Si oui, il la télécharge, l'installe et redémarre tout seul en quelques secondes ; les programmes se reconnectent tout seuls.
- **Rechercher des mises à jour** : vérifie tout de suite. La ligne en dessous indique ce qui se passe (*vous avez déjà la dernière version*, *téléchargement de la mise à jour…*).

Les petites corrections de la fenêtre arrivent en un instant, même sans redémarrer.

### Ports et pilotes

- **Ports série par radio** (Mac et Linux) : combien de ports virtuels créer pour chaque radio, de 1 à 16. Effet immédiat ; les ports utilisés par un programme ne sont jamais retirés.
- **Pilotes USB automatiques** (Windows) : si vous branchez une radio sans pilote, The Rigger installe le pilote officiel (voir *Pilotes USB*).

### Informations

Version, crédits et le bouton pour offrir un café à IU1MVI avec PayPal.

## Pilotes USB

- **Windows** : si vous branchez une radio sans pilote, The Rigger télécharge le pilote officiel signé (depuis Windows Update ou le fabricant) et l'installe. Windows demande une confirmation une seule fois. Sont couverts Silicon Labs CP210x (Icom, Yaesu, Kenwood), FTDI (Elecraft et beaucoup de câbles), WCH CH340 (Xiegu et câbles économiques) et Prolific.
- **macOS** : les pilotes sont déjà dans le système, rien à faire.

## Radios prises en charge

| Marque | Modèles |
|---|---|
| Icom | IC-7100, IC-7300, IC-7300MK2, IC-705, IC-7610, IC-7760, IC-9700, IC-905, IC-7851, IC-7800, IC-7700, IC-7600, IC-7410, IC-7200, IC-7000, IC-9100, IC-746PRO, IC-7400, IC-756 (toutes), IC-718, IC-706 (toutes), IC-703, IC-910H et les autres CI-V, récepteurs IC-R8600, IC-R75, IC-R30 |
| Xiegu | G90, X6100, X6200, X5105, X108G (protocole Icom CI-V) |
| Kenwood | TS-890S, TS-990S, TS-590S/SG, TS-2000, TS-480, TS-870S, TS-570, TS-850, TS-450S, TS-690S et les autres avec commandes CAT |
| Elecraft | K3, K3S, K4, KX2, KX3 |
| Yaesu | FTX-1, FTDX10, FTDX101D/MP, FT-710, FT-991/991A, FT-891, FTDX3000, FTDX5000, FTDX1200, FT-950, FT-2000, FT-450/450D, FTDX9000 |
| Yaesu classiques | FT-817, FT-818, FT-857, FT-897 |
| FlexRadio | série 6000 via le port CAT de SmartSDR |
| Compatibles Kenwood | Lab599 TX-500, QRP Labs QDX/QMX, (tr)uSDX, Malachite et beaucoup de SDR |

Les Icom dont l'adresse CI-V a été changée dans le menu sont trouvées quand même.

## Programmes en conflit (Windows)

Certains programmes font le même travail que The Rigger et, s’ils sont ouverts ou installés, lui prennent la radio ou les ports où les programmes le cherchent : le vrai OmniRig, CatBKT, DXLab Commander, flrig, Hamlib rigctld, Ham Radio Deluxe et les programmes qui créent des ports COM virtuels (VSPE, Virtual Serial Port Driver). The Rigger les cherche tout seul toutes les 20 secondes.

S’il en trouve, une ligne jaune avec le lien **Voir** apparaît dans l’onglet **Radio** et mène à **Réglages › Ports et pilotes › Programmes en conflit**. Pour chaque programme, on voit s’il est ouvert ou installé et quel problème il cause, avec deux boutons :

- **Fermer…** le ferme tout de suite, sans rien désinstaller ;
- **Désinstaller…** ouvre son désinstalleur (Windows demande l’autorisation d’administrateur).

Avant chaque action, une fenêtre explique ce qui se passe, pourquoi et les risques ; on continue seulement en cochant *J’ai lu et compris*. Ensuite The Rigger reprend tout seul la radio et les ports libérés. DXLab Commander, rigctld et Ham Radio Deluxe peuvent seulement être fermés : ils font partie de suites plus larges que vous voulez peut-être garder.

## Nettoyage com0com (Windows)

### Ce que ça fait

Chaque étape s’affiche dans la fenêtre de The Rigger. Le nettoyage cherche com0com, le pilote gratuit qui crée des paires de ports COM virtuels, puis : le désinstalle, supprime tous ses ports virtuels (même les ports « fantômes » que le Gestionnaire de périphériques n’affiche pas), retire son pilote de Windows et libère les numéros COM que ces ports occupaient. Avant de modifier quoi que ce soit, elle montre ce qu’elle a trouvé et demande confirmation ; à la fin, elle propose de redémarrer.

### Pourquoi l’utiliser

Avec le temps, com0com laisse des dizaines ou des centaines de ports virtuels et de numéros COM réservés : les nouveaux ports USB reçoivent des numéros très élevés, Windows affiche des erreurs en boucle, les programmes radio s’embrouillent et le PC ralentit. The Rigger n’utilise pas de ports COM virtuels (les programmes se connectent par OmniRig, Hamlib, flrig, TCI, HRD ou CAT réseau : voir le Manuel), donc com0com n’est plus utile.

### Risques

Il faut l’autorisation d’administrateur. Les programmes qui utilisent com0com ne fonctionnent plus avec ces ports : par exemple un répartiteur de ports ou deux programmes reliés par des ports virtuels. Les vrais ports COM (radios, câbles USB-série) ne sont pas touchés. L’opération est irréversible : si vous avez de nouveau besoin de com0com, il faut le réinstaller. Fermez d’abord les programmes qui utilisent les ports COM. À utiliser à vos risques : l’auteur décline toute responsabilité.

### Mode d’emploi

**Réglages → Ports et pilotes → Nettoyage com0com → Nettoyer…** (le bouton n’est actif que si com0com est sur le PC). Lisez l’avertissement, cochez *J’ai lu et compris* et appuyez sur **Lancer le nettoyage**. Windows demande l’autorisation d’administrateur : répondez **Oui**. Les étapes s’affichent dans la même fenêtre de The Rigger ; après la recherche, appuyez sur **Continuer** (ou **Annuler** pour ne rien modifier). À la fin, appuyez sur **Redémarrer maintenant** ou **Fermer**. Si la fenêtre indique qu’il reste des périphériques, redémarrez le PC et relancez le nettoyage.

## Signalements et idées

Le bouton en forme de bulle, en haut à droite, sert à signaler un problème ou proposer une idée, gratuitement et anonymement.

- **Quelque chose ne va pas** : décrivez ce que vous faisiez, ce que vous attendiez et ce qui s’est passé ; indiquez la radio et le programme. En général, joignez le journal du **dernier démarrage** ; si le problème arrive de temps en temps, celui des **7 derniers jours**.
- **Idée ou demande** : une nouvelle fonction, un programme à relier, une radio à ajouter. Toutes les idées sont étudiées ; celles utiles à beaucoup entrent dans les versions suivantes.

**Anonymat.** Nous n’envoyons ni nom, ni indicatif, ni e-mail, ni adresse IP. Avant l’envoi, The Rigger retire du journal le nom d’utilisateur, le nom du PC, les dossiers personnels et les adresses réseau. Avec *Voir exactement ce qui est envoyé*, vous vérifiez mot à mot ce qui part. N’écrivez pas de données personnelles dans le texte.

Le journal est un fichier texte que The Rigger garde sur votre ordinateur (les 12 derniers démarrages) ; il n’est envoyé que si vous le choisissez.

**Indicatif.** En haut, une case facultative pour l’indicatif : si vous la remplissez, nous pourrons vous recontacter ; si vous la laissez vide, le signalement reste totalement anonyme. The Rigger s’en souvient pour la prochaine fois.

## Problèmes courants

**La radio n'apparaît pas.** Vérifiez qu'elle est allumée et branchée avec le câble USB, puis appuyez sur *Rechercher à nouveau les radios*. Si un autre programme a ouvert le port USB de la radio avant The Rigger, fermez-le : c'est The Rigger qui doit avoir le port. Sur les Icom, le *CI-V USB Baud Rate* doit être sur *Auto* ou une valeur normale.

**Sous Windows, la radio n'apparaît pas et le pilote manque.** Laissez *Pilotes USB automatiques* activé et confirmez la demande de Windows. Si cela ne suffit pas, installez le pilote du fabricant du câble et appuyez sur *Rechercher à nouveau les radios*.

**Le programme ne se connecte pas.** Vérifiez dans ce manuel la connexion choisie et l'adresse. Puis appuyez sur *Tester la connexion* dans la fiche de la radio : il affiche les adresses exactes et, si toutes les lignes ont ✓, The Rigger fonctionne et le problème vient des réglages du programme.

**Le voyant du programme est jaune.** Le programme est connecté mais ne demande rien à la radio. Vérifiez dans le programme que le contrôle CAT est activé (il y a souvent un bouton *Connect* ou *Enable*).

**Le PTT ne fonctionne pas.** Dans le programme, le PTT doit être sur **CAT** (ou *PTT via Radio Command*), pas sur RTS ou DTR.

**Un programme OmniRig dit qu'OmniRig est absent.** The Rigger doit avoir été ouvert au moins une fois sur cet ordinateur. Ouvrez-le, puis rouvrez le programme.

**Un port est déjà utilisé par un autre programme.** Si flrig, rigctld ou un autre programme occupe les mêmes ports, The Rigger prend le suivant libre : vérifiez l'adresse exacte avec *Tester la connexion*.

**Je veux utiliser la radio avec le logiciel du fabricant.** Désactivez la radio dans The Rigger avec son bouton marche : le port USB se libère.

---

The Rigger · logiciel développé par IU1MVI · utilisation libre et gratuite pour tous les OM.
La compatibilité OmniRig utilise l'interface publique d'OmniRig d'Alex Shovkoplyas, VE3NEA (licence MIT). Hamlib, flrig, TCI et Ham Radio Deluxe sont des marques de leurs auteurs respectifs. 73 !
