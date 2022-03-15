# Les bonnes pratiques du développeur

:pushpin: Cette page présente quelques bonnes pratiques globales au métier de développeur.

Celles-ci doivent permette :

* de s'épanouir dans son travail
* de collaborer et partager
* de s'améliorer continuellement
* de gagner en efficacité

:information_source: Le but de cette page n'est pas documentaire, elle est simplement là dans le but d'éveiller la curiosité ou une réflexion sur ses pratiques personnelles.

## Optimiser son poste de travail pour gagner en confort et en efficacité

* Utiliser des outils adaptés et récents.
* Favoriser les environnements de développement automatisables (documentés et que l'on peut reconstruire simplement et rapidement).
* Scripter les tâches récurrentes ou à faible valeur ajoutée.
* Utiliser les outils de feedback rapide permettant d'améliorer la qualité : SonarLint, Code Coverage, fonctionnalité d'Inspection du code dans IntelliJ, ShellCheck pour les scripts shell, tous les Linters (MD, JS, TS, ...), ...
* Appliquer les principes du _Clean Code_ et plus généralement du _Software Craftsmanship_ quelle que soit la technologie (java, shell, web, php, ...).

## Principes S.O.L.I.D.

* Règles du Boy Scout ou de la fenêtre cassée, ...
* Principes DRY, KISS, YAGNI, SOC, ...
* Nommage évocateur, méthodes courtes, ...

## Profiter des apports des outils Git et GitLab/GitHub

* Favoriser le mode d'authentification par clef SSH.
* Favoriser l’utilisation des feature branch et des _Merge/Pull Request_ et pousser régulièrement vos modifications pour éviter de perdre votre travail en cas de crash.
* Apprendre à utiliser les commandes de base (clone, push, pull, fetch, rebase, merge, config, log, status).
* Produire des fichiers README au format Markdown à la racine de vos dépôts pour décrire chaque projet.

## S'approprier le cycle de vie des applications

* Savoir bien distinguer les différentes phases : Construction / Fabrication, Livraison, Installation / Déploiement.
* Connaître les outils adaptés aux différentes fonctions (GitLab-CI, Jenkins, ...).
* Connaître les équipes support derrières ces outils dans votre organisation.

## Travailler à plusieurs pour favoriser l'appropriation collective

* Pratique du Pair ou Mob Programming.
* Pratique des _Merge/Pull Request_.
* Pratique des revues de code collectives.

## "Write all things"

* Il est important de pouvoir tout noter, tracer rapidement, dans l'instant pour ne rien oublier et de pouvoir y revenir plus tard en utilisant par exemples des outils comme Trello, Evernote, TodoList, ....
* Il faut également documenter tous les choix d'architecture ou d'implémentation détaillant les contraintes et/ou les impératifs de chaque situation.
* Détailler également tous les problèmes rencontrés permet de mieux comprendre comment on est arrivée à la solution mise en oeuvre.
* Envisager l'écriture d'ADR (_Architectural Decision Records_) pour assurer l'historique et maintenir la connaissance sur le projet.

## Etre centré sur la qualité

* Toujours chercher à produire du travail de qualité.
* Appliquer et insuffler dans l'équipe les bonnes pratiques.
* S'impliquer dans les sujets et creuser les problématiques quitte à remettre en question certains choix.

## Partager avec ses pairs

* Partager avec les communautés des développeurs.
* Documenter / capitaliser.

## Gérer ses tâches et ne pas laisser traîner celles rapides à exécuter

* L'important est que toute tâche courte (par exemple d'une durée inférieure à 5 minutes) soit faite immédiatement (ou quasiment) et ne soit pas reportée. Voir méthode [GTD (_Get Things Done_)](https://everlaab.com/comment-augmenter-sa-productivite-avec-la-methode-gtd/) de David Allen.
* Importantes ou pas elles devront être faites donc il faut éviter d'encombrer sa _todo list_ et son esprit en les évacuant rapidement. Plus on a de tâches à réaliser, plus notre mémoire est sollicitée et donc plus on est préoccupé.
* Pour toutes les autres tâches (donc les plus longues) il faut utiliser un outil de gestion et effectuer un classement via la [matrice d'Eisenhower](https://chef-de-projet.fr/matrice-eisenhower/)

## Élargir son spectre et prendre du recul

* Essayer d'avoir une vision globale en ne se limitant pas à son besoin ou son projet.
* Se renseigner si une solution n'existe pas déjà ailleurs ou de manière globale.
* Demander l'avis, voire la validation, des équipes support et d'architecture avant de partir sur une solution technique.
* Ne pas aller tout le temps sur Internet si une solution interne existe (repo maven ou npm, dockerhub, outillage, ...).

## Participer à des événements ou conférences

* Pratiquer des Coding Dojos avec d'autres développeurs.
* Suivre l'actualité et participer aux différentes communautés.
* Tester de nouvelles choses, de nouvelles façons de faire, explorer de nouvelles pistes, ...
* Contribuer aux projets Open Source que l'on utilise (Spring, Liquibase, ...) : Issues voire Pull Request.

## Ne pas rester bloqué

* Faire intervenir la communauté des développeurs.
* Demander le support à ses référents techniques (Tech Lead / DevOps).
* Remonter les alertes à son CP / PO / N+1.
