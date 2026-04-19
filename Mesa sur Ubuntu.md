# Installer le mesa sur Ubuntu

Commande pour connaitre la version de mesa 

```bash
glxinfo | grep Mesa
```

Ajout du PPA : 

```bash
sudo add-apt-repository ppa:kisak/kisak-mesa
```

Mettre a jour : 

```bash
sudo apt update && sudo apt upgrade
```

Pour supprimer le PPA d'abord faire ceci : 

```bash
sudo apt install ppa-purge
``` 

et ensuite faire cela

```bash
sudo ppa-purge ppa:kisak/kisak-mesa
```

