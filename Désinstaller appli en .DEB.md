

Trouver le nom du paquet : ``dpkg -l | grep -i`` nom de paquet

Ensuite tu tapes la commande suivante : ``sudo apt remove --purge`` suivit du nom du paquet

Nettoyez les dépendances inutiles : ``sudo apt autoremove``

Si vous souhaitez supprimer aussi les fichiers de configuration, utilisez: ``sudo apt purge`` nom du paquet

Actualisez les listes et vérifiez qu’il est bien désinstallé: ``sudo apt update`` ``dpkg -l | grep `` suivit du nom du paquet et il ne doit plus apparaitre
