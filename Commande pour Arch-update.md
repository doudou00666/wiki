# Arch-update

Installer **Arch-update** par l'intermédiare de Octopi et aprés tapez les commandes suivantes

**Applet systray** : 

`arch-update --tray --enable`  puis `systemctl --user enable --now arch-update-tray.service` et `arch-update --tray`

**Activer le Timer de **Arch-update**** 

`systemctl --user enable --now arch-update.timer`
