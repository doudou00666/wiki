### Localiser les presets et la config

On vérifie ouù sont les presets :

```bash
fastfetch --list-data-paths
```

Généralement on le trouve ici :  

```bash
/usr/share/fastfetch/presets/
```
ou là 

```bash
~/.local/share/fastfetch/presets/
```

Le fichier de config de l'utilisateur par défault se trouve ici : 

```bash
~/.config/fastfetch/config.jsonc
```

Si pas de dossier 

```bash
~/.config/fastfetch/config.jsonc
```
il faut le générer en faisant :

```bash
mkdir -p ~/.config/fastfetch
fastfetch --gen-config
```

ça créer le fichier  **_config.jsonc_** avec le stric minimal


### Parcourir les exemples ###

Pour listeer les presets de fastetch on fais la commande suivante : 

```bash
fastfetch --list-presets
```
Si tu veux tester du tape la commande suivante :

```bash
fastfetch --config examples/13.jsonc
```
Mettre le script pour modfier le fastfetch 

```bash

// Inspired by Catnap
{
    "$schema": "https://github.com/fastfetch-cli/fastfetch/raw/dev/doc/json_schema.json",
    "logo": {
        "type": "small",
        "padding": {
            "top": 1
        }
    },
    "display": {
        "separator": " "
    },
    "modules": [
        {
            "key": "╭───────────╮",
            "type": "custom"
        },
        {
            "key": "│ {#31} user    {#keys}│",
            "type": "title",
            "format": "{user-name}"
        },
        {
            "key": "│ {#32}󰇅 hname   {#keys}│",
            "type": "title",
            "format": "{host-name}"
        },
        {
            "key": "│ {#33}󰅐 uptime  {#keys}│",
            "type": "uptime"
        },
        {
            "key": "│ {#34}󰧱 age     {#keys}│",
            "type": "command",
            "shell": "bash",
            "text": "birth_install=$(stat -c %W /); current=$(date +%s); days_difference=$(( (current - birth_install) / 86400 )); echo \"${days_difference} jours\""
        },
        {
            "key": "│ {#34}{icon} distro  {#keys}│",
            "type": "os"
        },
        {
            "key": "│ {#35} kernel  {#keys}│",
            "type": "kernel"
        },
        {
            "key": "│ {#36}󰇄 desktop {#keys}│",
            "type": "de"
        },
        {
            "key": "│ {#31}󰖟 session {#keys}│",
            "type": "command",
            "shell": "bash",
            "text": "case \"${XDG_SESSION_TYPE:-}\" in wayland) echo Wayland ;; x11) echo X11 ;; *) echo Unknown ;; esac"
        },
        {
            "key": "│ {#31} term    {#keys}│",
            "type": "terminal"
        },
        {
            "key": "│ {#32} shell   {#keys}│",
            "type": "shell"
        },
        {
            "key": "│ {#33}󰍛 cpu     {#keys}│",
            "type": "cpu",
            "showPeCoreCount": true
        },
        {
            "key": "│ {#34}󰉉 disk    {#keys}│",
            "type": "disk",
            "folders": "/"
        },
        {
            "key": "│ {#35} memory  {#keys}│",
            "type": "memory"
        },
        {
            "key": "│ {#36}󰩟 network {#keys}│",
            "type": "localip",
            "format": "{ipv4} ({ifname})"
        },
        {
            "key": "├───────────┤",
            "type": "custom"
        },
        {
            "key": "│ {#39} colors  {#keys}│",
            "type": "colors",
            "symbol": "circle"
        },
        {
            "key": "╰───────────╯",
            "type": "custom"
        }
    ]
}
```
### Ajouter Fastetch au démarrage du terminal

```bash
sudo nano ~/.bashrc
```
en bas du fichier tu ajoute le ligne suivante :

```bash
fastfetch
```
Tu recharges ce fichier

```bash
source ~/.bashrc
```
Si tu es en zsh (Cachyos) :

```bash
sudo nano nano ~/.zshrc
```
Tu rajoutes en bas

```bash
fastfetch
```

Tu recharges :

```bash
source ~/.zshrc
```

Pour que fastfetch se lance à chaque fois que j'ouvre le terminal avec fish il faut modifié le fichier de config :

```bash
sudo nano ~/.config/fish/config.fish
```
et je rajoute

```bash
fastfetch
```

et supprimer les ligne de bienvenue et type hel il faut rajouté dans le fichier config de fish :

```bash
sudo nano ~/.config/fish/config.fish
```
et on rajoute :

```bash
set -g fish_greeting ""
```

et la commande vérif comme quoi cela merche 

```bash
exec fish
```




