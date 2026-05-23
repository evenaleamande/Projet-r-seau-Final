# Projet-r-seau-Final



#Conception d'un Réseau IoT Sécurisé : 

Application en Milieu Hospitalier

 Introduction au projet

 Ce projet porte sur la conception et la sécurisation d'un réseau IoT (Internet des Objets) appliqué à un environnement hospitalier intelligent, plus précisément pour la surveillance d'une chambre adaptée aux personnes en situation de handicap.

L'objectif de ce travail est de démontrer comment l'interconnexion de dispositifs intelligents (caméras, capteurs de mouvement, actionneurs) peut automatiser l'assistance d'un patient tout en garantissant un contrôle strict et une sécurité réseau maximale face aux intrusions.

---

 Qu'est-ce qu'un Réseau IoT ?

L'**IoT (Internet of Things)** ou *Internet des Objets* représente l'infrastructure technologique qui permet à des objets physiques de se connecter à Internet afin de collecter, traiter et échanger des données en temps réel sans intervention humaine constante. 

Dans le cadre d'un réseau hospitalier :
Les Capteurs (Entrées) :** Détecteurs de mouvement, webcams de surveillance ou capteurs environnementaux qui mesurent l'état de la chambre.
Les Actionneurs (Sorties) :** Lampes automatiques, sirènes d'alarme ou systèmes d'ouverture de fenêtres qui réagissent selon les données reçues.
Le Contrôleur (Cœur du système) :** Un serveur IoT central ou une passerelle (Home Gateway) qui reçoit les requêtes, analyse les conditions définies et ordonne l'exécution des actions.

---
 Comment assurer la Sécurisation d'un Réseau IoT ?

La prolifération des objets connectés augmente considérablement la surface d'attaque d'une infrastructure. Sécuriser un réseau IoT demande une approche rigoureuse à plusieurs niveaux :

1. La Segmentation Réseau (VLANs) :** Séparer les flux de données. Le réseau de la chambre IoT (patient) et celui du contrôleur central (administration) doivent se trouver sur des sous-réseaux distincts (par exemple via des routeurs configurés comme le modèle 2811), afin qu'une faille sur un objet connecté n'impacte pas tout l'hôpital.
   
2. **Le Contrôle d'Accès et le Filtrage (ACL) :**
   Mettre en place des Listes de Contrôle d'Accès (ACL) sur les routeurs et commutateurs (Switches 2960) pour autoriser uniquement les équipements légitimes (comme le smartphone du superviseur ou le serveur IoT officiel) à interagir avec la chambre.
   
3. L'Automatisation des Règles Conditionnelles (Algorithme IoT) 
   Le système doit être programmé avec des conditions logiques strictes. Si une anomalie ou une tentative d'entrée non autorisée se produit, la caméra s'active immédiatement et le système déclenche une sirène d'alarme sonore côté contrôleur pour alerter instantanément le personnel de sécurité.

 Architecture et Scénarios de Simulation

Le projet est entièrement modélisé et simulé sous **Cisco. L'architecture met en opposition et en interconnexion deux pôles majeurs :
À Gauche — Le Contrôleur de Sécurité :** Composé du serveur IoT principal, d'un smartphone de supervision et d'un système d'alarme redondant (sirènes).
À Droite — La Chambre Patient :** Équipée d'une webcam, d'un détecteur de présence, d'une lumière intelligente et d'une fenêtre motorisée.

Scénarios programmés :
Assistance Automatique :** Si le patient se déplace ou a un problème (mouvement capté), la lumière s'allume automatiquement et la webcam effectue une capture visuelle.
Gestion du Confort :** Régulation de l'ouverture de la fenêtre selon les paramètres climatiques.
Protocole d'Intrusion :** Si une personne inconnue tente d'accéder à la zone restreinte, l'alarme se déclenche automatiquement pour appeler à une intervention immédiate.


##  Conclusion 

mercii
Ce projet de conception pose les bases concrètes d'une infrastructure hospitalière connectée moderne, combinant l'automatisation de l'assistance et la rigueur de la cybersécurité. Grâce à la simulation complète de l'architecture réseau et à la programmation des conditions IoT, notre équipe est pleinement prête pour l'exposé. Les configurations réseau sont prêtes, les scénarios de sécurité sont validés, et nous sommes impatients de vous présenter la démonstration en direct de ce système intelligent !
