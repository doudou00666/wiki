
# Commande Utile

Regénaration du grub : `sudo grub-mkconfig -o /boot/grub/grub.cfg`

# Double boot avec un autre OS

Pour Archlinux installer OS-prober : `sudo pacman -S os-prober`

Editez le fichier de la configuration du GRUB : `sudo nano /etc/default/grub`

Ajoutez ou décommentez cette ligne à la fin du fichier : `GRUB_DISABLE_OS_PROBER=false`

Ensuite regénérer lela config du Grub : `sudo grub-mkconfig -o /boot/grub/grub.cfg`
