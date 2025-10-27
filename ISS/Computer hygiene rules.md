## Connaître le Système d’Information

### Identifying the components of the IS.

- Avant de protéger un système d’information (SI), il faut d’abord bien le connaître.
  - Cela veut dire faire l’inventaire de tous les éléments du SI : matériels, logiciels, données, utilisateurs, etc.
- Pourquoi ?
  `Parce qu’on ne peut protéger que ce qu’on connaît`.
- Donc, avant de mettre en place des mesures de sécurité, on doit :
  - Lister tous les biens (serveurs, postes, données, applications…)
  - Commencer par les métiers → comprendre les activités de l’entreprise et ce qui est essentiel pour elles.

### Inventorier les biens

Quand on fait l’inventaire des biens, on cherche à tout recenser ce qui fait partie du système d’information.

1. Identifier les biens :
   `Données sensibles` (mots de passe, données clients, contrats, brevets…), `Applications` (les logiciels utilisés et leurs versions), `Systèmes d’exploitation`, `Équipements` (tout le matériel connecté (PC, smartphones, serveurs, routeurs…)).

2. Utiliser des outils :

- Pour repérer les ordinateurs et appareils sur le réseau → ex. ServiceNow, MicroFocus.
- Pour lister les logiciels installés et leurs versions → ex. AIDA64 ou fichiers de configuration.

➡️ But : savoir exactement ce qu’on possède afin de détecter les failles et mieux sécuriser l’ensemble.

### Types de réseaux

- BAN (Body Area Network) : réseau composé de télé transmetteur utilisé dans le domaine de la santé.
- PAN
- WPAN (Wireless PAN)
- LAN
- MAN (Metropolitan Area Network) : réseau plus large qu’un LAN et étendu par exemple sur une ville.
- CAN (Campus Area Network) : réseau s’étendant sur plusieurs LAN, et de la taille d’une université.
- WAN

### Interconnexion

Interconnexion, c’est tout ce qui relie ton réseau à d’autres réseaux (Internet, partenaires, etc.).

Il faut les connaître et les maîtriser car chaque connexion est un point d’entrée potentiel pour une attaque.

Exemples :

- Accès Internet (box, fibre, 4G/5G).
- Connexions avec d’autres réseaux (partenaires, universités) via VPN, liaisons dédiées ou satellite.

➡️ But : savoir par où passe la communication pour contrôler et sécuriser ces accès.

## Maîtriser le réseau

### Sécuriser le réseau interne

- `Créer des zones séparées` : serveurs, postes, invités → pour limiter la propagation d’attaques.
- `Authentification mutuelle` : chaque appareil prouve son identité avant de communiquer → empêche les usurpations.
- `Cloisonner le réseau` avec des outils comme VLAN, sous-réseaux et filtres.
- `Restreindre les accès` : grâce à IEEE 802.1X, on contrôle qui peut se connecter (authentification via certificat ou carte à puce, gérée par un serveur Radius).

➡️ But : s’assurer que seuls les utilisateurs et équipements autorisés accèdent au réseau interne.

### BYOD (Bring Your Own Device)

Le réseau sert à partager des infos, mais il peut aussi propager des virus ou attaques.

Les appareils personnels (ordi, téléphone perso) sont souvent moins sécurisés :

- L’utilisateur installe ce qu’il veut → risques de logiciels malveillants, antivirus pas à jour.
- Contrairement aux appareils professionnels, gérés et sécurisés par l’entreprise (logiciels vérifiés, mises à jour centralisées).

➡️ Ces appareils personnels peuvent fuiter des données sensibles, volontairement ou non.

Conclusion :
Le système d’information fonctionne comme une **chaîne** → s’il y a **_un maillon faible_** (un appareil non sécurisé), **_tout le réseau est en danger._**

### <span style='color: red'>Alors, on interdit les smartphones et ordinateurs personnels au bureau ?</span>

### Contrôler les échanges internes

Contrôler les échanges internes, c’est surveiller et limiter les communications entre les différentes zones du réseau (ex. serveurs, postes utilisateurs, invités).

Filtrer les flux :

- Repérer les ports et protocoles nécessaires.
- Créer une **_matrice de flux_** qui indique ce qui est autorisé ou interdit entre les zones.

Autoriser uniquement ce qui est sûr :

- Utiliser une liste blanche (adresses IP autorisées à communiquer).
- Pas de liste noire, car on ne peut pas prévoir toutes les menaces possibles.

Principe clé :
👉 « Tout ce qui n’est pas explicitement autorisé est interdit »
→ On bloque tout par défaut, puis on ouvre seulement ce qui est nécessaire et sûr.

➡️ But : réduire les risques d’attaques internes et limiter la propagation d’un problème sur le réseau.

### Protéger le réseau interne d’Internet

