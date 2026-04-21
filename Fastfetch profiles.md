# Fastfetch profiles

Voici un petit guide « de A à Z » pour parcourir les exemples Fastfetch et en copier un comme profil actuel.

## 1. Localiser les presets et la config

1. Vérifie où sont les presets sur ta machine :
   `fastfetch --list-data-paths` (facultatif mais pratique).​
2. Classiquement, tu les trouveras ici :
   * `/usr/share/fastfetch/presets/`
   * éventuellement `~/.local/share/fastfetch/presets/`.
3. Le fichier de config utilisateur par défaut est :
   `~/.config/fastfetch/config.jsonc`.

Si `~/.config/fastfetch/config.jsonc` n’existe pas, génère-le une fois :

```
mkdir -p ~/.config/fastfetch
fastfetch --gen-config
```

Cela crée un **config.jsonc** minimal dans `~/.config/fastfetch/`.

## 2. Parcourir les exemples

1. Liste les presets connus par Fastfetch :Les noms listés sont ceux que tu peux utiliser avec `--config`.
   ```
   fastfetch --list-presets 
   ```
2. Pour tester un preset **sans rien écraser**, lance par exemple :ou, si c’est juste `examples/13` dans la liste :Tu peux enchaîner comme ça avec les autres presets jusqu’à trouver celui qui te plaît.
   ```
   fastfetch --config examples/13.jsonc 
   ```
   ```
   fastfetch --config examples/13 
   ```

## 3. Copier un exemple vers la config actuelle

Une fois que tu as choisi un exemple (par ex. `examples/13.jsonc`) :

1. Repère son chemin réel, typiquement :
   `/usr/share/fastfetch/presets/examples/13.jsonc`.
2. Sauvegarde éventuellement ta config actuelle :
   ```
   mkdir -p ~/.config/fastfetch
   cp ~/.config/fastfetch/config.jsonc ~/.config/fastfetch/config.backup.jsonc

   ```
3. Copie le preset choisi comme nouvelle config par défaut :(adapte le chemin si nécessaire selon ta distro).
   ```
   cp /usr/share/fastfetch/presets/examples/13.jsonc \
      ~/.config/fastfetch/config.jsonc
   ```

À partir de là, un simple `fastfetch` utilisera ce profil, que tu pourras ensuite éditer directement dans `~/.config/fastfetch/config.jsonc` (nano, vim, etc.).

Profil chomiam fastfetch

```shellscript
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
