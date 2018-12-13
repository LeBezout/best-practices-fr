# Bonnes pratiques d'utilsiation de Liquibase

:bulb: [Site officiel - Page des _Best Practices_](http://www.liquibase.org/bestpractices.html)

## Rappel des notions clefs

### Changelog

C'est le **catalogue** séquentiel des opérations à appliquer sur une base de données. Ces opérations sont organisées par lots les plus cohérents et consistants possibles.

### Changeset

C'est un **lot d'opérations** à appliquer sur la base de données. Ce lot pourra bien souvent se résumer à une seule opération (conseillé).

### Context

Les contextes sont des **étiquettes** permettant de contrôler les changements à appliquer. Cette information peut être appliquée au niveau de l'inclusion d'un changelog ou plus finement au niveau d'un changeset.

:bulb: Utiliser cette notion pour créer des jeux de données pour vos tests unitaires et l'intégration continue.

## Avantages de la solution

* **Traçabilité** : historique complet des changements appliqués
* **Intégrité et cohérence** : cohérence dans l'application des changements et suivi des versions applicatives
* **Reproductibilité :** solution reproductible d'un environnement à l'autre à l'identique
* **Sécurité :** mise à niveau d'un schéma, possibilité de retour à un état précédent, ...

:bulb: Son utilisation est fortement conseillée et est même indispensable dans un contexte DevOps.

## Règles fondamentales

* :warning: **Ne jamais intervenir manuellement sur le schéma de base.** Toute modification doit entraîner la création d'un nouveau changeset.
* :warning: **Un _changeset_ est IMMUABLE.** Si celui-ci a déjà été exécuté sur un des environnements projet il ne doit plus jamais être modifié dans le fichier changelogs.

## Bonnes pratiques

* Favoriser le format XML pour l'écriture des fichiers _changelogs_, ce format est connu de tous (dev, ops, AD) et ne nécessite pas de dépendances externes (fichiers jar).
* Organiser vos fichiers de _changelogs_ avec un fichier principal et des fichiers par version applicative comme il est indiqué dans les bonnes pratiques de l'outil (on peut également isoler les données, de test ou d'initialisation tel que des paramètres, dans un dossier dédié, par exemple _data_).
* Utiliser un contexte et des fichiers dédiés pour créer des jeux de tests.
* Prévoir pour chaque _changeset_ son rollback. Se baser sur la documentation officielle car dans la majorité des cas il n'y aura rien à prévoir.
* Prévoir dans les _changelogs_ une compatibilité avec différents systèmes, par exemple une cible Oracle, un poste de développement avec MySQL et des tests unitaires exécutés sur une base H2 ou HSQL.
* Décorréler l'exécution de Liquibase du déploiement applicatif (même si c'est très pratique). Intégrer cette exécution comme une étape indépendante du processus de mise à jour de l'application. L'analyse des problèmes n'en sera que facilité.
* Utiliser un projet (voire même un dépôt GIT) dédié pour stocker les sources des _changelogs_ et packager celui-ci sous forme d'un module Maven.
* Ecrire une classe de test utilisant une base de données "in memory" (H2 par exemple) permettant de valider les fichiers _changelogs_, y compris le rollback.
* Définir les changements de la manière la plus élémentaire possible (1 changement = 1 changeset) ainsi le code de rollback est plus facile à implémenter.
* Implémenter un élément (une servlet, un webservice, ...) permettant de connaître l'état de la base de données (_liquibase status_).
* L'attribut `logicalFilePath` d'un fichier _changelog_ doit juste contenir le nom du fichier.
* Éviter l'utilisation de `includeAll` qui permet d'inclure dans le _changelog_ principal tous les _changelogs_ d'un sous-dossier. Préférer utiliser `include` en nommant les fichiers un par un pour éviter de prendre en compte des éléments non désirés ou pour pouvoir spécifier des contextes différents.
