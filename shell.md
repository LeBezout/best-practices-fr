# Bonnes pratiques de développement de scripts Shell Unix/Linux

## Utiliser un éditeur évolué

> Améliore la maintenabilité et la robustesse

Comme pour un langage comme Java ou C#, ... il est inconcevable de ne pas utiliser d'IDE. Un éditeur évolué propose :

* la coloration syntaxique
* les contrôles de validation syntaxique
* de l'outillage annexe (shellcheck par exemple)
* un éventuel terminal intégré

:bulb: [Microsoft _Visual Studio Code_](https://vscodecandothat.com/) est par exemple un bon choix.

## Utiliser une machine virtuelle

> Améliore la robustesse

Sur des postes Windows utiliser des machines virtuelles pour tester les scripts sur un OS le plus proche possible de la cible.

On peut imaginer se monter un environnement complet de test à l'image des systèmes cibles en profitant des avantages liés aux machines virtuelles :

* **Reproductibilité** : permet de reproduire d'un poste à l'autre à l'identique ou  en cas de crash
* **Isolation** : permet d'éviter les conflits de versions logicielles, de variables d'environnement, ...
* **Rapidité** : permet d'initialiser rapidement un nouvel environnement

## Utiliser la documentation

Celle-ci est accessible de différentes façons :

* `<commande> --help`
* `man <commande>`
* l'outil en ligne https://cheat.sh/[cheat.sh] ou via la ligne de commandes `curl http://cht.sh/<commande>`
* les différentes _cheat sheets_ disponibles sur Internet
* etc ....

## Normaliser

> Améliore la maintenabilité et la robustesse

* Partager les conventions entre tous les développeurs et les rendre facilement consultables
* Utiliser les mêmes en-tête et le même style de commentaires et de description des fonctions
* Ajouter et configurer un fichier `.editorconfig` pour gérer vos normes en rajoutant un bloc `[*.sh]`
* Normaliser le nommage de vos fichiers "bibliothèques" afin de les identifier clairement. Par exemple : `lib_XXX.sh`, `func_XXXX.sh`, etc... 
* Nommer les constantes en majuscules et les variables en minuscules
* Préférer la syntaxe `${variable}` plutôt que `$variable` et s'y tenir partout
* Utiliser des entensions de fichiers appropriées : `.sh` pour les shells standards, `.ksh` si c'est un shell spécifique _Korn Shell_, etc ...

## Être explicite

> Améliore la maintenabilité et la robustesse

* Nommer clairement vos variables, (pseudo-)constantes, fonctions, scripts
* Quand ils existent utiliser les arguments de scripts ou de commandes avec des **noms longs**, c'est beaucoup plus clair et donc maintenable. Exemples :
  * `mvn clean install --batch-mode --quiet` plutôt que `mvn clean install -B -q`
  * `curl --request POST --header "content-type: application/json" --data "{\"param\": \"value\"}" http://site.org` plutôt que `curl -X POST -H "content-type: application/json" -d "{\"param\": \"value\"}" http://site.org`

## Suivre les recommandations de _ShellCheck_

> Améliore la maintenabilité, l'exploitabilité, la sécurité, la performance et la robustesse

:link: <https://www.shellcheck.net/>

_ShellCheck_ est un outil de contrôle de la syntaxe comportant un jeu de règles consutable en ligne.

Cet outil est utilisable soit en ligne (par copier-coller du script) soit directement intégré à l'IDE, par exemple pour _MS Visual Studio Code_ il faut installer l'extension [`timonwong.shellcheck`](https://github.com/timonwong/vscode-shellcheck).

:link: <https://github.com/koalaman/shellcheck#in-your-editor>
