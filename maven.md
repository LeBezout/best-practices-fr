# Bonnes pratiques d'utilisation de Maven

## Grandes versions
* Maven `1.0` : 07/2004 -> 1.1 : 06/2007
* Maven `2.0` : 10/2005 -> 2.2.1 : 11/2009
* Maven `3.0` : 10/2010
* Maven `3.1.1` : 10/2013 (Java 5)
* Maven `3.2.6` : 12/2014 (Java 6)
* Maven `3.6.0` : 10/2018 (Java 7)

## Respecter les standards Maven

* _Convention over Configuration_ : respecter les conventions Maven (structure standard des projets, ...)
  * `src/main/java`, `src/main/resources`, `src/main/filters`, `src/main/webapp`
  * `src/test/java`, `src/test/resources`
  * `src/assembly`
  * `target/generated-sources`
* Configurer le fichier `settings.xml`
  * Accès aux référentiels internes
* Utiliser les variables pré-définies, par exemple au lieu de `target` (en dur) utiliser `${project.build.directory}`

## Mutualiser

* Utiliser un pom parent commun à vos modules (pour mutualiser les informations et les versions)
* Utiliser des blocs `dependencyManagement` et `pluginManagement` pour gérer vos versions
* Isoler les fonctionnalités (packaging par exemple) dans des profils séparés pour optimiser les exécutions (sans en abuser)

## Tester

* Evidemment, ne pas désactiver les tests
* Implémenter des tests d'intégration

## Optimiser vos automatisations

* Utiliser `--batch-mode` pour s'assurer qu'aucune intéraction avec un utilisateur ne soit demandée
* Utiliser `--quiet` pour réduire la verbosité
* Utiliser `--fail-fast` ou `--fail-at-end` en fonction de vos besoins

## Maîtriser vos artefacts

* Ne jamais positionner les fichiers de configuration externalisables (par environnement) dans `src/main/resources`
* Ne déployer dans le référentiel d'entreprise que le strict nécessaire (un war, un ear, un zip n'a souvent aucune utilité dans le référentiel)
* Générer et déployer sources et Javadoc pour vos composants communautaires / partagés
* Gérer correctement vos versions et utiliser judicieusement les "SNAPSHOT"
* Le code généré doit être dans le dossier `target` et isolé dans un module dédié (avec son propre cycle de vie et gestion de version)
* Utiliser les fonctionnalités avancées telles que les filtres, les profils, les "assembly"

## Assurer un build reproductible

* Spécifier toujours une version sur chacun des plugins utilisés, ne laisser pas Maven décider (build reproductible)
* Eviter autant que possible l'utilisation d'outils externes via différents plugins (ant, nodejs, exec, ...)

## Sécuriser

* Aucun secret ne doit apparaître en clair (... ou en base64) dans vos fichiers de configurations ou filtres
* Monter régulièrement les versions de vos dépendances
* Contrôler les failles de sécurité potentielles via le plugin **[OWASP Dependency Check](https://jeremylong.github.io/DependencyCheck/dependency-check-maven/index.html)**
* N'utiliser pas de versions de Maven trop anciennes (Maven 2.X par exemple)

## Liens utiles

* [Versions History](https://maven.apache.org/docs/history.html)
* [Lyfecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)
* [Standard Directory Layout](http://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)
* [List of predefined Maven properties](https://github.com/cko/predefined_maven_properties/blob/master/README.md)
