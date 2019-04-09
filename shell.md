# Bonnes pratiques de développement de scripts Shell Unix/Linux

## Règle 1 : Utiliser un éditeur évolué

:pushpin: **Objectif :** améliorer la maintenabilité et la robustesse.

Comme pour un langage comme Java ou C#, ... il est inconcevable de ne pas utiliser d'IDE. Un éditeur évolué propose :

* la coloration syntaxique.
* les contrôles de validation syntaxique.
* de l'outillage annexe (_ShellCheck_ par exemple).
* un éventuel terminal intégré.
* la possibilité de de contrôle du bon format de fichier. On conseillera d'utiliser l'encodage `UTF-8` (sans BOM) et évidemment les sauts de lignes `LF`.

:bulb: [Microsoft _Visual Studio Code_](https://vscodecandothat.com/) est par exemple un bon choix.

## Règle 2 : Utiliser les mêmes méthodes de développement qu'un projet classique

:pushpin: **Objectif :** améliorer la maintenabilité et la robustesse.

* Évidemment on utilise comme tout projet ou langage un outil de gestion de sources. [GIT](https://git-scm.com/book/fr/v2) est désormais le seul choix qui s'impose, avec un fichier `.gitattributes` correctement renseigné à la racine du dépôt, comportant par exemple les lignes suivantes :
  * `*.sh   text eol=lf`
  * `*.ksh   text eol=lf`
  * `*.bash   text eol=lf`
* Commenter sans paraphraser le code : expliquer le pourquoi par le comment.
* Soigner l'indentation.
* Favoriser les pratiques de revues collectives et de _Merge/Pull Request_.
* Utiliser les contrôles automatisés via l'intégration et/ou l'inspection continue.
* Tester et utiliser des bouchons ou des _mocks_.
* Utiliser les principes de développement tels que :
  * KISS (_Keep It Simple, Stupid_)
  * DRY (_Don't Repeat Yourself_)
  * YAGNI (_You Ain't Gonna Need It_)
  * SOC (_Separation Of Concerns_)
  * Fail-Fast (_signaler le plus rapidement possible une erreur._)
  * Règle du Boy-Scout (_Laisser le code plus propre qu'on ne l'a trouvé._)
  * etc...
* Limiter la taille des fonctions et des fichiers.

:bulb: Dans le cas des scripts Shell (comme pour des DDL ou SQL pour la base de données), **le livrable est à la fois la source**. C'est un avantage en ce qui concerne la gestion des versions et des livraisons que l'on peut directement et rapidement (pas d'outil, pas de compilation) effectuer via le gestionnaire de sources.

## Règle 3 : Utiliser une machine virtuelle

:pushpin: **Objectif :** améliorer la robustesse.

Sur des postes _Windows_ utiliser des machines virtuelles (via les outils Vagrant + VirtualBox par exemple) permet de tester les scripts sur un OS le plus proche possible de la cible et permet la découverte des défauts au plus tôt (gain de temps).

On peut imaginer se monter un environnement complet de test à l'image des systèmes cibles en profitant des avantages liés aux machines virtuelles que sont :

* la *reproductibilité* d'un poste à l'autre à l'identique ou  en cas de crash.
* l'*isolation* évitant les conflits de versions logicielles, de variables d'environnement, ...
* la *rapidité* d'initialisation et de mise à disposition d'un nouvel environnement.

:bulb: Évidemment on ne travaille pas directement sur les environnements cibles.

## Règle 4 : Utiliser la documentation

:pushpin: **Objectif :** améliorer la robustesse.

Celle-ci est accessible de différentes façons :

* l'aide interne : `<commande> --h` ou `<commande> --help`
* le manuel : `man <commande>` ou `help <commande>` pour les commandes de type _builtin_.
* l'outil en ligne [cheat.sh](https://cheat.sh/) ou via la ligne de commandes `curl http://cht.sh/<commande>`
* l'outil en ligne [ExplainShell](https://explainshell.com/) qui permet de détailler des commandes complètes.
* les différentes _cheat sheets_ ou _ref cards_ disponibles sur Internet (à imprimer et à garder à portée de main). Exemples :
  * <https://steve-parker.org/sh/cheatsheet.pdf>
  * <https://www.loggly.com/wp-content/uploads/2015/05/Linux-Cheat-Sheet-Sponsored-By-Loggly.pdf>
  * <https://www.git-tower.com/learn/cheat-sheets/cli>
* etc ....

## Règle 5 : Normaliser

:pushpin: **Objectif :** améliorer la maintenabilité et la robustesse.

* Partager les conventions entre tous les développeurs et les rendre facilement consultables (et modifiables).
* Utiliser les mêmes en-têtes et le même style de commentaires et de description des fonctions.
* Ajouter et configurer un fichier `.editorconfig` pour gérer vos normes en rajoutant un bloc `[*.sh]`.
* Normaliser le nommage de vos fichiers "bibliothèques" afin de pouvoir les identifier clairement. Par exemple : `lib_XXX.sh` (_librairies_), `func_XXXX.sh` (_functions_), `inc_XXXX.sh` (_includes_), etc...
* Nommer les constantes (et variables d'environnement) en majuscules avec underscores et les variables (et fonctions) en minuscules et ne pas mélanger les styles : `PascalCase`, `camelCase`, `snake_case`, `UPPERCASE`, `lowercase`.
* Préférer la syntaxe `${variable}` plutôt que `$variable` et s'y tenir partout (permet de rester homogène lorsqu'on utilise les techniques d'expansion `${BASH_VERSION%%.*}`).
* Éviter de mélanger les formes syntaxiques (déclaration de fonctions, structures de contrôles, utilisation d'une variable, ...). Les syntaxes à utiliser doivent être présentes dans vos documents de normes interne.
* Ne pas mélanger les différents interpréteurs, essayer de rester homogène dans tous vos scripts. L'interpréteur **bash** est un bon compromis entre sh (le plus compatible) et ksh (plus puissant) dont il reprend certains éléments.

## Règle 6 : Être explicite

:pushpin: **Objectif :** améliorer la maintenabilité et la robustesse.

* Utiliser des extensions de fichiers appropriées (même si n'elles n'ont aucune importance pour le système) : `.sh` pour les shells standards, `.ksh` si c'est un shell spécifique _Korn Shell_, etc ...
* Adapter également en conséquence, afin de lever l'ambiguïté, les en-têtes _shebang_ : `#!/bin/bash` (_on rappellera que celles-ci doivent obligatoirement être positionnées sur la première ligne du script, même avant n'importe quel autre commentaire ou même un espace_).
* Nommer clairement vos variables, (pseudo-)constantes, fonctions, scripts.
* Préférer attendre en entrée des arguments nommés :
  * Préférer `monscript --test --param=value` plutôt que `monscript test value` (syntaxe _GNU-style_).
  * Préférer `monscript -p1 value1 -p2 value2` plutôt que `monscript value1 value2` (syntaxe _getopts_).
* Quand ils existent utiliser les arguments de scripts externes ou de commandes avec des **noms longs**, c'est beaucoup plus clair et donc maintenabl. N'étant pas contraint par la taille des lignes c'est beaucoup plus clair et donc maintenable. Exemples :
  * Écrire `mvn clean install --batch-mode --quiet` plutôt que `mvn clean install -B -q`
  * Écrire `curl --request POST --header "content-type: application/json" --data "{\"param\": \"value\"}" http://site.org` plutôt que `curl -X POST -H "content-type: application/json" -d "{\"param\": \"value\"}" http://site.org`

## Règle 7 : Documenter

:pushpin: **Objectif :** améliorer la maintenabilité et la robustesse.

* Documenter vos sous-programmes et fonctions :
  * les entrées / sorties
  * les effets de bord (altération de données en entrée)
* Implémenter l'affichage de la version du script : `monscript --version` (standard GNU).
* Implémenter une aide en ligne : `monscript --help` (standard GNU).
  * utile pour l'utilisateur (... si maintenu à jour !)
  * force le développeur à expliquer son programme et donc à se poser des questions.
* Donner des exemples d'utilisation, produire des synoptiques, ...
* Documenter et partager vos processus, méthodes et normes internes :
  * soit au format Markdown dans votre dépôt
  * soit dans _Confluence_

## Règle 8 : Gérer les erreurs

:pushpin: **Objectif :** améliorer l'exploitabilité et la robustesse.

* Un code retour `0` (zéro) doit être renvoyé en cas de succès uniquement. En cas d'échec un code **supérieur** à 0 est renvoyé (on s'interdira donc les codes négatifs).
* Utiliser (et documenter) différents codes retours par types d'erreur, facilitant l'analyse ou l'automatisation de la gestion des erreurs. Exemples :
  * `1` ou `1x` ou `1xx` pour les erreurs de la ligne de commandes ou arguments attendus en entrée non présents, ...
  * `2` ou `2x` ou `2xx` pour les erreurs de validation (fichier attendu non présent, ...)
  * etc...
* Produire les messages d'erreur sur la sortie des erreurs : `echo "[ERREUR] ECHEC : $1" 1>&2;`.
* Produire des messages d'erreur clairs, détaillés et standardisés (par exemple pour pouvoir être analysés par un automate) permettant de guider l'utilisateur dans la résolution du problème.
* Tester tous les codes retour des commandes/scripts utilisés (même les plus évidentes et ne pas enchaîner les commandes si une commande précédente est en échec). Considérer éventuellement d'activer l'option `set -e`.
* S'assurer de la bonne fermeture de tous les fichiers ou toutes les connexions ouvertes avant l'arrêt du script.

:bulb: Pour forcer l'affichage d'un message sur le terminal même si une redirection est faite sur le script (ex: `1> log.txt`) on pourra utiliser `echo "message" > /dev/tty`.

## Règle 9 : Implémenter différents modes d'exécution

:pushpin: **Objectif :** améliorer l'exploitabilité et la robustesse.

Implémenter un mode d'auto-diagnostic, ou _Dry Run_ en anglais ou encore mode d'exécution à blanc permet :

* de valider la bonne installation du composant.
* de valider la configuration interne (constantes) ou externe (fichiers de paramétrage).
* de vérifier que tous les connexes sont bien disponibles ou accessibles (système de fichiers local, NAS, service distant, base de données, ...).

:warning: Évidemment ce mode ne doit travailler qu'en mémoire et ne faire que des appels en lecture (service, BDD, ...) :

* pas de création de fichier (autre que log)
* pas de modification / suppression de données

:bulb: Idéalement le vrai mode d'exécution ne doit pas être celui par défaut, évitant ainsi de lancer des actions irrémédiables et non désirées par inadvertance.
Ce mode de diagnostic (`--diag` par exemple) ou encore les modes `--help` ou `--version` sont des candidats possibles.

Implémenter un mode verbeux (`--verbose`) et un mode silencieux (`--quiet`) permettant de jouer sur le nombre d'informations affichées dans la console.

:warning: La sortie dans un fichier de journalisation ne doit pas être impactée par ce paramètre.

## Règle 9 : Sécuriser les exécutions

:pushpin: **Objectif :** améliorer la sécurité et la robustesse.

* Valider tous les entrants et tous les pré-requis en début de script, lever une erreur dès que possible. Cependant dans certains cas non critiques on pourra proposer des alternatives, des valeurs ou des comportements par défaut.
* Ne pas utiliser d'utilisateur à privilèges (`root`). Utiliser des comptes dont les droits sont **appropriés** au traitement à exécuter (ni plus ni moins).
* Poser les droits **appropriés** (jamais de `777` / `rwx`) sur les arborescences.
* Utiliser de façon **appropriée** les groupes et les comptes permettant d'intervenir chacun sur son arborescence.
* Borner de façon **appropriée** les possibilités du script en contrôlant l'utilisation des ressources système via la commande `ulimit` :
  * restreindre le nombre de processus simultanés via `ulimit -u <valeur>`
  * restreindre la création de fichiers _core dump_ via `ulimit -c <valeur>`
  * restreindre le temps processeur maximum en secondes via `ulimit -t <valeur>`
  * restreindre la  taille des fichiers écrits via `ulimit -f <valeur>`
* Appliquer la règle 8 et le principe _fail fast_ en **gérant les erreurs au plus tôt**.
* Appliquer la règle 9 en **diagnostiquant les exécutions au plus tôt** utiliser par exemple l'option `set -o noexec` (ou `bash -o noexec mon_script.sh`) pour valider les scripts.

## Règle 11 : Suivre les recommandations de _ShellCheck_

:pushpin: **Objectif :** améliorer la maintenabilité, l'exploitabilité, la sécurité, la performance et la robustesse.

:link: <https://www.shellcheck.net/>

_ShellCheck_ est un outil de contrôle de la syntaxe et d'analyse statique comportant un jeu de règles (+ de 320) consultable en ligne sur le [Wiki GitHub](https://github.com/koalaman/shellcheck/wiki/).

Cet outil est utilisable soit en ligne (par copier-coller du script) soit directement intégré à l'IDE, par exemple pour _MS Visual Studio Code_ il faut installer l'extension [`timonwong.shellcheck`](https://github.com/timonwong/vscode-shellcheck), celle-ci propose un fonctionnement comme **SonarLint** pour un projet Java par exemple avec le signalement des défauts à la volée.

:information_source:  _ShellCheck_ encourage grandement à respecter la norme **POSIX** ou **SUSv3** (plus complète).

:bulb: L'outil ShellCheck peut également être utilisé de façon automatisée par une ligne d'intégration continue : `shellcheck myscripts/*.sh`.

:bulb: Associé à l'outil _SonarQube_ celui-ci permet de suivre la qualité des scripts dans le temps (nombre de bugs, nombre de lignes de code, etc ...)

:link: <https://github.com/koalaman/shellcheck#in-your-editor>

## Annexes

### Quelques autres bonnes pratiques

:pushpin: Autres bonnes pratiques "en vrac" qu'il est bon de respecter.

* Préférer les déclarations de fonctions de la forme `nom_fonction() {}` plutôt que `function nom_fonction {}`.
* Préférer la syntaxe `var=$(commande)` plutôt que `` var=`command`` `.
* Contrôler la présence d'un fichier avec `-f` ou d'un dossier avec `-d` plutôt qu'avec `-e` (trop générique).
* Favoriser les chemins absolus plutôt que les chemins relatifs.
* Considérer la commande `printf` comme une alternative de meilleur choix à `echo` dans la plupart des cas.
* Préférer l'en-tête _Shebang_ `#!/bin/bash` dès que possible et limiter la dépendance à un interpréteur spécifique.
* Toujours préférer l'utilisation de variables entre guillemets `"${var}"` plutôt que `${var}` ... sauf dans certains cas ou il faut faire attention, par exemple `"${dir}/"*` (bien mettre `*` en dehors des guillemets).
* Limiter au strict minimum l'utilisation des variables globales.
* Favoriser les techniques d'expansion ou de substitution de variables plutôt que d'utiliser les pipes avec `sed`, `awk`, ...

### Checklists de contrôle

:pushpin: _Checklist_ utilisable avant de remonter un fichier dans le gestionnaire de sources.

* [ ] Fichier avec une extension cohérente `.sh` ou `.ksh`, ...
* [ ] Fichier au format `UTF-8` (avec accents) ou `US-ASCII` (sans accents).
* [ ] Présence de l'en-tête _shebang_ cohérente avec l'extension choisie.
* [ ] Les variables, fonctions et constantes sont correctement nommées et de façon homogène dans tout le script.
* [ ] Le script est documenté (en-tête avec auteur, date, description, ...), sans copier-coller non modifié.
* [ ] Les fonctions sont documentées (entrées / sorties / effets de bord).
* [ ] Les contrôles _ShellCheck_ ne relèvent plus de défaut.
* [ ] Les options de débogage sont désactivés.

:pushpin: _Checklist_ de contrôle de syntaxe permettant de détecter des erreurs "bêtes".

* [ ] Présence de l'en-tête _shebang_ **sur la première ligne**.
* [ ] Présence d'aucun espace de chaque côte du symbole d'affection d'une variable : `var=valeur`.
* [ ] Présence obligatoire d'espace autour des symboles de test `[` et `]` : `if [ -d $dir ]`.
* [ ] Présence obligatoire d'un `;` avant un `then` s'il est placé sur la même ligne que le `if`.
* [ ] Présence obligatoire d'un `;` avant un `do` s'il est placé sur la même ligne que le `for` ou le `while`.
* [ ] Présence obligatoire de `;;` à la fin de chaque _cas_ d'un `case` (pour le dernier aussi même si ce n'est pas obligatoire).

### Les interpréteurs de commandes Shell

L'interpréteur Shell gère l'invite de commandes et l'exécution de commandes et scripts. Il existe différents interpréteurs Shell dont les plus connus sont :

* **sh** : _Bourne Shell_ (écrit par Steve Bourne) l'ancêtre de tous les shells.
* **bash** : _Bourne Again Shell_ est une amélioration du Bourne Shell, disponible par défaut sous Linux et Mac OS X. **C'est généralement celui par défaut**.
* **ksh** : _Korn Shell_ (écrit par David G. Korn) est un shell puissant présent sur les Unix propriétaires (ex: AIX), mais aussi disponible en version libre depuis 2000 (installable par exemple via `yum install ksh` ou `apt-get install ksh`).
* **csh** : _C Shell_ un shell utilisant une syntaxe proche du langage C.

### Quelques options utiles lors de la mise en place d'un script

:pushpin: A placer en début de script après la ligne _shebang_, celles-ci peuvent être particulièrement utiles lors de la mise au point d'un script.

| Version courte | Version longue | Description |
| -------------- | -------------- | ----------- |
| `set -u` | `set -o nounset` | Ne pas autoriser les variables non définies. |
| `set -v` | `set -o verbose` | Affiche la ligne avant de l'exécuter. |
| `set -x` | `set -o xtrace` | Affiche l'exécution des commandes après traitement des caractères spéciaux (ex: $var). |
| `set -n` | `set -o noexec` | Permet la détection des erreurs de syntaxe via la lecture des commandes mais sans les exécuter. |
| `set -e` | `set -o errexit` | Force l'arrêt du script en cas d'erreur. |
| `set -C` | `set -o noclobber` | Avertissement quand une redirection va écraser un fichier existant. |
| | `set -o pipefail` | Le code retour n'est plus celui de la dernière commande exécutée par le _pipe_ mais la dernière à échouer ou 0 si aucune n'échoue. |

:bulb: Comme pour les arguments de commandes les versions longues sont à favoriser car plus parlantes. On utilisera `set -o`pour afficher la liste et l'état de chaque option (`on` / `off`).
