
# Connexion VPN wireguard  sous Archlinux

Paquet à installer

```sudo pacman -S wireguard-tools systemd-resolvconf```

Faire la config

```sudo nano /etc/wireguard/fr.conf```  pour surfark en fr  faire un copier coller du fichier wireguard déjà dl

mettre kill switch    A mettre entre **DNS** et **Peer** dans les config vpn pour le kill switch

```PostUp = iptables -I OUTPUT ! -o %i -m mark ! --mark $(wg show %i fwmark) -m addrtype ! --dst-type LOCAL ! -d 192.168.0.0/16 -j REJECT && ip6tables -I OUTPUT ! -o %i -m mark ! --mark $(wg show %i fwmark) -m addrtype ! --dst-type LOCAL -j REJECTPreDown = iptables -D OUTPUT ! -o %i -m mark ! --mark $(wg show %i fwmark) -m addrtype ! --dst-type LOCAL ! -d 192.168.0.0/16 -j REJECT && ip6tables -D OUTPUT ! -o %i -m mark ! --mark $(wg show %i fwmark) -m addrtype ! --dst-type LOCAL -j REJECT```


Demarrer le service de resolution DNS :

```sudo systemctl enable --now systemd-resolved.service```


pour se conneceter faire la commande suivante : ```sudo wg-quick up fr```

pour ce déconnecter faire la commande suivante : ```sudo wg-quick down fr```
