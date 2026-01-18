
# Guide de désinstallation d'un paquet sur Ubuntu/Kubuntu


Ce tutoriel présente les étapes pour supprimer complètement un paquet installé via APT ou DPKG sur une distribution Debian-based comme Kubuntu 25.10. Remplacez "nom_du_paquet" par le nom exact trouvé à l'étape 1.

🔍 Étape 1 : Identifier le paquet

Trouvez le nom exact du paquet installé avec cette commande :

``dpkg -l | grep -i nom_du_paquet``

🗑️ Étape 2 : Supprimer le paquet

Exécutez la commande suivante pour une suppression basique (paquet sans configs) :

``sudo apt autoremove``

🧹 Étape 3 : Nettoyer les dépendances

Supprimez les dépendances inutiles laissées par le paquet :

``sudo apt autoremove``

Cela libère de l'espace en retirant les paquets auto-installés non nécessaires.

✅ Étape 4 : Vérifier la suppression

Actualisez les listes de paquets et confirmez l'absence du paquet :

``sudo apt update``
``dpkg -l | grep nom_du_paquet``

Aucun résultat ne doit apparaître si la désinstallation est réussie.




