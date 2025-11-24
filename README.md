# wiki   VPN

 
# connexion VPN wireguard  sous Archlinux

Paquet à installer

```sudo pacman -S wireguard-tools systemd-resolvconf```

Faire la config

```sudo nano /etc/wireguard/fr.conf```  pour surfark en fr  faire un copier coller du fichier wireguard déjà dl


Demarrer le service de resolution DNS :

```sudo systemctl enable --now systemd-resolved.service```


pour se conneceter faire la commande suivante : ```sudo wg-quick up fr```

pour ce déconnecter faire la commande suivante : ```sudo wg-quick down fr```
