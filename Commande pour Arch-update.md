# 🧭 Tutoriel : Installer et configurer Arch-update via Octopi

Arch-update est un outil pratique permettant de vérifier et d’automatiser les mises à jour de votre système Arch Linux.  
Ce guide vous explique comment l’installer et activer ses services via **Octopi**.

---

## 🧩 Étape 1 — Installation via Octopi

1. Ouvrez **Octopi**.  
2. Recherchez le paquet **arch-update**.  
3. Installez-le depuis le dépôt ou depuis **AUR**, selon la disponibilité.

---

## ⚙️ Étape 2 — Activer l’applet Systray

Une fois Arch-update installé, ouvrez un terminal et exécutez les commandes suivantes :

```bash
arch-update --tray --enable
systemctl --user enable --now arch-update-tray.service
arch-update --tray