- Le réseau interne, considéré comme de **confiance**, doit être protégé d’Internet.
- Les serveurs exposés à Internet sont placés dans une DMZ (zone démilitarisée), zone isolée et fortement filtrée.
- Un pare-feu (équipement ou logiciel comme celui de Windows ou Zone Alarm) filtre les échanges, contrôle les connexions entrantes et n’autorise les applications qu’au cas par cas.
- Des systèmes IDS/IPS détectent (IDS) et préviennent (IPS) les tentatives d’intrusion.

➡️ Objectif : empêcher qu’une attaque venant d’Internet atteigne le réseau interne.

### Accès distant

#### Bonnes pratiques :

Points d’entrée identifiés :

- Serveurs d’authentification (TACACS+, RADIUS),
- Concentrateurs VPN,
- Remote Access Server (RAS).

Moyens sécurisés pour se connecter :

- `SSH` → connexion à distance aux équipements (plus sûr que Telnet).
- `RDP` sécurisé → accès à un bureau à distance.
- `SFTP` / `SCP` → copier des fichiers en sécurité.
- `HTTPS` → accès aux interfaces web (ex. TeamViewer).
- `VPN` → créer un tunnel sécurisé sur un réseau public :
  - `IPSec` → authentification + chiffrement, protège tout le trafic.
  - `SSL` → protège surtout le trafic Web, facile à déployer.

⚠️ Détail important : VPN sécurité ≠ VPN réseau

`VPN réseau` : relie deux réseaux internes, la confidentialité est secondaire.  
`VPN sécurité` : relie deux réseaux ou un utilisateur et un réseau de façon sécurisée, avec authentification et chiffrement.

➡️ But : permettre un accès distant tout en garantissant la sécurité et la confidentialité des échanges.

### Sécuriser l’administration

Accès limité : l’administration doit se faire depuis le réseau interne ou via un VPN sécurisé pour les accès distants.

Interfaces Web :

- Ne pas utiliser le compte « admin » par défaut.
- Modifier l’URL de la page d’administration.
- Se protéger contre les attaques de brute force sur les mots de passe.

Réseau d’administration dédié :

- Séparé du réseau de production.
- Seuls les postes et administrateurs autorisés peuvent s’y connecter (liste blanche).
- Authentification mutuelle entre postes et équipements administrés.

➡️ Objectif : protéger les systèmes critiques et empêcher tout accès non autorisé.

### Sécuriser le Wi-Fi

Chiffrement des communications:

- Utiliser une clé Wi-Fi longue (≥ 15 caractères alphanumériques).
- Choisir WPA2 comme protocole de sécurité.
- Si possible, utiliser l’algorithme CCMP pour le chiffrement.

Paramètres du réseau

- Modifier le SSID (nom du réseau par défaut).
- Changer les identifiants par défaut pour accéder à l’interface d’administration de la box (ex. http://192.168.1.1
  ).

Protection de la clé

- Ne pas divulguer la clé Wi-Fi, la garder confidentielle.

⚠️ Remarque : aucune sécurité n’est parfaite ; même WPA2 et CCMP ont des faiblesses connues.  
➡️ Objectif : protéger les communications et limiter les accès non autorisés au réseau Wi-Fi.

#### Wifi : WPS

- Ne pas utiliser le WPS, car il est vulnérable aux attaques par force brute sur le PIN.
- Préférer configurer le Wi-Fi manuellement avec un mot de passe robuste.
- Si WPS est utilisé, désactiver automatiquement après 5 tentatives de clé.

#### Wi-Fi privé vs public

Wi-Fi privé : pour les personnes de confiance dans le réseau interne (WLAN).

- Idéal : authentification par certificats plutôt qu’un mot de passe partagé.

Wi-Fi public : pour le grand public ou personnes non fiables (hotspots).

- Risque : les utilisateurs peuvent écouter le trafic, sauf si les sites visités sont en HTTPS.

#### Wifi : Bonnes pratiques en cas d’usage du Wifi Public

Désactiver le partage :

- Arrêter la découverte réseau.
- Arrêter le partage de fichiers et d’imprimantes.

Activer le pare-feu :

- Contrôler les connexions entrantes et, si possible, les sortantes.
- Activer la journalisation pour suivre les accès.

Navigation sécurisée :

- Éviter les sites en HTTP.
- Vérifier que les sites sont en HTTPS.

Wi-Fi public : si possible, utiliser un **VPN** pour sécuriser les communications.

## Sécuriser les terminaux

### Choisir les applications

- Risque des logiciels inconnus : l’auteur ou le site peut être malveillant, avec des malwares comme des chevaux de Troie pour voler identifiants ou données bancaires.

Bonnes pratiques :

- Télécharger uniquement depuis des sources sûres (sites officiels, stores officiels) et, sur Android, interdire les sources inconnues.

- Vérifier la signature : Utiliser la clé publique du fournisseur pour confirmer que le logiciel est authentique et n’a pas été modifié.

- Vérifier l’empreinte hachée (checksum) :

  - Recalculer le hash du fichier téléchargé et comparer avec celui publié sur le site.
  - Garantit l’intégrité sans clé publique.

