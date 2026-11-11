# The Rigger — Manuel

## À quoi sert-il

The Rigger fait office de standard entre vos radios et les programmes de l'ordinateur. Normalement, le port série d'une radio ne peut être utilisé que par un seul programme à la fois. The Rigger est le seul à parler avec la radio et il donne à chaque programme une connexion qui lui est propre : WSJT-X, le logiciel de log, le logiciel de contest et les autres travaillent ensemble sur la même radio sans se gêner.

Il gère plusieurs radios en même temps, sous Windows, macOS et Linux.

## Installation

Téléchargez le fichier correspondant à votre système sur la page **Releases** du projet sur GitHub.

- **Windows** : lancez `therigger-windows-amd64.exe`. Si « Windows a protégé votre ordinateur » apparaît, choisissez *Informations complémentaires › Exécuter quand même*.
- **macOS** : décompressez `TheRigger-macOS-arm64.zip` (Mac à puce Apple) ou `TheRigger-macOS-amd64.zip` (Mac Intel) et placez *The Rigger* dans Applications. La première fois : clic droit › *Ouvrir*.
- **Linux** : rendez `therigger-linux-amd64` (ou `arm64`, par exemple sur Raspberry Pi) exécutable et lancez-le.

Ensuite, The Rigger se met à jour tout seul et démarre tout seul avec l'ordinateur.

## Premier démarrage

Au démarrage, la fenêtre de bienvenue avec les crédits apparaît. Appuyez sur **Commencer · 73**.

Branchez la radio avec le câble USB et allumez-la. En quelques secondes, The Rigger la reconnaît tout seul : il essaie les ports USB, le protocole et la vitesse, et trouve le modèle. Vous n'avez rien à régler.

## La fenêtre

La fenêtre n'affiche que l'essentiel :

- **une ligne par radio**, avec un voyant : vert si la radio est connectée et répond, gris si elle est éteinte ou débranchée ;
- **sous chaque radio, les programmes connectés**, chacun avec son voyant : vert s'il dialogue avec la radio, jaune s'il a ouvert le port mais reste inactif.

Si vous lisez « aucun programme connecté » sous une radio, aucun programme ne l'utilise.

En haut se trouvent trois boutons : **?** (comment connecter les programmes, et ce manuel), **⚙** (réglages) et **⏻** (quitte The Rigger).

Fermer la fenêtre n'arrête pas The Rigger : il reste dans la zone de notification, près de l'horloge, et les programmes restent connectés. Pour la rouvrir, cliquez sur l'icône et choisissez *Afficher la fenêtre*.

## Connecter les programmes

Appuyez sur **?** : pour chaque programme, The Rigger indique exactement quoi régler, avec le port déjà choisi. Le bouton **Copier** copie le nom du port ou l'adresse, à coller dans le programme.

Il existe deux types de connexion :

1. **Hamlib NET rigctl** : pour WSJT-X, JTDX, JS8Call, fldigi, CQRLOG et les autres programmes qui le prennent en charge. Dans le programme, choisissez *Hamlib NET rigctl* comme radio et l'adresse indiquée comme serveur (par exemple `127.0.0.1:4532`). Autant de programmes que vous voulez peuvent s'y connecter.
2. **Port série** : pour Log4OM, N1MM Logger+, HRD, Logger32, DXLab Commander, MixW et tous les autres. Dans le programme, choisissez comme radio **le vrai modèle de votre radio** (par exemple Icom IC-7100) ou **Kenwood TS-2000**, et le port indiqué. Vitesse au choix, aucun contrôle de flux, PTT par CAT.
   - Sous Windows, ce sont des ports `COM` ordinaires.
   - Sur Mac et Linux, ils se trouvent dans `/tmp/TheRigger/`, par exemple `/tmp/TheRigger/IC-7100-1`.

**Reconnaissance automatique** : chaque port reconnaît tout seul le protocole du programme (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 ou TS-2000). Si vous choisissez le vrai modèle dans le programme, les commandes vont directement à la radio et toutes ses fonctions sont disponibles. Si vous choisissez Kenwood TS-2000, les fonctions communes sont disponibles : fréquence, mode, PTT et split. Avec les radios Yaesu, la toute première fois qu'un programme réglé sur TS-2000 utilise un port, le PTT peut ne pas passer à la première émission : il fonctionne dès la deuxième, et le port s'en souvient.

