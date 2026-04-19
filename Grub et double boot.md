
# Commande Utile

Regénaration du grub : 

```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

# Double boot avec un autre OS

Pour Archlinux installer OS-prober : 

```bash
sudo pacman -S os-prober
```

Editez le fichier de la configuration du GRUB : 

```bash
sudo nano /etc/default/grub
```
Ajoutez ou décommentez cette ligne à la fin du fichier : 

```bash
GRUB_DISABLE_OS_PROBER=false
```
Ensuite regénérer la config du Grub :

```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
