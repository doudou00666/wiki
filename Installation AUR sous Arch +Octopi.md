⚙️ Installation de Yay et Octopi sous Arch Linux

🧰 Pré-requis : outils de compilation

Avant toute installation, il faut s’assurer que les outils de compilation nécessaires sont présents.


```bash
sudo pacman -S --needed base-devel git
```

📦 Installation de Yay
🔗 Cloner le dépôt Yay

Pour commencer, il faut cloner le dépôt officiel de Yay depuis l’AUR :

```bash
git clone https://aur.archlinux.org/yay.git
```

🏗️ Compiler et installer

Ensuite, entrez dans le dossier du projet et lancez la compilation :

```bash
cd yay``
``makepkg -si
```

🧹 (Optionnel) Nettoyage du répertoire

Une fois l’installation terminée, vous pouvez faire un petit nettoyage :

``` bash
cd ..
```

```bash
rm -rf yay
```

🖥️ Installation de Octopi

Enfin, installez Octopi, une interface graphique pour gérer vos paquets :

```bash
yay -S octopi
```
