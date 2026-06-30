# INC – 006 – Conflit d'adresse IP

## Contexte
Un utilisateur signale qu'il ne parvient plus à accéder au réseau de l'entreprise. Son poste affiche une connexion au réseau local, mais l'accès aux ressources internes et à Internet est impossible.

## Symptômes
- Aucun accès à Intert
- Impossible d'accèder aux serveurs et aux partages réseaux
- Message d'erreur indiquant un conflit d'adresse IP
- Les autres utilsateurs du réseau fonctionnent normalement
- La connexion réseau apparaît comme active

## Diagnostic

### Vérification de la configuration réseau

Ouvrir l'invite de commandes puis exécuter : 

```cmd
ipconfig /all
```

Contrôler :
- Adresse IPv4 attribuée
- Masque de sous-réseaux
- Passerelle par défaut
- Serveur DHCP
- Serveurs DNS

### Vérification de la présence d'un conflit

Effectuer un test de connectivité :

```
ping < adresse_IP_du_poste >
```

Contrôler : 

* Si une réponse est obtenue depuis une autre machine
* Si l'adresse IP est déjà utilisée sur le réseau

Consulter également les journaux système.

Exemple :

```text
Observateur d'événements
-> Journaux Windows
-> Système
```

Vérifier :

* Les événements signalant un conflit d'adresse IP
* Les messages provenant du service TCP/IP

### Vérification du serveur DHCP

 Contrôler : 

 * La disponibilité du serveur DHCP
 * La plage d'adresse IP disponible
 * Les réservations d'adresses
 * Les baux DHCP actifs

### Vérification de la configuration du poste

Contrôler :

* La présence d'une adresse IP statique
* Le mode d'obtention automatique (DHCP)
* La conformité avec le plan d'adressage de l'entreprise

## Cause probable 

* Deux équipements utilisent la même adresse IP
* Une adresse IP statique est configurée dans la plage du serveur DHCP
* Un bail DHCP est corrompu ou expiré
* Une mauvaise configuration réseau est présente sur le poste utilisateur

## Résolution

### Renouvellement du bail DHCP

Exécuter les commandes suivantes :

```
ipconfig /release
ipconfig /renew
```

### Vérification de la configuration réseau

* Supprimer une adresse IP statique incorrecte
* Configurer l'obtention automatique d'une adresse IP si nécessaire
* Vérifier les paramètres DNS et la passerelle

### Contrôle du serveur DHCP

- Vérifier les baux actifs
- Supprimer les entrées en conflits si nécessaire
- Contrôler la disponibilité de la plage d'adresses

### Validation

Tester la connectivité :

```
ping <passerelle>
ping 8.8.8.8
ping google.com
```

Vérifier :

* L'accès au réseau local
* L'accès à Internet
* L'accès aux ressources de l'entreprise


## Résultat

* Une adresse IP unique est attribué au poste
* L'accès au réseau est rétabli
* Les ressouces internes sotn de nouveau accessibles
* La connexion Internet fonctionne normalement

## Compétences démontrées

* Diagnostic réseau
* Configuration TCP/IP
* Gestion du protocole DHCP
* Support utilisateur
* Résolution d'incidents réseau
* Administration systèmes et réseaux




