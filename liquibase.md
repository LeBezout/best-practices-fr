# Bonnes pratiques d'utilsiation de Liquibase

:bulb: [Site officiel - Page des _Best Practices_](http://www.liquibase.org/bestpractices.html)

## Règles fondamentales

* :warning: **Ne jamais intervenir manuellement sur le schéma de base.** Toute modification doit entraîner la création d'un nouveau changeset.
* :warning: **Un _changeset_ est IMMUABLE.** Si celui-ci a déjà été exécuté sur un des environnements projet il ne doit plus jamais être modifié dans le fichier changelogs.

## Bonnes pratiques

* Favoriser le format XML pour l'écriture des fichiers _changelogs_, ce format est connu de tous (dev, ops, AD) et ne nécessite pas de dépendances externes (fichiers jar).
* Utiliser un contexte et des fichiers dédiés pour créer des jeux de tests.
* Prévoir pour chaque changeset son rollback. Se baser sur la documentation officielle car dans la majorité des cas il n'y aura rien à prévoir.
* Prévoir dans les changelogs une compatibilité avec différents systèmes, par exemple une cible Oracle, un poste de développement avec MySQL et des tests unitaires exécutés sur une base H2 ou HSQL.
* Décorréler l'exécution de Liquibase du déploiement applicatif (même si c'est très pratique). Intégrer cette exécution comme une étape indépendante du processus de mise à jour de l'application. L'analyse des problèmes n'en sera que facilité.
* Utiliser un projet (voir même un dépôt GIT) dédié pour stocker les sources des changelogs et packager celui-ci sous forme d'un module Maven.
* Ecrire une classe de test utilisant une base de données "in memory" permettant de valider les fichiers changelogs.
* Définir les changements de la manière la plus élémentaire possible (1 changement = 1 changeset) ainsi le code de rollback est plus facile à implémenter.
* Implémenter un élément (servlet, service rest, ...) permettant de connaître l'état de la base de données.
* L'attribut `logicalFilePath` d'un fichier _changelog_ doit juste contenir le nom du fichier.
