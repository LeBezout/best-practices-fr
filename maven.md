# Bonnes pratiques d'utilisation de Maven

* _Convention over Configuration_ : respecter les conventions Maven (structure standard des projets, ...)
* Utiliser le fichier de configuration `settings.xml`
* Utiliser un pom parent commun à vos modules (pour mutualiser les informations et les versions)
* Utiliser des blocs `dependencyManagement` et `pluginManagement` pour gérer vos versions
* Ne jamais positionner les fichiers de configuration externalisables (par environnement) dans `src/main/resources`
* Ne déployer dans le référentiel d'entreprise que le strict nécessaire (un war, un ear, un zip n'a souvent aucune utilité dans le référentiel)
* Monter régulièrement les versions de vos dépendances et contrôler les failles de sécurité potentielles via l'outil **OWASP Dependency Check**
* Générer et déployer sources et Javadoc pour vos composants communautaires / partagés
* Gérer correctement vos versions et utiliser judicieusement les "SNAPSHOT"
* Le code généré doit être dans le dossier `target` et isolé dans un module dédié (avec son propre cycle de vie et gestion de version)
* Utiliser les fonctionnalités avancées telles que les filtres, les profils, les "assembly"
* Isoler les fonctionnalités (packaging par exemple) dans des profils séparés pour optimiser les exécutions
* Spécifier toujours une version sur chacun des plugins utilisés, ne laisser pas Maven décider (build reproductible)
