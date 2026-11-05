# Résumé — Fedora Workstation (note AFFiNE)

> Source : [note.cloud-box.ovh](https://note.cloud-box.ovh/workspace/32944895-5f28-4800-b6fb-7d4bc11efe07/SJ_PL6J3SGOjN7fw3eKt4)

## Vue d'ensemble

**Fedora Workstation** est une distribution Linux développée par le Fedora Project, une communauté mondiale de contributeurs bénévoles. Lancée en 2003 comme continuation de Red Hat Linux, Fedora sert de plateforme d'innovation et de test pour les technologies open source de pointe. Le projet est sponsorisé principalement par Red Hat (filiale d'IBM depuis 2019), mais gouverné par une communauté indépendante. Fedora est l'amont (upstream) de Red Hat Enterprise Linux (RHEL) — les nouvelles technologies sont testées dans Fedora avant d'éventuellement intégrer RHEL.

**Principes fondamentaux :**

- Logiciels libres uniquement dans les dépôts officiels (politique stricte sur les licences)
- Cycle de publication rapide : nouvelle version tous les 6 mois (avril et octobre), support ≈ 13 mois
- Intégration rapide des dernières technologies (Wayland, PipeWire, Btrfs, etc.)

## Sommaire

1. [Dépôts RPM Fusion](#depts-rpm-fusion)
2. [Ajout du support flatpak](#ajout-du-support-flatpak)
3. [Outils Gaming sur Fedora](#outils-gaming-sur-fedora)
   - Pilotes NVIDIA
   - MangoHud
   - GOverlay
   - Steam
   - Heroic Games Launcher
   - Gamemode
   - ProtonPlus
4. [Codecs Multimédia](#codecs-multimdia)
5. [Polices d'écriture](#polices-driture)
6. [Dépôts complémentaires](#depts-complmentaires)
7. [Noyau gaming CachyOS](#noyau-gaming-cachyos)
8. [Fedora Steam Session](#fedora-steam-session)
9. [Optimisation DNF](#optimisation-dnf)

## Dépôts RPM Fusion

Fedora n'inclut que des logiciels dont les licences sont compatibles avec sa politique stricte de logiciels libres. **RPM Fusion** est un dépôt communautaire tiers qui complète les dépôts officiels en fournissant :

- Licences propriétaires ou restrictives (pilotes NVIDIA, certains codecs)
- Problèmes de brevets logiciels (codecs H.264, H.265, AAC)
- Logiciels non libres (Steam, Discord, certaines applications multimédia)
- Restrictions légales selon les juridictions

**Deux sections :**

- **Free** : logiciels libres mais incompatibles avec la politique Fedora (problèmes de brevets)
- **Non-Free** : logiciels propriétaires ou avec licences restrictives

**Installation :**

```bash
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf upgrade --refresh
```

## Ajout du support flatpak

**Flatpak** : format de paquets qui permet aux développeurs de fournir une seule version de leur application qui tourne sur (presque) toutes les distributions, dans un bac à sable plus sécurisé.

**Atouts :**

- Mêmes applications partout (Debian, Fedora, Arch, etc.)
- Sandbox : isolation de l'app du système
- Installation sans droits admin (espace utilisateur)
- Un seul paquet pour toutes les distros

**Contreparties :**

- Embarquage des dépendances (prise de place disque)
- Intégration système parfois moins fine
- Configuration des permissions via `flatseal`

**Installation :**

```bash
sudo dnf install flatpak
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
# redémarrage requis
```

## Outils Gaming sur Fedora

Fedora est devenue une excellente plateforme pour le gaming Linux grâce à Proton (Steam Play) et à un écosystème d'outils matures.

### Pilotes NVIDIA

```bash
sudo dnf install akmod-nvidia
# (optionnel pour CUDA / NVENC)
sudo dnf install xorg-x11-drv-nvidia-cuda
# redémarrer, puis vérifier
nvidia-smi
```

### 1. MangoHud — Overlay de performance

Affiche en temps réel les FPS, températures CPU/GPU, utilisation mémoire, fréquences et autres métriques de performance pendant vos sessions de jeu.

```bash
sudo dnf install mangohud
# Avec Steam : ajouter mangohud %command% dans les arguments de lancement du jeu
```

### 2. GOverlay — Interface graphique pour MangoHud

Permet de configurer MangoHud via une interface graphique.

```bash
sudo dnf install goverlay
```

Fonctionnalités : configuration visuelle des métriques, profils par jeu, thèmes et positionnement personnalisables, statistiques avancées (frametimes, percentiles).

### 3. Steam

```bash
sudo dnf install steam
```

Configuration recommandée :
- Changez la langue (Steam > Paramètres > Interface)
- Après installation de ProtonPlus : définir « Proton GE-Latest » (Paramètres > Compatibilité)

### 4. Heroic Games Launcher

Alternative open source au launcher officiel Epic Games, avec support natif de GOG et Amazon Prime Gaming.

**Installation recommandée (RPM) :**

- GitHub : <https://github.com/Heroic-Games-Launcher/HeroicGamesLauncher/releases>
- Version : `Heroic-X-X-X-linux-x86_64.rpm`

En `.rpm`, les mises à jour se font manuellement ; Heroic notifie avec un lien vers la nouvelle version.

### 5. Gamemode — Optimisation système pendant le gaming

Ajuste automatiquement les paramètres système (gouverneur CPU, priorités processus, etc.) pour maximiser les performances.

```bash
sudo dnf install gamemode
# Avec Steam : ajouter gamemoderun %command%
# gamemode + mangohud : gamemoderun mangohud %command%
```

### 6. ProtonPlus — Gestion des versions Proton

Installe et gère facilement différentes versions de Proton (Proton-GE par exemple).

```bash
flatpak install flathub com.vysp3r.ProtonPlus
```

Fonctionnalités : installation de Proton-GE, Wine-GE, custom versions ; support de Steam et Heroic ; interface simple.

## Codecs Multimédia

Par défaut, Fedora inclut uniquement des codecs libres (ffmpeg-free). Pour lire tous les formats multimédia courants (MP4, MKV, AVI, MP3, AAC, etc.), installer les codecs depuis RPM Fusion.

**Méthode recommandée (Fedora 41+) :**

```bash
sudo dnf group install multimedia
```

**Vérification :**

```bash
sudo dnf install vlc vlc-plugins-all
```

VLC est recommandé pour sa compatibilité étendue. Certains navigateurs peuvent nécessiter un redémarrage.

## Polices d'écriture

### 1. Polices libres recommandées

Fedora utilise déjà Noto comme base moderne. Compléter avec :

```bash
sudo dnf install \
  google-noto-sans-fonts \
  google-noto-serif-fonts \
  google-noto-mono-fonts \
  dejavu-sans-fonts \
  dejavu-serif-fonts \
  dejavu-sans-mono-fonts \
  liberation-sans-fonts \
  liberation-serif-fonts \
  liberation-mono-fonts \
  fira-code-fonts \
  jetbrains-mono-fonts
```

- **Noto** : excellente couverture Unicode, bon rendu (UI, web, langues non latines)
- **DejaVu + Liberation** : bonne compatibilité avec l'héritage Windows (Arial/Times/Courier)
- **Fira Code / JetBrains Mono** : adaptées pour le code (ligatures, clarté)

### 2. Dépôt Copr des fonts avec icônes

Pour l'affichage d'icones dans le texte (fastfetch, etc.) :

```bash
sudo dnf copr enable che/nerd-fonts
sudo dnf install nerd-fonts
```

### 3. Polices Microsoft "core fonts" (compatibilité documents)

Pour que les documents Office / sites web s'affichent « comme sous Windows » (Arial, Times New Roman, Calibri…) — installateur `msttcore-fonts-installer` du projet `mscorefonts2`.

**Prérequis :**

```bash
sudo dnf install curl cabextract xorg-x11-font-utils fontconfig
```

**Installer :**

```bash
curl -LO https://downloads.sourceforge.net/project/mscorefonts2/rpms/msttcore-fonts-installer-2.6-1.noarch.rpm
sudo rpm -ivh --nodigest --nofiledigest msttcore-fonts-installer-2.6-1.noarch.rpm
```

## Dépôts complémentaires

**AppStream (GNOME)** : métadonnées riches (icônes, descriptions, captures d'écran, catégories…) qui permettent à GNOME Software / KDE Discover d'afficher proprement les logiciels.

```bash
sudo dnf install rpmfusion-free-appstream-data rpmfusion-nonfree-appstream-data
```

**Paquets "tainted"** : catégorie spéciale pour les logiciels encore plus sensibles légalement (lecture de DVD chiffrés, certains firmwares soumis à brevets ou restrictions). Activés en connaissance de cause.

```bash
sudo dnf install rpmfusion-free-release-tainted rpmfusion-nonfree-release-tainted
```

## Noyau gaming CachyOS

**Intérêts du kernel CachyOS :**

- Scheduler BORE par défaut (réactivité, latence plus faible sur tasks interactives)
- Fréquence d'ordonnancement à 1000 Hz (régularité des frame times, input lag réduit)
- Patchs sur l'I/O (BFQ amélioré, mq-deadline, etc.) et gestion mémoire/zram
- Stack réseau tunée (BBRv3, optimisations)
- Intégration de modules gaming (ntsync pour Proton/Wine, support Steam Deck/ROG Ally)

**Dépôt COPR recommandé :** `bieszczaders`

```bash
sudo dnf copr enable bieszczaders/kernel-cachyos
sudo dnf install kernel-cachyos kernel-cachyos-devel-matched
```

## Fedora Steam Session

Pour une session SteamOS (comme sur Bazzite ou ChimeraOS) :
<https://github.com/shahnawazshahin/steam-using-gamescope-guide>

## Optimisation DNF

Réduire le temps de téléchargement des mises à jour, choisir automatiquement des miroirs plus rapides, éviter les rafraîchissements de métadonnées trop fréquents.

**Exemple de bloc `[main]` optimisé dans `/etc/dnf/dnf.conf` :**

```ini
[main]
gpgcheck=1
installonly_limit=3
clean_requirements_on_remove=True

# Optimisations
fastestmirror=True
max_parallel_downloads=10
metadata_timer_sync=7200
```

- `fastestmirror=True` : DNF teste les miroirs et privilégie les plus rapides
- `max_parallel_downloads=10` : jusqu'à 10 paquets en parallèle (3 par défaut)
- `metadata_timer_sync=7200` : rafraîchissement des métadonnées toutes les 2 h

**Tester :**

```bash
sudo dnf clean all
sudo dnf upgrade
```

---

*Résumé généré à partir de la note AFFiNE « Fedora Workstation ».*
