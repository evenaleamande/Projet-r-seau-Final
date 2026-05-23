# Projet Réseau IoT Sécurisé

## Contexte

Ce projet présente la conception et la sécurisation d’un réseau IoT dans un environnement hospitalier intelligent. L’objectif est de modéliser un réseau sécurisé pour la surveillance d’une chambre de patient, en utilisant des capteurs, des actionneurs et des contrôleurs connectés.

## Description

Le projet illustre comment des objets connectés (caméras, détecteurs de présence, capteurs environnementaux, systèmes d’alarme) peuvent s’interfacer avec une passerelle IoT et un serveur central pour effectuer une assistance automatisée et garantir la sécurité du patient.

## Objectif

- Concevoir une architecture réseau IoT sécurisée
- Garantir la confidentialité et l’intégrité des données échangées
- Segmenter le réseau en VLANs pour limiter la surface d’attaque
- Mettre en place des règles de filtrage et de contrôle d’accès
- Démontrer la simulation d’un scénario hospitalier intelligent

## Architecture et composants

- Routeur principal pour le routage inter-VLAN et l’application des ACL
- Commutateur (switch) pour la segmentation VLAN
- Passerelle IoT connectant les capteurs et actionneurs
- Serveur IoT et système de supervision pour l’analyse des données
- Équipements hospitaliers : webcam, détecteur de mouvement, lumière intelligente, fenêtre motorisée

## Sécurité

- Isolation des appareils IoT sur un VLAN dédié
- Filtrage du trafic entre VLANs via des ACL
- Utilisation de SSH pour l’administration distante
- Séparation du réseau de supervision et du réseau invité
- Protection contre les accès non autorisés et les intrusions

## Scénarios de simulation

- Assistance automatique : activation de la lumière et capture vidéo en cas de mouvement
- Confort : régulation de l’ouverture de la fenêtre selon les paramètres ambiants
- Intrusion : déclenchement d’une alarme et notification du personnel en cas d’accès suspect

## Configuration des équipements

Les configurations suivantes donnent un exemple type de réseau IoT sécurisé et peuvent être adaptées à la topologie du fichier Packet Tracer.

### Routeur principal

```text
hostname R1
!
enable secret cisco123
username admin privilege 15 secret adminpass
ip domain-name reseau-iot.local
crypto key generate rsa modulus 1024
!
interface GigabitEthernet0/0
 description Lien vers VLAN IoT
 ip address 192.168.10.1 255.255.255.0
 no shutdown
!
interface GigabitEthernet0/1
 description Lien vers VLAN Administration
 ip address 192.168.20.1 255.255.255.0
 no shutdown
!
interface GigabitEthernet0/2
 description Lien vers VLAN Invités
 ip address 192.168.30.1 255.255.255.0
 no shutdown
!
ip routing
!
access-list 100 permit ip 192.168.20.0 0.0.0.255 192.168.10.0 0.0.0.255
access-list 100 permit ip 192.168.20.0 0.0.0.255 192.168.30.0 0.0.0.255
access-list 100 deny ip 192.168.30.0 0.0.0.255 192.168.10.0 0.0.0.255
access-list 100 permit ip any any
!
line vty 0 4
 transport input ssh
 login local
!
service password-encryption
!
end
```

### Commutateur principal

```text
hostname SW1
!
vlan 10
 name IoT
!
vlan 20
 name Administration
!
vlan 30
 name Invites
!
interface range FastEthernet0/1 - 8
 switchport mode access
 switchport access vlan 10
!
interface range FastEthernet0/9 - 16
 switchport mode access
 switchport access vlan 20
!
interface range FastEthernet0/17 - 24
 switchport mode access
 switchport access vlan 30
!
interface Vlan10
 ip address 192.168.10.2 255.255.255.0
 no shutdown
!
interface Vlan20
 ip address 192.168.20.2 255.255.255.0
 no shutdown
!
interface Vlan30
 ip address 192.168.30.2 255.255.255.0
 no shutdown
!
ip default-gateway 192.168.20.1
!
end
```

### Passerelle IoT / segmentation

- Séparer les objets IoT dans le VLAN 10
- Placer les équipements de supervision dans le VLAN 20
- Réserver le VLAN 30 aux accès invités
- Appliquer des ACL sur le routeur pour limiter l’accès entre les segments
- Chiffrer les sessions d’administration via SSH

### Notes importantes

Le fichier `presentation final pou reseau..pkt` est un fichier Packet Tracer binaire. La configuration exacte des équipements doit être extraite en ouvrant le fichier avec Cisco Packet Tracer et en copiant les commandes de chaque appareil.

#### Fichiers associés

- `capture du modèle de conception.png` : représentation de notre modèle de conception pour le réseau IoT sécurisé
- `presentation final pou reseau..pkt` : fichier Cisco Packet Tracer montrant notre architecture

## Conclusion

Ce projet pose les bases d’une infrastructure hospitalière IoT sécurisée, combinant automatisation, supervision et cybersécurité. La simulation montre comment isoler les flux, filtrer les communications et protéger un réseau d’objets connectés dans un contexte sensible.

## Commentaire sur les push

Un `push` envoie les modifications locales vers le dépôt distant sur GitHub. Dans ce projet, la branche `feature/add-readme-file-descriptions` a été poussée vers `origin`, ce qui met les changements en ligne et permet de créer une Pull Request.

## Contact

Pour plus d’informations ou questions sur ce projet, consultez le fichier du projet ou contactez l’auteur.
