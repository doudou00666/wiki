
# Installation de Yay


Il faut installer les outils de compilations 

`sudo pacman -S --needed base-devel git`

## Cloner le dépot **Yay** : 

`git clone https://aur.archlinux.org/yay.git`

## Il faut entré dans le dossier et compiler : 

`cd yay`    

`makepkg -si`

## En option on fait un nettoyage :

`cd..`

`rm -rf yay`


## Installation de octopi

`yay -S octopi`
