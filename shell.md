# Bonnes pratiques de développement scripts Shell Unix/Linux

## Utiliser un éditeur évolué

Un éditeur évolué propose :

* la coloration syntaxique
* les contrôles de validation syntaxique
* de l'outillage annexe (shellcheck par exemple)
* un éventuel terminal intégré

## Suivre les recommendations de _ShellCheck_

:link: <https://www.shellcheck.net/>

_ShellCheck_ est un outil de contrôle de la syntaxe comportant un jeu de règles consutable en ligne.

Cet outil est utilisable soit en ligne (par copier-coller du script) doit directement intégré à l'IDE, par exemple pour _MS Visual Studio Code_ installer l'extension [`timonwong.shellcheck`](https://github.com/timonwong/vscode-shellcheck).

:link: <https://github.com/koalaman/shellcheck#in-your-editor>

## Utiliser une machine virtuelle

Sur postes Windows utiliser des machines virtuelles pour tester les scripts sur un OS le plus proche possible de la cible.

## Utiliser la documentation

* `<commande> --help`
* `man <commande>`
* Outil en ligne comme [cheat.sh](https://cheat.sh/)
* ou en ligne de commandes `curl http://cht.sh/<command>`
* CheatSheets disponibles sur Internet
* etc ....

## Normaliser

* Partager les conventions
* Utiliser les mêmes en-tête et le même style de commentaires et de descritpion des fonctions
* Ajouter ou configurer un fichier `.editorconfig` pour gérer vos normes en rajoutant un bloc `[*.sh]`.

__à compléter__
