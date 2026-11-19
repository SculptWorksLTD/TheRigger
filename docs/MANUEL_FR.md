# The Rigger — Manuel

## En bref

The Rigger est le seul à parler avec la radio et donne à chaque programme sa propre connexion : WSJT-X, logiciels de log, de contest et SDR travaillent ensemble sur la même radio. Il trouve les radios tout seul, en gère plusieurs et se met à jour tout seul. Il n'émet jamais de sa propre initiative.

## Installation

**Windows** : téléchargez `The-Rigger-Windows.zip`, placez **The Rigger.exe** dans un dossier à vous (par exemple *Documents*) et ouvrez-le. Si *Windows a protégé votre ordinateur* apparaît : **Informations complémentaires › Exécuter quand même**. Inutile d'installer OmniRig, com0com ou Hamlib. Le raccourci sur le Bureau se crée tout seul.

**Mac** : téléchargez `The-Rigger-Mac.pkg` (puce Apple) ou `The-Rigger-Mac-Intel.pkg` (Intel) et installez-le. Si le Mac refuse de l'ouvrir : *Réglages Système › Confidentialité et sécurité › Ouvrir quand même*.

## Premier démarrage

Branchez la radio avec le câble USB et allumez-la : en quelques secondes elle apparaît dans l'onglet **Radios**. Il n'y a rien à régler dans The Rigger. Réglez ensuite les programmes comme ci-dessous.

## Connecter les programmes

Trois règles valent pour tous les modes :

- **PTT** toujours sur **CAT** (ou *PTT par commande radio*), jamais RTS ou DTR.
- Adresse toujours **127.0.0.1** (votre ordinateur).
- Après le réglage, appuyez sur **Test**, **Connect** ou **OK** dans le programme.

Choisissez le mode que votre programme connaît :

| Mode | Ce que vous réglez | Programmes |
|---|---|---|
| Hamlib | *Hamlib NET rigctl* · `127.0.0.1:4532` | WSJT-X, JTDX, JS8Call, MacLoggerDX, Gpredict, CQRLOG, VarAC |
| flrig | *FLRig* · `127.0.0.1` port `12345` | fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog, Cloudlog) |
| TCI | *TCI* · `127.0.0.1:40001` | N1MM Logger+, MSHV, Log4OM, DXLog |
| OmniRig (Windows) | *OmniRig* · *Rig 1* | Log4OM, HDSDR, SDR Console, CW Skimmer, MMSSTV, UcxLog |
| Ham Radio Deluxe | serveur `127.0.0.1` port `7809` | HRD Logbook, DM-780 |
| DXLab Commander | `127.0.0.1` port `52002` | BBLogger |
| CAT réseau | vrai modèle ou *Kenwood TS-2000* · `127.0.0.1:4600` | N1MM Logger+, DXLab Commander (modèle *Thetis*) |
| Ports série (Mac) | vrai modèle · port `/tmp/TheRigger/…` · vitesse quelconque | RUMlogNG, SkookumLogger |

### Hamlib (WSJT-X et similaires)

1. **Rig** : *Hamlib NET rigctl* (dans certains programmes *rigctld*, modèle 2).
2. **Serveur** : `127.0.0.1:4532`.
3. **PTT** : *CAT*. Dans WSJT-X, appuyez sur **Test CAT** : il devient vert.

### flrig

1. Choisissez **FLRig** (dans fldigi : *Rig Control › flrig › Connect to flrig*).
2. Adresse `127.0.0.1`, port `12345`. Inutile d'installer flrig.

### TCI

1. Choisissez **TCI**, adresse `127.0.0.1:40001`.
2. L'audio reste sur la carte son de la radio, comme d'habitude.

### OmniRig (Windows seulement)

1. Choisissez **OmniRig**, puis **Rig 1** (deuxième radio **Rig 2**). N'installez pas le vrai OmniRig.
2. Lancez les programmes normalement, pas *en tant qu'administrateur*.

### Ham Radio Deluxe

1. Serveur `127.0.0.1`, port `7809`, appuyez sur **Connect**. Inutile d'ouvrir HRD Rig Control.
2. MMTTY et MMVARI : copiez le plugin gratuit **HRDPTT.mmr** dans le dossier du programme et choisissez **HRDPTT** comme port.

### DXLab Commander (BBLogger)

1. Dans BBLogger, *Preferences › CAT* : **IP** `127.0.0.1`, **Port** `52002`, **Autostart** vide. Pas de CatBKT.
2. Dans la fenêtre du QSO, appuyez sur **CAT ON**.

### CAT réseau

1. Comme radio le **vrai modèle** (par exemple *IC-7100*) ou **Kenwood TS-2000**, connexion **TCP**, `127.0.0.1` port `4600`.
2. DXLab Commander : **Model** *Thetis*, **Communicate via TCP**, `127.0.0.1` port `4600`.

