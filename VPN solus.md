# Commande pour créer une connexion VPN Wireguard sur Solus

Installer le paquet suivant ```sudo eopkg install wireguard-tools```

ensuite faire ```sudo -i```

Puis faire ```mkdir /etc/wireguard```

ensuite faire le fichier config ```sudo nano /etc/wireguard/fr.conf```

le **FR** correspond au nom du pays sur lequel je veux me connecter si je veux me connecter sur un autre pays je change le **FR**

Faire le copier coller dans le fichier téléchargé chez le fournisseur VPN

ensuite mettre le kill switch dans le fichier entre **DNS** et **PEER** le bloc suivant:

``PostUp = iptables -I OUTPUT ! -o %i -m mark ! --mark $(wg show %i fwmark) -m addrtype ! --dst-type LOCAL ! -d 192.168.0.0/16 -j REJECT && ip6tables -I OUTPUT ! -o %i -m mark ! --mark $(wg show %i fwmark) -m addrtype ! --dst-type LOCAL -j REJECT
PreDown = iptables -D OUTPUT ! -o %i -m mark ! --mark $(wg show %i fwmark) -m addrtype ! --dst-type LOCAL ! -d 192.168.0.0/16 -j REJECT && ip6tables -D OUTPUT ! -o %i -m mark ! --mark $(wg show %i fwmark) -m addrtype ! --dst-type LOCAL -j REJECT``

Pour se conncecter faire : ```sudo wg-quick up fr```

Pour se déconnecter faire : ```sudo wg-quick down fr```
