# SecretDNS

**Outil gratuit pour Windows qui contourne la surveillance d'Internet (DPI) grâce au DNS sur HTTPS et à la fragmentation SNI, activé en un seul clic.**

[English](README.md) · [한국어](README.ko.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · [Español](README.es.md) · [Português (Brasil)](README.pt-BR.md) · Français

> Ce document est une traduction. En cas de différence, la [version coréenne](README.ko.md) fait foi.

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%2F%2011-0078D4)
![License](https://img.shields.io/badge/license-Freeware-brightgreen)
[![Download](https://img.shields.io/badge/download-kilho.net-orange)](https://down.kilho.net/secretdns?lang=fr)

![Écran de SecretDNS](images/secretdns-en.png)

## Présentation

Lorsque vous ouvrez un site web, l'ordinateur envoie deux choses en clair : une **requête DNS** demandant l'adresse IP du site, et le **nom du site (SNI)** contenu dans le premier paquet de chaque connexion HTTPS. Les équipements d'inspection (DPI) des opérateurs ou des administrateurs réseau lisent ces deux éléments pour savoir quel site vous visitez et, au besoin, coupent la connexion ou vous redirigent vers une page d'avertissement.

SecretDNS bouche ces deux failles d'une seule pression sur le **bouton cadenas**.

- **DNS** — Traite les requêtes DNS de l'ordinateur en **chiffré (DoH)** via un serveur tel que Cloudflare. Les paramètres réseau de Windows ne sont jamais modifiés : dès que vous arrêtez le programme, tout revient à la normale, et si l'ordinateur s'éteint brusquement pendant l'exécution, Internet fonctionne comme d'habitude après le redémarrage, sans aucune trace.
- **SNI** — **Empêche le nom du site d'être exposé aux équipements d'inspection** lors des connexions HTTPS. La connexion au site fonctionne normalement et, seule la partie du nom étant traitée, le ralentissement est quasi nul.

Les sites qui cessent de fonctionner une fois fragmentés (banques, paiements) passent intacts grâce à une **liste d'exceptions** intégrée, et le **Rapport** montre comment chaque site a été traité. Pour les sites que le contournement DNS ne peut pas ouvrir — comme l'**erreur 451**, courante dans les pays sans liberté d'Internet, où le site lui-même refuse les connexions venant de ce pays — le **Proxy mixte** ne fait passer que ces sites par un autre pays. Seuls les domaines que vous indiquez passent par là ; le reste de votre Internet conserve toute sa vitesse.

SecretDNS n'est pas un VPN. Il ne masque pas votre adresse IP et ne chiffre pas tout le trafic : il ne traite que les deux points utilisés pour la surveillance, le DNS et le SNI.

## Fonctionnalités

- **Un seul clic** — Il suffit d'appuyer sur le **bouton cadenas** de l'écran d'accueil. Un clic sur l'icône de la zone de notification ou sur le cadenas en haut à droite des Réglages l'active ou le désactive aussi.
- **DNS sur HTTPS** — Cloudflare par défaut. Ajoutez vos propres serveurs et cochez-en plusieurs ; SecretDNS bascule automatiquement de l'un à l'autre. Un mode **Serveurs** utilise un serveur DNS sans chiffrement (ex. 1.1.1.1).
- **Aucune modification des paramètres Windows** — Les paramètres DNS de la carte réseau ne sont pas touchés. Aucune trace à l'arrêt, et après une coupure de courant ou un arrêt forcé, un redémarrage remet tout en ordre.
- **Fragmentation SNI** — Empêche le nom du site d'être exposé dans les connexions HTTPS et HTTP.
- **Liste d'exceptions / Liste manuelle** — Choisissez les sites à ne pas fragmenter, ou seulement ceux à fragmenter. Quelque 160 domaines (banques, paiements, portails, jeux …) sont intégrés d'office comme exceptions.
- **Navigateurs uniquement** — Applique la fragmentation aux seuls navigateurs principaux, sans toucher aux jeux ni aux logiciels professionnels. Activé dès le départ.
- **Faux paquet** — Méthode de contournement supplémentaire pour les réseaux où la fragmentation seule ne suffit pas.
- **Connexion qui ne coupe pas** — Vérifie que le serveur DNS est joignable avant de démarrer ; si le serveur cesse de répondre en cours d'exécution, Internet reste disponible et le fonctionnement reprend automatiquement au retour du serveur. Internet continue de fonctionner après une mise en veille ou un changement de Wi-Fi.
- **Rapport** — Tableau des domaines et du traitement appliqué (chiffré, fragmenté, texte clair, via serveur …), séparément pour DNS et SNI, dans une fenêtre à part, avec copie dans le presse-papiers.
- **Proxy mixte** — Seuls les domaines de votre liste passent par un serveur à l'étranger. À utiliser pour les sites bloqués par une erreur 451 que le DNS ne peut contourner ; tout le reste se connecte directement comme d'habitude, sans perte de vitesse.
- **Démarrage automatique · zone de notification** — Démarrage avec Windows ; fermer la fenêtre la réduit dans la zone de notification.
- **22 langues** — Suit la langue d'affichage de Windows, ou choisissez-la vous-même dans **Langue** des Réglages.

## Téléchargement / Installation

| Type | Lien |
|---|---|
| Installateur | [Télécharger](https://down.kilho.net/secretdns?lang=fr) |
| Portable (ZIP) | [Télécharger](https://down.kilho.net/secretdns?lang=fr&nosetup) |

L'installateur lance SecretDNS à la fin de l'installation et active **Lancer au démarrage**. Pour la version portable, décompressez le ZIP et lancez `SecretDNS.exe`. Dans les deux cas, SecretDNS demande les **droits d'administrateur**.

## Utilisation

### Premiers pas

1. Lancez SecretDNS. Lorsque la fenêtre de droits d'administrateur apparaît, cliquez sur **Oui**.
2. Appuyez sur le **bouton cadenas** au centre de l'écran d'accueil. Quand le cadenas s'illumine en doré, SecretDNS est en cours d'exécution, et l'icône de la zone de notification devient dorée elle aussi.
3. Utilisez votre navigateur comme d'habitude. Il n'y a rien d'autre à faire.
4. Pour désactiver, appuyez de nouveau sur le cadenas ou cliquez une fois sur l'icône de la zone de notification. Fermer la fenêtre (×) ne quitte pas le programme : il est réduit dans la zone de notification.

Ce qui est activé se décide dans les **Réglages**, ouverts par le bouton **roue dentée** en haut à droite. Pendant l'exécution, les réglages sont verrouillés : arrêtez d'abord pour les modifier (**Langue** et **Voir le journal** restent utilisables pendant l'exécution). Le cadenas en haut à droite des Réglages démarre et arrête directement, sans revenir à l'écran d'accueil.

### Organisation de l'écran

**Écran d'accueil** — Le **bouton cadenas** (Démarrer/Arrêter) au centre, la **roue dentée** (Réglages) en haut à droite, et la version dans la barre d'état en bas. Un clic sur le logo en haut ouvre le site web (le logo des autres écrans fait de même).

**Réglages** — La flèche en haut à gauche ramène à l'écran d'accueil ; le cadenas en haut à droite démarre/arrête. Le cadenas est ouvert et gris à l'arrêt, fermé et doré en cours d'exécution.

| Élément | Rôle |
|---|---|
| **Configuration DNS** — Désactivé / Serveurs / DNS sur HTTPS | Comment traiter les requêtes DNS. Le bouton **Serveurs** des lignes Serveurs et DNS sur HTTPS modifie la liste de serveurs correspondante |
| **Configuration SNI** — Désactivé / Fragment / Fragmentⓜ | Fragmenter tous les sites (sauf la liste d'exceptions) ou seulement ceux de la liste manuelle |
| Liste **Exception** / **Manuel** | Choisir Fragment affiche la liste d'exceptions juste sous cette ligne ; choisir Fragmentⓜ affiche la liste manuelle sous la sienne. Un domaine par ligne |
| **Activer le proxy mixte** | Seuls les domaines de la liste passent par un serveur à l'étranger. Une fois coché, la zone de liste apparaît juste en dessous (nécessite un réglage DNS actif) |
| **Navigateurs uniquement** | Applique la fragmentation et le faux paquet au seul trafic des navigateurs |
| **Activer le faux paquet** | Méthode de contournement supplémentaire pour les réseaux où la fragmentation ne suffit pas |
| **Activer le rapport** + **Voir le journal** | Conserve un rapport. **Voir le journal** ouvre la fenêtre du rapport |
| **Lancer au démarrage** | Démarre dans la zone de notification à l'ouverture de session. S'il était en cours la dernière fois, la protection est aussi activée automatiquement |
| **Langue** | Langue de l'interface. **Système** suit la langue d'affichage de Windows |

**Serveurs DNS** — La liste du côté dont vous avez appuyé sur **Serveurs** (Serveurs ou DNS sur HTTPS) s'affiche sous forme de tableau, avec **Ajouter** · **Modifier** · **Supprimer** en dessous.

**Fenêtre du rapport** — Trois colonnes : **Type** (DNS · SNI · VPN), **Domaine** et **Appliqué**. Chaque ligne identique n'est conservée qu'une fois, et les lignes dont la colonne Appliqué est vide (envoyées sans traitement) sont grisées. **Copier** / **Copier(tout)** copient un texte séparé par des tabulations ; **Effacer** vide la liste. La fenêtre est redimensionnable et, si vous réduisez la fenêtre principale dans la zone de notification puis la rouvrez, la fenêtre du rapport revient avec elle.

**Icône de la zone de notification** — Grise à l'arrêt, dorée en cours d'exécution. Un clic bascule Démarrer/Arrêter. Le menu contextuel contient **SecretDNS** (afficher la fenêtre) · **Démarrer** · **Arrêter** · **Kilho.net** · **Quitter**. Au survol s'affichent la version et l'état actuel.

### Que faire quand…

**Un site redirige vers une page d'avertissement ou la connexion coupe**
Avec les réglages par défaut (DNS **Serveurs** ou **DNS sur HTTPS** + SNI **Fragment**), appuyer sur le cadenas suffit dans la plupart des cas. Activez le rapport et visitez le site : la ligne `SNI` doit indiquer **Fragment** et la ligne `DNS`, **Texte clair** ou **DNS sur HTTPS**. Si cela ne fonctionne toujours pas, essayez **Activer le faux paquet** ci-dessous.

**Un site ne s'ouvre plus après l'activation de SecretDNS (banque, paiement, connexion à un jeu …)**
Le trafic de ce site ne supporte pas la fragmentation. Dans les Réglages, ajoutez son domaine sur une ligne de la liste **Exception** sous la ligne **Fragment**, puis relancez.
- Écrivez-le **en commençant par un point**, comme `.example.com`, pour couvrir `example.com` et tous ses sous-domaines (`www.example.com`, `m.example.com`).
- Vous pouvez coller l'URL de la barre d'adresse telle quelle : `https://`, `www.` et le chemin final sont retirés automatiquement.
- La liste est enregistrée quand vous cliquez en dehors de la zone, quittez les Réglages ou démarrez, et s'applique **à partir du prochain démarrage**. Démarrez directement avec le cadenas en haut à droite des Réglages : inutile de revenir à l'écran d'accueil.
- Quelque 160 domaines — banques, cartes, paiements, portails, boutiques, jeux, administrations (`.go.kr`), écoles (`.ac.kr`) — sont déjà intégrés comme exceptions ; inutile de les saisir. Ils restent actifs même si vous videz la liste.

**Ne fragmenter que quelques sites et laisser le reste tranquille**
Passez la configuration SNI sur **Fragmentⓜ** : la zone de la liste **Manuel** apparaît sous cette ligne. Seuls les domaines qui y sont écrits sont fragmentés ; tout le reste est envoyé tel quel. Si seuls un ou deux sites posent problème, c'est l'option la plus sûre. Les règles de saisie sont les mêmes que pour la liste d'exceptions et, si la liste est vide, SecretDNS vous demande de saisir un domaine avant de démarrer.

**Chiffrer uniquement le DNS, sans fragmentation**
Réglez la configuration DNS sur **DNS sur HTTPS** et la configuration SNI sur **Désactivé**. À l'inverse, pour laisser le DNS tel quel et n'utiliser que la fragmentation, réglez DNS sur **Désactivé**. Si les deux sont désactivés, « Aucune fonction à exécuter. » s'affiche.

**« Impossible de se connecter au serveur DNS chiffré (DoH). » s'affiche**
Certains réseaux d'entreprise ou d'école ont accès à Internet mais n'atteignent pas certains serveurs DoH. Deux solutions :
- Appuyez sur **Serveurs** sur la ligne DNS sur HTTPS et cochez un autre serveur dans la liste (par exemple **cloudflare-dns.com** de la liste par défaut).
- Ou passez la configuration DNS sur **Serveurs**. Pas de chiffrement, mais vous conservez l'avantage d'utiliser un autre serveur DNS sans modifier les paramètres Windows.

**Utiliser un autre serveur DNS**
Appuyez sur **Serveurs** sur la ligne **Serveurs** ou **DNS sur HTTPS** de la configuration DNS pour ouvrir la liste de serveurs correspondante.
- Avec **Ajouter**, saisissez **Nom · Adresse 1 · Adresse 2** (secours, peut rester vide). Les serveurs prennent une adresse IPv4 telle que `8.8.8.8` ; le DoH prend une adresse telle que `https://1.1.1.1/dns-query` ou `https://dns.google/dns-query`.
- Seuls les serveurs **cochés** sont utilisés. Si vous en cochez plusieurs, le passage à un autre serveur est automatique quand l'un ne répond pas. Si aucun n'est coché, Cloudflare est utilisé.
- La liste par défaut contient Cloudflare (coché) et Google (non coché).
- Les modifications s'appliquent **à partir du prochain démarrage**.

**Ne pas perturber les jeux ni les logiciels professionnels**
Laissez **Navigateurs uniquement** activé (il l'est dès le départ). La fragmentation et le faux paquet ne s'appliquent qu'au trafic des navigateurs principaux comme Chrome · Edge · Firefox · Whale ; les autres programmes ne sont pas touchés. Le traitement DNS continue de s'appliquer quel que soit le programme.
À l'inverse, si un programme autre qu'un navigateur (un gestionnaire de téléchargement, par exemple) a aussi besoin de la fragmentation, désactivez **Navigateurs uniquement**.

**Toujours bloqué malgré la fragmentation**
Essayez **Activer le faux paquet**. C'est une méthode de contournement supplémentaire pour les équipements d'inspection que la fragmentation seule ne parvient pas à franchir, et elle n'affecte pas la connexion réelle.

**Ouvrir les sites bloqués en ne faisant passer qu'eux par un serveur à l'étranger (Proxy mixte)**
Dans les pays où la liberté d'Internet n'est pas garantie, un site peut refuser toute connexion venant de ce pays, et le navigateur affiche une **erreur 451** (Unavailable For Legal Reasons). C'est rare dans les pays où Internet est libre. Dans ce cas, ni le chiffrement DNS ni la fragmentation ne l'ouvrent : le blocage repose sur le pays depuis lequel vous vous connectez. Le proxy mixte ne fait passer que ces sites par un serveur d'un autre pays.
Avec un réglage DNS actif, cochez **Activer le proxy mixte** : une zone de liste apparaît juste en dessous. Saisissez un domaine par ligne (`.example.com`, même règle que la liste d'exceptions) et démarrez.
- Seuls les domaines de la liste passent par le serveur à l'étranger ; le reste se connecte directement comme d'habitude. Contrairement à un VPN complet, les autres sites gardent leur vitesse normale.
- Un serveur est attribué automatiquement à chaque démarrage et, s'il ne répond pas, le suivant est utilisé automatiquement.
- Dans le rapport, cela apparaît comme type **VPN**, appliqué **Via serveur**.
- Le proxy mixte nécessite un réglage DNS actif et se désactive en même temps que lui si DNS est mis sur Désactivé.

**L'activer à chaque démarrage de l'ordinateur**
Cochez **Lancer au démarrage** (l'installateur l'enregistre déjà). À l'ouverture de session, il démarre dans la zone de notification sans fenêtre et, **s'il était en cours la dernière fois**, la protection est aussi activée automatiquement. Si vous l'avez arrêté et quitté vous-même, il attend au démarrage suivant sans s'activer.
Si le Wi-Fi tarde à se connecter après le démarrage, il démarre automatiquement dès que le réseau est disponible.

**Le garder actif après avoir fermé la fenêtre**
Appuyer sur fermer (×) ne quitte pas mais réduit dans la zone de notification : il n'y a rien à régler. Pour quitter complètement, clic droit sur l'icône → **Quitter** (une confirmation apparaît). Quitter désactive aussi la protection.

**Changer la langue de l'interface**
Choisissez-la dans **Langue**, tout en bas des Réglages : l'interface change aussitôt, même en cours d'exécution. Choisissez **Système** pour suivre de nouveau la langue d'affichage de Windows.

**Voir comment chaque site est traité en ce moment**
Activez **Activer le rapport** et ouvrez la fenêtre du rapport avec **Voir le journal**. Les domaines visités pendant l'exécution s'ajoutent ligne par ligne. **Voir le journal** fonctionne aussi en cours d'exécution.

| Type | Appliqué | Signification |
|---|---|---|
| DNS | **DNS sur HTTPS** | Résolu via le serveur chiffré |
| DNS | **Texte clair** | Résolu via le serveur indiqué (sans chiffrement) |
| SNI | **Fragment** | Le nom du site a été envoyé fragmenté |
| SNI | (vide) | Envoyé sans traitement : le site figure dans la liste d'exceptions |
| VPN | **Via serveur** | Passé par le serveur à l'étranger via le proxy mixte |

Avec **Copier(tout)**, collez dans le Bloc-notes ou Excel : les colonnes restent séparées.

**Pourquoi Internet ne coupe pas même si le serveur DNS ne répond plus**
SecretDNS vérifie avant de démarrer que le serveur DNS est joignable et, si le serveur cesse de répondre un moment pendant l'exécution, il gère la situation automatiquement pour qu'Internet ne s'arrête pas. Au retour du serveur, il revient automatiquement au fonctionnement normal ; entre-temps, l'état est visible sur l'icône de la zone de notification et dans le rapport. Inutile de le relancer après une sortie de veille ou un changement de Wi-Fi.

**Un message concernant le pilote apparaît**
Dans de rares cas, un message peut demander de redémarrer l'ordinateur avant de lancer le programme. Il suffit de redémarrer comme indiqué.

**L'ordinateur s'est éteint pendant l'exécution**
Aucune inquiétude. SecretDNS ne modifie pas les paramètres réseau de Windows et n'agit que pendant son exécution : après une coupure de courant ou un arrêt forcé, Internet fonctionne comme d'habitude dès le rallumage. Avec Lancer au démarrage activé, il redémarre de lui-même après l'ouverture de session.

## Configuration

Se modifie dans les **Réglages** et s'enregistre immédiatement. La plupart des réglages s'appliquent **à partir du prochain démarrage**, et ils sont conservés lors des mises à jour.

| Élément | Par défaut (installateur) | Par défaut (portable) |
|---|---|---|
| Configuration DNS | Serveurs | Serveurs |
| Configuration SNI | Fragment | Fragment |
| Liste des serveurs DNS | Serveurs : Cloudflare ✓, Google / DNS sur HTTPS : Cloudflare ✓, cloudflare-dns.com ✓, Google | identique |
| Activer le proxy mixte | Désactivé | Désactivé |
| Navigateurs uniquement | Activé | Activé |
| Activer le faux paquet | Désactivé | Désactivé |
| Activer le rapport | Désactivé | Désactivé |
| Lancer au démarrage | Activé | Désactivé |
| Langue | Système | Système |

La langue de l'interface suit la langue d'affichage de Windows (22 langues ; sinon, anglais) et peut être modifiée dans **Langue** des Réglages.

## Configuration requise

- Windows 10 ou Windows 11 (32 et 64 bits)
- **Droits d'administrateur** — une fenêtre de confirmation apparaît à chaque lancement.
- Aucun runtime supplémentaire n'est nécessaire.
- Connexion Internet — pour la vérification du serveur DNS et les notifications de nouvelle version.

## Mises à jour

SecretDNS ne se met **pas** à jour tout seul. Au lancement, il vérifie si une nouvelle version existe et affiche un avis ; en appuyant sur **Oui**, la page de téléchargement s'ouvre et le programme se ferme. Les nouvelles versions sont publiées manuellement après vérification interne et annoncées sur la [page SecretDNS](https://kilho.net/secretdns). Consultez l'[avis sur la politique de mise à jour](https://en.kilho.net/archives/notice/2940).

## Licence

SecretDNS est un **freeware**. Utilisez-le gratuitement et sans restriction partout — au bureau, à la maison, dans les administrations, à l'école — et redistribuez-le librement.

## Liens

- Site web : <https://kilho.net/secretdns>
- Forum : <https://kilho.top/forum/qna>
- X (Twitter) : <https://www.twitter.com/kilhonet>

© KILHO.NET
