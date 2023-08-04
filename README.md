# Checkpoint01SBTSSR
##  1.1. Réponses éléments du réseau - QUIZZ

1. L'élément B est un firewall ou en français pare-feu et l'élément A est un switch ou commutateur réseau. Le Pare-feu laisse passer les flux réseau ou "communications autorisées" grâce à différents types de filtres.
le commutateur réseau permet de mettre en place des réseau virtuel de différents type (bus, en étoile, etc) et répartir les flux au sein du réseau. 

2. em0, em1, em2 représentent les interphases du pare-feu. em0 est en liaison direct avec internet, em1 communique avec le lan 10.0.0.0/24 et l'interphase em2 communique avec le réseau 10.0.1.0/26. la configuration des différentes interphases (em0, em1, em2) ne seront pas les mêmes car elles ne sont pas assujettis aux mêmes environnements et donc aux mêmes risques.

3. /26 est le masque de l'adrresse IP, mais aussi le nombre de bit réseau. il y a 62 adresses IP disponibles sur le réseau où il y a un masque /26.

4. Dans le vocabulaire IP Ubuntu-1 et Ubuntu-2 sont des équipements ou du matériel, ils vont occuper une IP de notre réseau. Ubuntu-1 a d'attribué l'adresse IP suivante : 10.0.1.1/26. Ubuntu-2 a d'attribué l'IP 10.0.0.1/24.

5. Dans le vocabulaire IP A et B sont des équipements réseau qui ont eux aussi des adresses IP privées et public.

6. Ubuntu-2 est connecté à l'équipement réseau pfSense via son interface em1, les flux réseau (toutes formes de communications) allant vers l'exterieurs ou allant vers le LAN 10.0.1.0/26 doivent passer par l'interface em1 de pfSense (si celui veut dire "directement connecté" alors oui Ubunt-2 est connecté directement connecté à em1 de l'équipement pfSense, mais Ubuntu-2 n'a pas a réellement communiqué avec pfSense, celui-ci est invisible pour Ubuntu-2).

##  1.2. Etude théorique

11. Calcul des réseaux :
Sur le réseau 10.0.0.0/24 la plage d'adresses disponible est la suivante :
10.0.0.1/24 à 10.0.0.254/24
    l'adresse de diffusion (le broadcast) est 10.0.0.255/24
Sur le réseau 10.0.1.0/26 la plage d'adresses disponible est la suivante :
10.0.1.1/26 à 10.0.1.62/26
    l'adresse de diffusion (le broadcast) est 10.0.1.63/26

12. Les machines Ubuntu-1 et Ubuntu-2 peuvent communiquer mais uniquement de Ubuntu-1 vers Ubuntu-2 car l'on connait la passerelle qui mène à Ubuntu-2.

13. Les 2 machines Ubuntu-1 et Ubuntu-2 peuvent communiquer vers l'extérieur et l'extérieur peut leurs répondre. Ubuntu-1 peut communiquer vers Ubuntu-2 car l'on a l'adresse de la passerelle. Switch peut communiquer avec Ubuntu-2 et Switch1 peut communiquer avec Ubuntu-1.

14. L'on peut créer des adresses IP dynamiques en passant par un routeur, en ayant un nouveau fournisseur d'accès internet qui nous attribura une nouvelle adresse IP dynamique ou en passant par un VPN qui nous attribura une nouvelle IP dynamique.

##  1.3 Analyse de trames

**Fichier 1**:
16. la machine qui initialise la communication est Private_66:68:00 (00:50:79:66:68:00) - les machines du réseau 10.10.4.0

17. Oui la communication a été établi entre les 2 machines du réseau 10.10.4.0, qui sont 10.10.4.1 et 10.10.4.2 La machine 10.10.4.1 a pingué la machine 10.10.4.2, cette dernière a bien répondu au ping.

18. C'est la machine 10.10.4.1 qui a fait la demande donc le request et c'est la machine 10.10.4.2 qui a répondu donc le reply.

19. Les rôles des matériels A et B sont d'optimiser la "route" des flux entre les machines. 

**Fichier 2**:
20. la machine qui initialise la communication est Private_66:68:02 (00:50:79:66:68:02) - La machine 10.10.80.3

21. La communication n'est pas établi (Host unreachable) entre la machine 10.10.80.3 et la machine 10.11.80.2
La communication est un échec car les machines ne sont pas dans le même réseau.

22. Les rôles des matériels A et B est d'envoyer les requêtes aux bons équipements et de leurs renvoyer les flux qui leurs est destinés.

**Fichier 3**:
23. la machine qui initialise la communication est Private_66:68:02 (00:50:79:66:68:02) - La machine 10.10.80.3

24. La communication n'a pas réussite car notre machine va pingué un réseau public (https://awebanalysis.com/fr/ip-lookup/8.8.8.8/) et sur un équipement CISCO qui plus est.

25. Les rôles des matériels A et B est d'envoyer les requêtes aux bons équipements et de leurs renvoyer les flux qui leurs est destinés qui prennent en compte les nouveaux paramètres énoncés lignes 1,2 et3.

26. Je vois les différents protocoles encapsulés dans la colonne Protocol (CDP, ARP, ICMP).
