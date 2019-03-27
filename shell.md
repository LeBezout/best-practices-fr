# Bonnes pratiques de développement de scripts Shell Unix/Linux

## Règle 1 : Utiliser un éditeur évolué

:pushpin: Améliore la maintenabilité et la robustesse

Comme pour un langage comme Java ou C#, ... il est inconcevable de ne pas utiliser d'IDE. Un éditeur évolué propose :

* la coloration syntaxique
* les contrôles de validation syntaxique
* de l'outillage annexe (_ShellCheck_ par exemple)
* un éventuel terminal intégré
* contrôle du bon format de fichier : utiliser l'encodage `UTF-8` (sans BOM) et évidemment les sauts de lignes `LF`

:bulb: [Microsoft _Visual Studio Code_](https://vscodecandothat.com/) est par exemple un bon choix.

## Règle 2 : Utiliser les mêmes méthodes de développement qu'un projet classique

:pushpin: Améliore la maintenabilité et la robustesse

* Évidemment on utilise comme tout projet ou langage un outil de gestion de sources. [GIT](https://git-scm.com/book/fr/v2) est désormais le seul choix qui s'impose, avec un fichier `.gitattributes` correctement renseigné à la racine du dépôt
  * `*.sh   text eol=lf`
  * `*.ksh   text eol=lf`
  * `*.bash   text eol=lf`
* Favoriser les pratiques de revues collectives et de _Merge/Pull Request_
* Utiliser les contrôles automatisés via l'intégration et/ou l'inspection continue
* Tester et utiliser des bouchons ou des _mocks_
* Utiliser les principes de développement KISS, DRY, YAGNI, Fail-Fast, ...

## Règle 3 : Utiliser une machine virtuelle

:pushpin: Améliore la robustesse

Sur des postes Windows utiliser des machines virtuelles (via les outils Vagrant + VirtualBox par exemple) permet de tester les scripts sur un OS le plus proche possible de la cible et permet la découverte des défauts au plus tôt (gain de temps).

On peut imaginer se monter un environnement complet de test à l'image des systèmes cibles en profitant des avantages liés aux machines virtuelles :

* **Reproductibilité** : permet de reproduire d'un poste à l'autre à l'identique ou  en cas de crash
* **Isolation** : permet d'éviter les conflits de versions logicielles, de variables d'environnement, ...
* **Rapidité** : permet d'initialiser rapidement un nouvel environnement

:bulb: Évidemment on ne travaille pas directement sur les environnements cibles.

## Règle 4 : Utiliser la documentation

:pushpin: Améliore la robustesse

Celle-ci est accessible de différentes façons :

* l'aide interne : `<commande> --help`
* le manuel : `man <commande>`
* l'outil en ligne [cheat.sh](https://cheat.sh/) ou via la ligne de commandes `curl http://cht.sh/<commande>`
* les différentes _cheat sheets_ disponibles sur Internet (à imprimer et à garder à portée de main)
* etc ....

## Règle 5 : Normaliser

:pushpin: Améliore la maintenabilité et la robustesse

* Partager les conventions entre tous les développeurs et les rendre facilement consultables (voir modifiables)
* Utiliser les mêmes en-têtes et le même style de commentaires et de description des fonctions
* Ajouter et configurer un fichier `.editorconfig` pour gérer vos normes en rajoutant un bloc `[*.sh]`
* Normaliser le nommage de vos fichiers "bibliothèques" afin de les identifier clairement. Par exemple : `lib_XXX.sh`, `func_XXXX.sh`, etc... 
* Nommer les constantes en majuscules et les variables en minuscules
* Préférer la syntaxe `${variable}` plutôt que `$variable` et s'y tenir partout

## Règle 6 : Être explicite

:pushpin: Améliore la maintenabilité et la robustesse

* Utiliser des extensions de fichiers appropriées : `.sh` pour les shells standards, `.ksh` si c'est un shell spécifique _Korn Shell_, etc ... et adapter également en conséquence les en-têtes _Shebang_ : `#!/bin/sh`
* Nommer clairement vos variables, (pseudo-)constantes, fonctions, scripts
* Préférer attendre en entrée des arguments nommés :
  * `monscript --test --param=value` plutôt que `monscript test value` (syntaxe _GNU-style_)
  * `monscript -p1 value1 -p2 value2` plutôt que `monscript value1 value2` (syntaxe _getopts_)
* Quand ils existent utiliser les arguments de scripts externes ou de commandes avec des **noms longs**, c'est beaucoup plus clair et donc maintenable. Exemples :
  * `mvn clean install --batch-mode --quiet` plutôt que `mvn clean install -B -q`
  * `curl --request POST --header "content-type: application/json" --data "{\"param\": \"value\"}" http://site.org` plutôt que `curl -X POST -H "content-type: application/json" -d "{\"param\": \"value\"}" http://site.org`

## Règle 7 : Documenter

:pushpin: Améliore la maintenabilité et la robustesse

* Documenter vos sous-programmes et fonctions :
  * les entrées / sorties
  * les effets de bord (altération de données en entrée)
* Implémenter une aide en ligne : `monscript --help`
  * utile pour l'utilisateur (... si maintenu à jour !)
  * force le développeur à expliquer son programme et donc à se poser des questions
* Donner des exemples d'utilisation, produire des synoptiques, ...
* Documenter vos process et normes internes
  * soit au format Markdown dans votre dépôt
  * soit dans _Confluence_

## Règle 8 : Implémenter un mode d'auto-diagnostic

:pushpin: Améliore l'exploitabilité et la robustesse

Implémenter un mode d'auto-diagnostic, ou _Dry Run_ en anglais ou encore mode d'exécution à blanc permet :

* de valider l'installation du composant
* de valider la configuration interne (constantes) ou externe (fichiers de paramétrage)
* de vérifier que tous les connexes sont bien disponibles ou accessibles (système de fichiers local, NAS, service distant, base de données, ...)

:warning: Évidemment ce mode ne doit travailler qu'en mémoire et ne faire que des appels en lecture (service, BDD, ...) :

* pas de création de fichier (autre que log)
* pas de modification de données

:bulb: Idéalement le vrai mode d'exécution ne doit pas être celui par défaut, évitant ainsi de lancer des actions irrémédiables et non désirées par inadvertance.
Ce mode de diagnostic ou encore les modes `--help` ou `--version` sont des candidats possibles.

## Règle 9 : Suivre les recommandations de _ShellCheck_

:pushpin: Améliore la maintenabilité, l'exploitabilité, la sécurité, la performance et la robustesse

:link: <https://www.shellcheck.net/>

_ShellCheck_ est un outil de contrôle de la syntaxe comportant un jeu de règles consultable en ligne.

Cet outil est utilisable soit en ligne (par copier-coller du script) soit directement intégré à l'IDE, par exemple pour _MS Visual Studio Code_ il faut installer l'extension [`timonwong.shellcheck`](https://github.com/timonwong/vscode-shellcheck).

:link: <https://github.com/koalaman/shellcheck#in-your-editor>

## Annexes

### Checklist de contrôle

:pushpin: _Checklist_ utilisable avant de remonter un fichier dans le gestionnaire de sources

* [ ] Extension `.sh` ou `.ksh`, ...
* [ ] Fichier au format `UTF-8` (avec accents) ou `US-ASCII` (sans accents)
* [ ] Présence de l'en-tête _Shebang_ cohérente avec l'extension
* [ ] Les variables, fonctions et constantes sont correctement nommées
* [ ] Le script est documenté (en-tête avec auteur, date, description, ...)
* [ ] Les fonctions sont documentées (entrées / sorties / effets de bord)
* [ ] Les contrôles _ShellCheck_ ne relèvent plus de défaut
