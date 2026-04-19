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
