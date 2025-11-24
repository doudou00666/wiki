# Installer le mesa sur Ubuntu

Commande pour connaitre la version de mesa  `glxinfo | grep Mesa`

Ajout du PPA : `sudo add-apt-repository ppa:kisak/kisak-mesa`

Mettre a jour : `sudo apt update` et `sudo apt upgrade`

Pour supprimer le PPA d'abord faire ceci : `sudo apt install ppa-purge` 

et ensuite faire cela `sudo ppa-purge ppa:kisak/kisak-mesa`

