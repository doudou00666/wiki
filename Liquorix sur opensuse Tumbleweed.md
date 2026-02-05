Je peux installer le kernel Liquorix sur Tumbleweed via un dépôt OBS qui le fournit déjà prêt à l’emploi pour openSUSE

1. Ajouter le dépôt Liquorix pour Tumbleweed


``sudo zypper ar -f \
https://download.opensuse.org/repositories/home:/hwsnemo:/kernels/openSUSE_Tumbleweed/ \
liquorix-kernel``

Puis rafraîchis les dépôts :

``sudo zypper ref``


2. Installer le noyau Liquorix

Installe le paquet noyau : ``sudo zypper in kernel-liquorix``

Si tu veux aussi les headers pour compiler des modules (drivers tiers, etc.) :  ``sudo zypper in kernel-liquorix-devel``


3. Redémarrer et choisir le noyau

``sudo reboot``


Dans le menu GRUB, tu devrais voir une entrée une ligne avec kernel-liquorix ou un suffixe -liquorix
