# Bonnes pratiques de développement de scripts Shell Unix/Linux

## Utiliser un éditeur évolué

> Améliore la maintenabilité

Comme pour un langage comme Java ou C#, ... il est inconcevable de ne pas utiliser d'IDE. Un éditeur évolué propose :

* la coloration syntaxique
* les contrôles de validation syntaxique
* de l'outillage annexe (shellcheck par exemple)
* un éventuel terminal intégré

:bulb: [Microsoft _Visual Studio Code_](https://vscodecandothat.com/) est par exemple un bon choix.

## Suivre les recommendations de _ShellCheck_

> Améliore la maintenabilité, l'exploitabilité, la sécurité, la performance et la robustesse

:link: <https://www.shellcheck.net/>

_ShellCheck_ est un outil de contrôle de la syntaxe comportant un jeu de règles consutable en ligne.

Cet outil est utilisable soit en ligne (par copier-coller du script) doit directement intégré à l'IDE, par exemple pour _MS Visual Studio Code_ installer l'extension [`timonwong.shellcheck`](https://github.com/timonwong/vscode-shellcheck).

:link: <https://github.com/koalaman/shellcheck#in-your-editor>

## Utiliser une machine virtuelle

> Améliore la robustesse

Sur postes Windows utiliser des machines virtuelles pour tester les scripts sur un OS le plus proche possible de la cible.

## Utiliser la documentation

* `<commande> --help`
* `man <commande>`
* Outil en ligne comme [cheat.sh](https://cheat.sh/)
* ou en ligne de commandes `curl http://cht.sh/<commande>`
* les différentes _cheat sheets_ disponibles sur Internet
* etc ....

## Normaliser

> Améliore la maintenabilité et la robustesse

* Partager les conventions entre tous les développeurs et les rendre facilement consultables
* Utiliser les mêmes en-tête et le même style de commentaires et de description des fonctions
* Ajouter et configurer un fichier `.editorconfig` pour gérer vos normes en rajoutant un bloc `[*.sh]`
* Nommer les constantes en majuscules
* Préférer la syntaxe `${variable}` plutôt que `$variable` et s'y tenir partout

## Etre explicite

> Améliore la maintenabilité et la robustesse

* Nommer clairement vos variables, (pseudo-)constantes, fonctions, scripts
* Quand ils existent utiliser les arguments de scripts ou de commandes avec des **noms longs**, c'est beaucoup plus clair et donc maintenable. Exemples :
  * `mvn clean install --batch-mode --quiet` plutôt que `mvn clean install -B -q`
  * `curl --request POST --header "content-type: application/json" --data "{\"param\": \"value\"}" http://site.org` plutôt que `curl -X POST -H "content-type: application/json" -d "{\"param\": \"value\"}" http://site.org`
  
_à compléter_
