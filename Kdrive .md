DL l'app image : `https://www.infomaniak.com/fr/applications/telecharger-kdrive`

Méthode Obsolète corrigé de la part de Infomaniak mais je garde la méthode au cas où.

Installer Fuse 2

Pour **Débian** ou base **Ubuntu**

`sudo apt install libfuse2t64`

Pour une base **Archlinux**

`sudo pacman -S fuse2`

Ensuite il faut modifier l'argument de lancement en ajoutant devant `QT_QPA_PLATFORM=xcb` 


