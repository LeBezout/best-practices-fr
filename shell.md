# Bonnes pratiques de développement scripts Shell Unix/Linux

## Utiliser un éditeur évolué

Un éditeur évolué propose :

* la coloration syntaxique
* les contrôles de validation syntaxique
* de l'outillage annexe
* un éventuel terminal intégré

## Suivre les recommendations de _ShellCCheck_

:link: <https://www.shellcheck.net/>

Soit en ligne (par copier-coller) doit directement intégré à l'IDE, par MS Visual Studio Code installer l'extension `timonwong.shellcheck`.

:link: <https://github.com/koalaman/shellcheck#in-your-editor>

## Utiliser une machine virtuelle

Sur postes Windows utiliser des machines virtuelles pour tester les scripts sur un OS le plus proche possible de la cible.

## Utiliser la documentation

* `<commande> --help`
* `man <commande>`
* Outil en ligne comme [cheat.sh](https://cheat.sh/)
* Ou en ligne de commande `curl http://cht.sh/<command>`
* etc ....

## Normaliser

* Partager les conventions
* Utiliser les mêmes en-tête et le même style de commentaires et de descritpion des fonctions


__in progress__