- Éviter les téléchargements directs via wget ou curl sans vérification.
- Ne pas se fier à une vérification automatique : faites-la vous-même avec le logiciel, la signature et la clé publique (ex. avec gpg sur Linux).

### Mises à jour logicielles et systèmes

Rôle : corriger des bugs ou vulnérabilités dans les logiciels et systèmes.

Cibles : systèmes d’exploitation et toutes les applications (Flash, Javascript, lecteurs PDF…).

En entreprise :

- Mise à jour centralisée via des serveurs dédiés (ex. WSUS pour Windows).
- Test préalable sur machines de test.
- Sauvegarde avant déploiement sur machines de production.
- Déploiement planifié et validé par l’administrateur.

Bonnes pratiques :

- Activer les mises à jour automatiques quand c’est possible.
- S’assurer que chaque mise à jour ne casse pas les applications existantes (tests de non‑régression).

### Antivirus / Antimalware / Antispyware

**Gratuits** installés par défaut (ex. Microsoft Security Essentials) ou manuellement (Avast, Malwarebytes) ou **Payants** ex. McAfee, Norton Antivirus.

Fonctionnement :

- Mise à jour régulière du moteur et de la base antivirale pour détecter les nouvelles menaces.
- Lorsqu’un nouveau malware apparaît : identification de sa signature, moyens de protection, puis mise à jour de la base.
- ⚠️ Éviter les scans « gratuits » proposés par des sites web suspects.

Limites :

- L’antivirus ne connaît que les signatures connues → temps de retard face aux nouvelles menaces.
- Un malware peut passer inaperçu même avec antivirus à jour.
- Il n’est pas une protection absolue : les mises à jour système, applications et bonnes pratiques restent indispensables.

### Symptômes de malware

- Ralentissement : ordinateur lent au démarrage/arrêt, débit réseau réduit.
- Comportements suspects : pop-ups, publicités, navigateur modifié (page d’accueil, moteur de recherche, extensions inconnues).
- Surconsommation des ressources : espace disque réduit, processeur surchargé.
- Sécurité compromise : antivirus/pare-feu désactivés, mises à jour échouent.
- Messagerie affectée : envoi de messages non autorisés depuis votre compte.

### Protéger les données

- Échanges par email : chiffrer les pièces jointes ou données sensibles (ex. AxCrypt, Zed Container) et transmettre le mot de passe par un autre canal sécurisé.
- Cloud : chiffrer les données avec des logiciels spécialisés, car le Cloud reste un ordinateur tiers non totalement fiable.
- Sauvegardes : utiliser un disque externe ou le Cloud pour conserver des copies sécurisées des données

### Durcissement de configuration des équipements

- Modifier les mots de passe par défaut (ex. compte administrateur).
- Désinstaller les logiciels/services inutiles (ex. partage de fichiers).
- Désactiver les ports et lecteurs non utilisés : USB, série, disquette, débogage USB sur téléphones.
- Sécuriser le BIOS :
  Mettre un mot de passe au démarrage et
  Désactiver le boot sur périphériques externes (clé USB, CD

## Gérer les utilisateurs

### Attribution de privilèges

- Principe du `moindre privilège` : donner à chaque utilisateur seulement les droits nécessaires à ses tâches.
  → Ex. : un visiteur n’a pas besoin d’accès administrateur.

- Principe du `besoin de connaître` : accès uniquement aux données utiles pour son travail ; restreindre l’accès aux informations sensibles.

Bonnes pratiques:

- Charte d’utilisation du SI : document signé par les utilisateurs précisant :
  - **les bonnes pratiques**.
  - **les interdictions**.
  - **les règles et responsabilités**.
  - **les sanctions** (disciplinaires, pénales, civiles).

Procédures d’attribution et de retrait:

- Définir une procédure claire pour attribuer et retirer les privilèges.
- Mettre à jour régulièrement la liste des droits de chaque utilisateur.
- Fournir à chaque utilisateur un compte personnel avec répertoire et boîte mail dédiés.
- En cas de départ ou changement de poste : Désactiver/supprimer le compte, Retirer les accès physiques (badge, clé, etc.).

### Rôles utilisateur

- Le rôle `administrateur`: ayant les privilèges les plus élevés sur le système.
- Le rôle `utilisateur`: ayant le droit d’utiliser le système et d’accéder à des répertoires sensibles.
- Le rôle `invité` : ayant peu de droits, et pas d’accès aux répertoires contenant les informations sensibles.

### Mots de passe : politique de mots de passe

Définir une politique de mot de passe qui oblige à

- Créer un mot de passe complexe
- Avoir un mot de passe d’au moins 8 caractères (10 pour les admin)
- Changer régulièrement les mots de passe
- Utiliser un mot de passe pour déverrouiller l’écran de veille
- Ne pas choisir le même mot de passe pour différents comptes
- Toujours stocker les mots de passe sous forme chiffrée
- Utiliser des « porte-feuilles » de mots de passe
