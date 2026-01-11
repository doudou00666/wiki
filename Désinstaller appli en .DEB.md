
# Guide de désinstallation d'un paquet sur Ubuntu/Kubuntu

Ce tutoriel reformate les étapes pour supprimer complètement un paquet installé via APT/DPKG sur une distribution Debian-based comme Kubuntu 25.10. Remplacez "nom_du_paquet" par le nom exact trouvé lors de la première étape.

​
Étape 1 : Identifier le paquet

Trouvez le nom exact du paquet installé avec cette commande :
``dpkg -l | grep -i`` nom_du_paquet
Notez le nom précis dans la première colonne de la sortie.

​
Étape 2 : Supprimer le paquet

Exécutez la commande suivante pour une suppression basique (paquet sans configs) :
``sudo apt remove --purge nom_du_paquet``
Cette option ``--purge`` efface aussi les fichiers de configuration principaux.

​
Étape 3 : Nettoyer les dépendances

Supprimez les dépendances inutiles laissées par le paquet :
``sudo apt autoremove``
Cela libère de l'espace en retirant les paquets auto-installés non nécessaires.

​
Étape 4 : Vérifier la suppression

Actualisez les listes de paquets et confirmez l'absence du paquet :
``sudo apt update``
Puis : ``dpkg -l | grep`` nom_du_paquet
Aucun résultat ne doit apparaître si la désinstallation est réussie.
