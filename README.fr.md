# SecretDNS

**Outil gratuit pour Windows qui contourne la surveillance d'Internet (DPI) grâce au DNS sur HTTPS et à la fragmentation SNI, activé en un seul clic.**

[English](README.md) · [한국어](README.ko.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · [Español](README.es.md) · [Português (Brasil)](README.pt-BR.md) · Français

> Ce document est une traduction. En cas de différence, la [version coréenne](README.ko.md) fait foi.

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%2F%2011-0078D4)
![License](https://img.shields.io/badge/license-Freeware-brightgreen)
![Version](https://img.shields.io/badge/version-4.0.5-blue)
[![Download](https://img.shields.io/badge/download-kilho.net-orange)](https://down.kilho.net/secretdns?lang=fr)

![Écran de SecretDNS](images/secretdns-en.webp)

## Présentation

Lorsque vous ouvrez un site web, l'ordinateur envoie deux choses en clair : une **requête DNS** demandant l'adresse IP du site, et le **nom du site (SNI)** contenu dans le premier paquet de chaque connexion HTTPS. Les équipements d'inspection (DPI) des opérateurs ou des administrateurs réseau lisent ces deux éléments pour savoir quel site vous visitez et, au besoin, coupent la connexion ou vous redirigent vers une page d'avertissement.

SecretDNS bouche ces deux failles d'un seul clic sur **Démarrer**.

- **DNS** — Traite les requêtes DNS de l'ordinateur en **chiffré (DoH)** via un serveur tel que Cloudflare. Les paramètres réseau de Windows ne sont jamais modifiés : dès que vous arrêtez le programme, tout revient à la normale, et si l'ordinateur s'éteint brusquement pendant l'exécution, Internet fonctionne comme d'habitude après le redémarrage, sans aucune trace.
- **SNI** — **Empêche le nom du site d'être exposé aux équipements d'inspection** lors des connexions HTTPS. La connexion au site fonctionne normalement et, seule la partie du nom étant traitée, le ralentissement est quasi nul.

Les sites qui cessent de fonctionner une fois fragmentés (banques, paiements) passent intacts grâce à une **liste d'exceptions** intégrée, et le **Rapport** montre comment chaque site a été traité. Pour les sites que le contournement DNS ne peut pas ouvrir — comme l'**erreur 451**, courante dans les pays sans liberté d'Internet, où le site lui-même refuse les connexions venant de ce pays — le **Proxy mixte** ne fait passer que ces sites par un autre pays. Seuls les domaines que vous indiquez passent par là ; le reste de votre Internet conserve toute sa vitesse.

SecretDNS n'est pas un VPN. Il ne masque pas votre adresse IP et ne chiffre pas tout le trafic : il ne traite que les deux points utilisés pour la surveillance, le DNS et le SNI.

## Fonctionnalités

- **Un seul clic** — Il suffit d'appuyer sur **Démarrer** dans l'écran d'accueil. Un clic sur l'icône de la zone de notification l'active ou le désactive aussi.
- **DNS sur HTTPS** — Cloudflare par défaut. Ajoutez vos propres serveurs et cochez-en plusieurs ; SecretDNS bascule automatiquement de l'un à l'autre. Un mode **Serveurs** utilise un serveur DNS sans chiffrement (ex. 1.1.1.1).
- **Aucune modification des paramètres Windows** — Les paramètres DNS de la carte réseau ne sont pas touchés. Aucune trace à l'arrêt, et après une coupure de courant ou un arrêt forcé, un redémarrage remet tout en ordre.
- **Fragmentation SNI** — Empêche le nom du site d'être exposé dans les connexions HTTPS et HTTP.
- **Liste d'exceptions / Liste manuelle** — Choisissez les sites à ne pas fragmenter, ou seulement ceux à fragmenter. Quelque 160 domaines (banques, paiements, portails, jeux …) sont intégrés d'office comme exceptions.
- **Navigateurs uniquement** — Applique la fragmentation aux seuls navigateurs principaux, sans toucher aux jeux ni aux logiciels professionnels.
- **Faux paquet** — Méthode de contournement supplémentaire pour les réseaux où la fragmentation seule ne suffit pas.
- **Connexion qui ne coupe pas** — Vérifie que le serveur DNS est joignable avant de démarrer ; si le serveur cesse de répondre en cours d'exécution, Internet reste disponible et le chiffrement reprend automatiquement au retour du serveur. Internet continue de fonctionner après une mise en veille ou un changement de Wi-Fi.
- **Rapport** — Tableau des domaines et du traitement appliqué (chiffré, fragmenté, texte clair, via serveur …), séparément pour DNS et SNI, avec copie dans le presse-papiers.
- **Proxy mixte** — Seuls les domaines de votre liste passent par un serveur à l'étranger. À utiliser pour les sites bloqués par une erreur 451 que le DNS ne peut contourner ; tout le reste se connecte directement comme d'habitude, sans perte de vitesse.
- **Démarrage automatique · zone de notification** — Démarrage avec Windows, réduction dans la zone de notification à la fermeture.
- **8 langues** — Coréen · anglais · japonais · chinois · russe · italien · français · espagnol. Suit la langue d'affichage de Windows.

## Téléchargement / Installation

| Type | Lien |
|---|---|
| Installateur | [Télécharger](https://down.kilho.net/secretdns?lang=fr) |
| Portable (ZIP) | [Télécharger](https://down.kilho.net/secretdns?lang=fr&nosetup) |

L'installateur lance SecretDNS à la fin de l'installation et l'enregistre pour **démarrer avec Windows**. Pour la version portable, décompressez le ZIP et lancez `SecretDNS.exe`. Dans les deux cas, SecretDNS demande les **droits d'administrateur**.

Différence entre les deux versions : la fonction **Proxy mixte** n'est incluse que dans la version avec installateur (dans la version portable, l'option est verrouillée).

## Utilisation

### Déroulement de base

1. Lancez SecretDNS. Lorsque la fenêtre de droits d'administrateur apparaît, cliquez sur **Oui**.
2. Appuyez sur **Démarrer** dans l'écran d'accueil. Le bouton affiche brièvement **Vérification du réseau**, puis **En cours**, et l'icône de la zone de notification passe à l'état actif.
3. Utilisez votre navigateur comme d'habitude. Il n'y a rien d'autre à faire.
4. Pour désactiver, appuyez de nouveau sur le bouton **En cours** ou cliquez une fois sur l'icône de la zone de notification. Fermer la fenêtre quitte le programme (avec **Réduire en icône à la fermeture** activé, il est réduit dans la zone de notification).

Ce qui est activé se décide dans l'onglet **Réglages**. Pendant l'exécution, les réglages sont verrouillés : arrêtez d'abord pour les modifier (la liste du proxy mixte fait exception : elle s'applique immédiatement, même en cours d'exécution).

### Organisation de l'écran

En haut se trouvent les onglets **Accueil · Réglages · Rapport · Faire un don** ; un clic sur le logo à droite ouvre le site web.

**Réglages**

| Élément | Rôle |
|---|---|
| **Configuration DNS** — Désactivé / Serveurs / DNS sur HTTPS | Comment traiter les requêtes DNS. **[…]** ouvre la fenêtre **Serveurs DNS** pour modifier la liste des serveurs |
| **Configuration SNI** — Désactivé / Fragment / Fragmentⓜ | Fragmenter tous les sites (sauf la liste d'exceptions) ou seulement ceux de la liste manuelle |
| Liste **Exception** / **Manuel** | Liste de domaines qui change selon le réglage SNI. Un domaine par ligne |
| **Réduire en icône au démarrage** | Démarre dans la zone de notification à l'ouverture de session (démarrage avec Windows). S'il était en cours la dernière fois, la protection est aussi activée automatiquement |
| **Réduire en icône à la fermeture** | Fermer la fenêtre ne quitte pas : réduction dans la zone de notification |
| **Activer le proxy mixte** + **[…]** | Seuls les domaines de la liste passent par un serveur à l'étranger. **[…]** modifie la liste (version avec installateur, nécessite un réglage DNS actif) |
| **Activer le rapport** | Conserve les enregistrements dans l'onglet Rapport |
| **Navigateurs uniquement** | Applique la fragmentation et le faux paquet au seul trafic des navigateurs |
| **Activer le faux paquet** | Méthode de contournement supplémentaire pour les réseaux où la fragmentation ne suffit pas |

**Rapport** — Trois colonnes : **Type** (DNS · SNI · VPN), **Domaine** et **Appliqué**. Chaque ligne identique n'est conservée qu'une fois, et les lignes dont la colonne Appliqué est vide (envoyées sans traitement) sont grisées. **Copier** / **Copier(tout)** copient un texte séparé par des tabulations ; **Effacer** vide la liste.

**Icône de la zone de notification** — Un clic bascule Démarrer/Arrêter. Le menu contextuel contient **SecretDNS** (afficher la fenêtre) · **Démarrer** · **Arrêter** · **Kilho.net** · **Quitter**. Au survol s'affichent la version et l'état actuel.

### Que faire quand…

**Un site redirige vers une page d'avertissement ou la connexion coupe**
Avec les réglages par défaut (DNS **DNS sur HTTPS** ou **Serveurs** + SNI **Fragment**), appuyer sur **Démarrer** suffit dans la plupart des cas. Activez le rapport et visitez le site : la ligne `SNI` doit indiquer **Fragment** et la ligne `DNS`, **DNS sur HTTPS**. Si cela ne fonctionne toujours pas, essayez **Activer le faux paquet** ci-dessous.

**Un site ne s'ouvre plus après l'activation de SecretDNS (banque, paiement, connexion à un jeu …)**
Le trafic de ce site ne supporte pas la fragmentation. Ajoutez son domaine sur une ligne de la liste **Exception** dans Réglages, puis relancez.
- Écrivez-le **en commençant par un point**, comme `.example.com`, pour couvrir `example.com` et tous ses sous-domaines (`www.example.com`, `m.example.com`).
- Vous pouvez coller l'URL de la barre d'adresse telle quelle : `https://`, `www.` et le chemin final sont retirés automatiquement.
- La liste est enregistrée quand vous cliquez ailleurs et s'applique **à partir du prochain démarrage**.
- Quelque 160 domaines — banques, cartes, paiements, portails, boutiques, jeux, administrations (`.go.kr`), écoles (`.ac.kr`) — sont déjà intégrés comme exceptions ; inutile de les saisir. Ils restent actifs même si vous videz la liste.

**Ne fragmenter que quelques sites et laisser le reste tranquille**
Passez la configuration SNI sur **Fragmentⓜ** : la liste en dessous devient la liste **Manuel**. Seuls les domaines qui y sont écrits sont fragmentés ; tout le reste est envoyé tel quel. Si seuls un ou deux sites posent problème, c'est l'option la plus sûre. Les règles de saisie sont les mêmes que pour la liste d'exceptions.

**Chiffrer uniquement le DNS, sans fragmentation**
Réglez la configuration DNS sur **DNS sur HTTPS** et la configuration SNI sur **Désactivé**. À l'inverse, pour laisser le DNS tel quel et n'utiliser que la fragmentation, réglez DNS sur **Désactivé**. Si les deux sont désactivés, « Aucune fonction à exécuter. » s'affiche.

**« Impossible de se connecter au serveur DNS chiffré (DoH). » s'affiche**
Certains réseaux d'entreprise ou d'école ont accès à Internet mais n'atteignent pas certains serveurs DoH. Deux solutions :
- Appuyez sur **[…]** à côté de la configuration DNS et, dans la liste **DNS sur HTTPS**, cochez un autre serveur (par exemple **cloudflare-dns.com** de la liste par défaut).
- Ou passez la configuration DNS sur **Serveurs**. Pas de chiffrement, mais vous conservez l'avantage d'utiliser un autre serveur DNS sans modifier les paramètres Windows.

**Utiliser un autre serveur DNS**
Appuyez sur **[…]** à côté de la configuration DNS pour ouvrir la fenêtre **Serveurs DNS**. À gauche, la liste **Serveurs** (adresses IP) ; à droite, la liste **DNS sur HTTPS**.
- Avec **Ajouter**, saisissez **Nom · Adresse 1 · Adresse 2** (secours, peut rester vide). Les serveurs prennent une adresse IPv4 telle que `8.8.8.8` ; le DoH prend une adresse telle que `https://1.1.1.1/dns-query` ou `https://dns.google/dns-query`.
- Seuls les serveurs **cochés** sont utilisés. Si vous en cochez plusieurs, le passage à un autre serveur est automatique quand l'un ne répond pas. Si aucun n'est coché, Cloudflare est utilisé.
- La liste par défaut contient Cloudflare (coché) et Google (non coché).
- Les modifications s'appliquent **à partir du prochain démarrage**.

**Ne pas perturber les jeux ni les logiciels professionnels**
Activez **Navigateurs uniquement**. La fragmentation et le faux paquet ne s'appliquent qu'au trafic des navigateurs principaux comme Chrome · Edge · Firefox · Whale ; les autres programmes ne sont pas touchés. Le chiffrement DNS continue de s'appliquer quel que soit le programme.

**Toujours bloqué malgré la fragmentation**
Essayez **Activer le faux paquet**. C'est une méthode de contournement supplémentaire pour les équipements d'inspection que la fragmentation seule ne parvient pas à franchir, et elle n'affecte pas la connexion réelle.

**Ouvrir les sites bloqués en ne faisant passer qu'eux par un serveur à l'étranger (Proxy mixte)**
Dans les pays où la liberté d'Internet n'est pas garantie, un site peut refuser toute connexion venant de ce pays, et le navigateur affiche une **erreur 451** (Unavailable For Legal Reasons). C'est rare dans les pays où Internet est libre. Dans ce cas, ni le chiffrement DNS ni la fragmentation ne l'ouvrent : le blocage repose sur le pays depuis lequel vous vous connectez. Le proxy mixte ne fait passer que ces sites par un serveur d'un autre pays.
Dans la version avec installateur, avec un réglage DNS actif, cochez **Activer le proxy mixte** et appuyez sur **[…]** pour ouvrir la fenêtre de la liste. Saisissez un domaine par ligne (`.example.com`, même règle que la liste d'exceptions) et appuyez sur **OK**.
- Seuls les domaines de la liste passent par le serveur à l'étranger ; le reste se connecte directement comme d'habitude. Contrairement à un VPN complet, les autres sites gardent leur vitesse normale.
- Un serveur est attribué automatiquement à chaque démarrage et, s'il ne répond pas, le suivant est utilisé automatiquement.
- La liste s'applique **même en cours d'exécution**.
- Dans le rapport, cela apparaît comme type **VPN**, appliqué **Via serveur**.
- Le proxy mixte nécessite un réglage DNS actif et se désactive en même temps que lui si DNS est mis sur Désactivé.

**L'activer à chaque démarrage de l'ordinateur**
Cochez **Réduire en icône au démarrage** (l'installateur l'enregistre déjà). À l'ouverture de session, il démarre dans la zone de notification sans fenêtre et, **s'il était en cours la dernière fois**, la protection est aussi activée automatiquement. Si vous l'avez arrêté et quitté vous-même, il attend au démarrage suivant sans s'activer.
Si le Wi-Fi tarde à se connecter après le démarrage, il démarre automatiquement dès que le réseau est disponible.

**Le garder actif après avoir fermé la fenêtre**
Activez **Réduire en icône à la fermeture** : appuyer sur fermer (×) ne quitte plus mais réduit dans la zone de notification. Pour quitter complètement, clic droit sur l'icône → **Quitter** (une confirmation apparaît). Quitter désactive aussi la protection.

**Voir comment chaque site est traité en ce moment**
Activez **Activer le rapport** et ouvrez l'onglet **Rapport**. Les domaines visités pendant l'exécution s'ajoutent ligne par ligne.

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
Aucune inquiétude. SecretDNS ne modifie pas les paramètres réseau de Windows et n'agit que pendant son exécution : après une coupure de courant ou un arrêt forcé, Internet fonctionne comme d'habitude dès le rallumage. Avec le démarrage automatique activé, il redémarre de lui-même après l'ouverture de session.

## Configuration

Se modifie dans l'onglet **Réglages** et s'enregistre immédiatement. La plupart des réglages s'appliquent **à partir du prochain démarrage**, et ils sont conservés lors des mises à jour.

| Élément | Par défaut (installateur) | Par défaut (portable) |
|---|---|---|
| Configuration SNI | Fragment | Fragment |
| Liste des serveurs DNS | Serveurs : Cloudflare ✓, Google / DoH : Cloudflare ✓, cloudflare-dns.com ✓, Google | identique |
| Réduire en icône au démarrage | Activé | Désactivé |
| Réduire en icône à la fermeture | Activé | Désactivé |
| Activer le proxy mixte | Désactivé | Indisponible |
| Activer le rapport | Désactivé | Désactivé |
| Navigateurs uniquement | Désactivé | Désactivé |
| Activer le faux paquet | Désactivé | Désactivé |

La langue de l'interface suit la langue d'affichage de Windows (coréen · anglais · japonais · chinois · russe · italien · français · espagnol ; sinon, anglais).

## Configuration requise

- Windows 10 ou Windows 11 (32 et 64 bits)
- **Droits d'administrateur** — une fenêtre de confirmation apparaît à chaque lancement.
- Aucun runtime supplémentaire n'est nécessaire.
- Connexion Internet — pour la vérification du serveur DNS et les notifications de nouvelle version.

## Mises à jour

SecretDNS ne se met **pas** à jour tout seul. Au lancement, il vérifie si une nouvelle version existe et affiche un avis ; en appuyant sur **Oui**, la page de téléchargement s'ouvre et le programme se ferme. Les nouvelles versions sont publiées manuellement après vérification interne et annoncées sur la [page SecretDNS](https://v2.kilho.net/secretdns). Consultez l'[avis sur la politique de mise à jour](https://en.kilho.net/archives/notice/2940).

**Historique des versions**

| Version | Date | Modifications |
|---|---|---|
| 4.0.5 | 2026-09-15 | Basculement automatique de serveur du proxy mixte pour des connexions plus stables ; utilisation du VPN plus facile à repérer dans le rapport |
| 4.0.4 | 2026-09-14 | Mise à jour et démarrage automatique plus fiables ; proxy mixte repensé (fenêtre d'édition des domaines, réglages enregistrés) ; fenêtre Serveurs DNS pour ajouter et choisir des serveurs ; meilleure connectivité DNS chiffrée chez certains opérateurs (adresses par nom, nouveau point de connexion Cloudflare) ; conseil de choisir un autre serveur en cas d'échec ; libellés du rapport clarifiés |
| 4.0.2 | 2026-09-04 | Correction des coupures intermittentes d'Internet dans certains environnements ; basculement automatique loin des serveurs DNS instables ; les sites continuent de s'ouvrir pendant les erreurs DNS temporaires ; la connexion chiffrée est rétablie automatiquement une fois le réseau stable |
| 4.0.1 | 2026-08-25 | Correction de l'absence d'Internet juste après le démarrage sur certains PC ; meilleure connectivité après une mise en veille, un VPN ou un changement de Wi-Fi ; récupération automatique en cas de panne d'Internet ; affichage de l'état d'attente et de récupération |

## Licence

SecretDNS est un **freeware**. Utilisez-le gratuitement et sans restriction partout — au bureau, à la maison, dans les administrations, à l'école — et redistribuez-le librement.

## Liens

- Site web : <https://v2.kilho.net/secretdns>
- Forum : <https://groups.google.com/g/kilhonet>
- X (Twitter) : <https://www.twitter.com/kilhonet>

© KILHO.NET