Un programme par port : The Rigger les attribue déjà pour qu'ils ne se gênent jamais. Chaque radio a 4 ports, que vous pouvez porter à 16 dans les réglages.

### Exemples

- **WSJT-X** : *Paramètres › Radio* : Radio *Hamlib NET rigctl*, Serveur *127.0.0.1:4532*, PTT *CAT*.
- **Log4OM** : dans la configuration CAT, choisissez la radio *Kenwood TS-2000* sur le port indiqué pour Log4OM. OmniRig n'est plus nécessaire.
- **N1MM Logger+** : *Config › Configure Ports* : Radio *Kenwood TS-2000*, le port COM indiqué pour N1MM, vitesse au choix, *DTR* et *RTS* désactivés.

## Réglages

- **Langue** : automatique (celle du système) ou l'une des sept disponibles.
- **Démarrage automatique** : The Rigger démarre tout seul avec l'ordinateur.
- **Mises à jour automatiques** : les nouvelles versions s'installent toutes seules, et seulement quand aucun programme n'utilise la radio.
- **Pilotes USB automatiques** : les pilotes USB manquants s'installent tout seuls.
- **Ports par radio** : de 1 à 16. Effet immédiat ; un port utilisé n'est jamais retiré.

## Pilotes USB

- **Windows** : si vous branchez une radio sans pilote, The Rigger télécharge le pilote officiel signé depuis Windows Update (ou chez le fabricant) et l'installe. Windows demande une confirmation. Sont couverts Silicon Labs (Icom, Yaesu, Kenwood), FTDI (Elecraft et de nombreux câbles), WCH CH340 (Xiegu et câbles économiques) et Prolific.
- **Linux** : les pilotes sont déjà dans le système. The Rigger corrige tout seul les droits d'accès aux ports et le service *brltty*, qui bloque les câbles CH340 sous Ubuntu. Il demande le mot de passe une fois.
- **macOS** : les pilotes font déjà partie du système.

Les ports COM virtuels de Windows utilisent le pilote gratuit *com0com*, que The Rigger installe tout seul la première fois (avec une confirmation de Windows).

## Radios prises en charge

- **Icom** et compatibles CI-V (Xiegu aussi) : IC-7100, IC-7300, IC-705, IC-7610, IC-9700, IC-905, IC-7760 et autres.
- **Kenwood** : TS-2000, TS-480, TS-590S/SG, TS-890S, TS-990S.
- **Elecraft** : K3, KX2, KX3, K4.
- **Yaesu** récents : FT-991/A, FTDX10, FT-710, FTDX101, FT-891, FTDX3000 et autres.
- **Yaesu** classiques : FT-817, FT-818, FT-857, FT-897.
- Autres radios aux commandes compatibles Kenwood : Lab599 TX-500, QRP Labs QDX/QMX et de nombreuses SDR.

## Problèmes fréquents

- **La radio n'apparaît pas** : vérifiez qu'elle est allumée et reliée par le câble USB. Sur les Icom, la vitesse *CI-V USB* du menu de la radio doit être sur *Auto* ou une valeur normale ; *CI-V USB Echo Back* peut rester tel quel.
- **Un programme ne se connecte pas** : appuyez sur **?** et vérifiez que vous avez choisi *Kenwood TS-2000* (ou *Hamlib NET rigctl*) et le bon port. Deux programmes ne peuvent pas utiliser le même port série.
- **Le voyant d'un programme est jaune** : le programme a ouvert le port mais n'interroge pas la radio. Vérifiez que le CAT est activé dans le programme.
- **Windows ne crée pas les ports COM** : sur certains PC sous Windows 11, le pilote *com0com* peut être bloqué. Utilisez alors la connexion *Hamlib NET rigctl*, qui fonctionne toujours.

---

The Rigger · logiciel développé par IU1MVI · utilisation libre et gratuite pour tous les OM. 73 !
