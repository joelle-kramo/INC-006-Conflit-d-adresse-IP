# INC – 006 – Conflit d'adresse IP

## Contexte
Un utilisateur signale qu'il ne parvient plus à accéder au réseau de l'entreprise. Son poste affiche une connexion au réseau local, mais l'accès aux ressources internes et à Internet est impossible.

## Symptômes
- Aucun accès à Intert
- Impossible d'accèder aux serveurs et aux partages réseaux
- Message d'erreur indiquant un conflit d'adresse IP
- Autres utilsateurs du réseau fonctionnant normalement
- Connexion réseau apparaissant comme active

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

 * Disponibilité du serveur DHCP
 * Plage d'adresse IP disponible
 * Réservations d'adresses
 * Baux DHCP actifs

### Vérification de la configuration du poste

Contrôler :

* Présence d'une adresse IP statique
* Mode d'obtention automatique (DHCP)
* Conformité avec plan d'adressage de l'entreprise

## Cause probable 

* Deux équipements utilisent la même adresse IP
* Adresse IP statique configurée dans plage du serveur DHCP
* Bail DHCP corrompu ou expiré
* Mauvaise configuration réseau présente sur le poste utilisateur

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

* Accès au réseau local
* Accès à Internet
* Accès aux ressources de l'entreprise


## Résultat

* Adresse IP unique attribué au poste
* Accès au réseau rétabli
* Ressouces internes de nouveau accessibles
* Connexion Internet fonctionne normalement

## Compétences démontrées

* Diagnostic réseau
* Configuration TCP/IP
* Gestion du protocole DHCP
* Support utilisateur
* Résolution d'incidents réseau
* Administration systèmes et réseaux




