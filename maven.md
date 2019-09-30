# Bonnes pratiques d'utilisation de Maven

![logo](images/maven_logo.png)

## Règle 1 : respecter les standards Maven

:pushpin: **Objectif :** améliorer la maintenabilité et l'exploitabilité.

* _Convention over Configuration_ : respecter les conventions Maven (structure standard des projets, ...).
  * `src/main/java`, `src/main/resources`, `src/main/filters`, `src/main/webapp`
  * `src/test/java`, `src/test/resources`
  * `src/assembly` (ou `src/main/assembly`)
  * `target/generated-sources`
  * `src/main/config` (hors du standard Maven qui permet de définir les configurations à externaliser)
* Configurer le fichier `settings.xml`.
  * Accès aux référentiels internes.
  * Optionnellement la configuration HTTP.
  * Optionnellement les profils par défaut.
* Utiliser les variables prédéfinies, par exemple au lieu de `target` (en dur) utiliser `${project.build.directory}`.

## Règle 2 : mutualiser

:pushpin: **Objectif :** améliorer la maintenabilité et la robustesse.

* Utiliser un pom parent commun à vos modules (pour mutualiser les informations et les versions).
* Utiliser des blocs `dependencyManagement` et `pluginManagement` pour gérer vos versions.
* Générer vos modules depuis un archetype `mvn archetype:generate ...`.

## Règle 3 : tester

:pushpin: **Objectif :** améliorer la robustesse et la performance.

* Évidemment, ne pas désactiver les tests.
* Implémenter des tests d'intégration.

## Règle 4 : optimiser vos automatisations

:pushpin: **Objectif :** améliorer la maintenabilité, l'exploitabilité.

* Utiliser `--batch-mode` pour s'assurer qu'aucune interaction avec un utilisateur ne soit demandée.
* Utiliser `--quiet` pour réduire la verbosité.
* Utiliser `--fail-fast` ou `--fail-at-end` en fonction de vos besoins.
* Isoler les fonctionnalités (packaging par exemple) dans des profils séparés pour optimiser les exécutions (sans en abuser pour une meilleure maintenabilité).

:bulb: Penser à configurer correctement vos dépôts Git, notamment le fichier `.gitignore` afin de ne pas remonter des éléments indésirables dans le référentiel.

## Règle 5 : maîtriser vos artefacts

:pushpin: **Objectif :** améliorer la maintenabilité, l'exploitabilité.

* Ne jamais positionner les fichiers de configuration externalisables (par environnement) dans `src/main/resources`.
* Ne déployer dans le référentiel d'entreprise que le strict nécessaire (un war, un ear, un zip n'a souvent aucune utilité dans le référentiel).
* Générer et déployer sources et Javadoc pour vos composants communautaires / partagés.
* Gérer correctement vos versions et utiliser judicieusement les "SNAPSHOT".
* Le code généré doit être dans le dossier `target` et isolé dans un module dédié (avec son propre cycle de vie et gestion de version).
* Utiliser les fonctionnalités avancées telles que les filtres, les profils, les "assembly".
* Comme pour les _packages_ Java favoriser l'utilisation des minuscules pour le nommage des artefacts (`groupId`, `artefactId`).
* Nommer clairement vos composants, par exemple ne répéter pas le `groupId` dans les `artefactId`.
* Analyser vos dépendances avec `mvn dependency:analyze`, sous l'IDE _Eclipse_ la vue "_Dependency Hierarchy_" est également très pratique.
* Supprimer les artefacts obsolètes ou erronés du référentiel d'entreprise.

## Règle 6 : assurer un build reproductible

:pushpin: **Objectif :** améliorer l'exploitabilité.

* Spécifier toujours une version sur chacun des plugins utilisés, ne laisser pas Maven décider (build reproductible).
* Éviter autant que possible l'utilisation d'outils externes via différents plugins (ant, nodejs, exec, ...).
* Se baser uniquement sur le référentiel d'entreprise (toutes les dépendances nécessaires doivent y être présentes).
* Ne pas utiliser le _scope_ `system`.

## Règle 7 : sécuriser

:pushpin: **Objectif :** améliorer la sécurité.

* Aucun secret ne doit apparaître en clair (... ou en base64) dans vos fichiers de configurations ou filtres.
* Mettre à jour régulièrement vers des versions plus récentes vos dépendances.
* Contrôler les failles de sécurité potentielles via le plugin [OWASP Dependency Check](https://jeremylong.github.io/DependencyCheck/dependency-check-maven/index.html) ou via l'IDE avec [Snyk Vulnerabilities Scanning](https://blog.jetbrains.com/idea/2019/03/catching-vulnerabilities-instantly-in-your-intellij-idea-environment/).
* N'utiliser pas de versions de Maven trop anciennes (Maven 2.X par exemple).

## Annexes

## Historique des grandes versions

* Maven `1.0` : 07/2004 -> 1.1 : 06/2007
* Maven `2.0` : 10/2005 -> 2.2.1 : 11/2009
* Maven `3.0` : 10/2010
* Maven `3.1.1` : 10/2013 (Java 5)
* Maven `3.2.6` : 12/2014 (Java 6)
* Maven `3.6.0` : 10/2018 (Java 7)

> :information_source: Maven 3.3+ require JDK 1.7 or above to execute. [maven.apache.org](https://maven.apache.org/index.html)

### Liens utiles

* [Versions History](https://maven.apache.org/docs/history.html)
* [Lyfecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)
* [Standard Directory Layout](http://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)
* [List of predefined Maven properties](https://github.com/cko/predefined_maven_properties/blob/master/README.md)
