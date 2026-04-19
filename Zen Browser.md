## Tutoriel de configuration Zen Browser

Ce tutoriel reformate les étapes pour personnaliser Zen Browser en supprimant les sites suggérés, en autorisant les pages de nouvel onglet personnalisées et en affichant la barre personnelle. Les icônes ajoutées facilitent la navigation visuelle des étapes.

## 🗑️ Étape 1 : Supprimer les suggestions

Installez le mod 

```bash
No Top Sites
```
depuis zen-browser.app/mods pour vider la liste des sites suggérés dans la barre d'adresse. Ce mod cible spécifiquement les top sites sans impact sur d'autres éléments.

## 🔓 Étape 2 : Activer nouvel onglet

Tapez 

```bash
about:config
```
acceptez l'avertissement, cherchez 

```bash
zen.urlbar.replace-newtab
```
et réglez sur `false`. Redémarrez Zen Browser pour permettre aux extensions de personnaliser la page de nouvel onglet.

## 📋 Étape 3 : Afficher barre personnelle

Dans `about:config`, recherchez `zen.view.hide-window-controls` et passez à `false`. Cela révèle la barre d'outils personnelle en mode compact (barre unique).



Activer la barre de titre (bordure système)

La bordure de fenêtre standard est fournie par votre système (comme KDE sous Linux). Pour l'activer :

    Cliquez droit sur la barre d'outils du navigateur.

    Sélectionnez Personnaliser la barre d'outils.

    Activez l'option Title bar (barre de titre).
    Cela ajoute une bordure classique en haut de la fenêtre pour une cohérence avec votre environnement de bureau.