### Ports série (Mac)

Comme radio le **vrai modèle** ou **Kenwood TS-2000**, port `/tmp/TheRigger/IC-7100-1` (le nom suit la radio), vitesse quelconque, sans handshake. Un port par programme.

### N3FJP (Windows)

*Rig Interface* : **None**. *Application Program Interface* : cochez **TCP API Enabled**, port `1100`. Bande, mode et fréquence se remplissent tout seuls.

### Plusieurs radios (jusqu’à 10 et plus)

Chaque radio a ses propres adresses : la radio 1 est la première de l’onglet Radios, la 2 la deuxième, et ainsi de suite. Pour les autres, ajoutez le pas indiqué.

| Mode | Radio 1 | Radio 2 | Radio 3 | Chaque radio en plus | Radio 10 |
|---|---|---|---|---|---|
| Hamlib | 4532 | 4534 | 4536 | +2 | 4550 |
| flrig | 12345 | 12346 | 12347 | +1 | 12354 |
| TCI | 40001 | 40002 | 40003 | +1 | 40010 |
| DXLab Commander | 52002 | 52102 | 52202 | +100 | 52902 |
| CAT réseau | 4600 | 4601 | 4602 | +1 | 4609 |
| Ham Radio Deluxe | radio 1 | radio 2 | radio 3 | même port 7809 | radio 10 |
| OmniRig | Rig 1 | Rig 2 | — | 2 seulement : c’est la limite d’OmniRig | — |

Deux radios identiques s’appellent par exemple *IC-7300* et *IC-7300 2*. Avec plus de deux radios, les programmes OmniRig ne voient que les deux premières : pour les autres, utilisez Hamlib, flrig ou TCI.

### Programmes absents de la liste

Cherchez dans le programme l'une de ces options, dans cet ordre : *Hamlib/rigctld*, *FLRig*, *TCI*, *OmniRig*, *Ham Radio Deluxe*, *TCP*. Utilisez la ligne correspondante du tableau. Les programmes Windows qui ne connaissent que les ports COM (Logger32, Win-Test, SatPC32) ne peuvent pas être connectés : utilisez Log4OM, N1MM ou Gpredict.

## La fenêtre

- **Radios** : les radios trouvées, avec fréquence, mode et programmes connectés. Le bouton marche de la carte libère la radio pour un autre programme (par exemple le logiciel du constructeur) ; la vraie radio reste allumée.
- **Manuel** : ce manuel.
- **Réglages** : langue, démarrage automatique, *Démarrer masqué*, mises à jour, ports et pilotes.

The Rigger se met à jour tout seul à chaque démarrage.

## Windows seulement

- **Programmes en conflit** : si le vrai OmniRig, CatBKT, DXLab Commander, flrig, rigctld, HRD ou un logiciel de ports COM virtuels prennent la radio ou les ports, une ligne jaune apparaît dans l'onglet Radios. **Voir** ouvre la liste avec **Fermer…**, **Désinstaller…** ou **Nettoyer…** (restes d'OmniRig dans le registre).
- **Nettoyage com0com** : *Réglages › Ports et pilotes › Nettoyer…* supprime com0com et ses ports virtuels. Lisez l'avertissement, confirmez et redémarrez à la fin.
- **Pilotes USB** : s'il en manque un, The Rigger installe tout seul le pilote officiel.

## Signalements et idées

Le bouton en forme de bulle, en haut à droite : **Quelque chose ne va pas** ou **Idée ou demande**. Joignez le journal du dernier démarrage. C'est anonyme ; l'indicatif est facultatif. *Voir exactement ce qui est envoyé* montre tout avant l'envoi.

## Problèmes courants

- **La radio n'apparaît pas** : allumez-la, vérifiez le câble et appuyez sur *Rechercher à nouveau les radios*. Fermez les programmes qui ouvrent directement le port USB de la radio.
- **Le programme ne se connecte pas** : revérifiez le mode et l'adresse dans le tableau. Si le programme était ouvert avant The Rigger, appuyez de nouveau sur *Test* ou *Connect*.
- **Le PTT ne marche pas** : dans le programme, mettez le PTT sur **CAT**.
- **OmniRig introuvable** : ouvrez The Rigger au moins une fois, puis rouvrez le programme (pas en tant qu'administrateur).

---

The Rigger · logiciel d'IU1MVI · gratuit pour tous les OM. La compatibilité OmniRig utilise l'interface publique d'OmniRig de VE3NEA (licence MIT). Hamlib, flrig, TCI et Ham Radio Deluxe sont des marques de leurs auteurs respectifs. 73 !
