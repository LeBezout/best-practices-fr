# Bonnes pratiques Java

## Styles

* Utiliser les conventions de _Sun_ les créateurs du langage [Sun Java Coding Style Guide](https://www.oracle.com/technetwork/java/javase/overview/codeconvtoc-136057.html)
* Ne pas utiliser d'outil du type `Format on Save`
* Utiliser `EditorConfig`
* Eviter les parenthèses inutiles
* Ajouter toujours une javadoc aux composants publics (classes, méthodes, constantes, enum, ...)
* Soigner l'ordre de déclaration des éléments dans une classe : membres statiques -> membres -> méthodes statiques -> constructeur(s) -> méthodes d'instance (_Java Coding Style Guide de Sun_)
* Limiter la taille des méthodes
* Les classes générées doivent être dans des modules séparés
* Soigner le nommage
  * Un nom doit expliquer ce que fait / ce qu'est l'élément nommé mais pas comment il le fait
  * Eviter les prefixes et suffixes
* Le code doit être assez clair pour se passer de commentaires. Limiter leur utilisation car ils deviennent vite obsolète ou éronnés

## Généralités

* Favoriser l'utilisation des interfaces (`List`, `Map`, `Set`, ...) pour déclarer les objets : `List<String> l = new ArrayList<>();` plutôt que `ArrayList<String> l = new ArrayList<>();`

## Constantes

* Il ne faut rendre `public` que des constantes qui le sont réellement (utilisées par plusieurs classes) sinon elles doivent être déclarées comme `private` dans les classes qui les utilisent.
* Ne pas mettre en constante (`static final`) des objets mutables. Par exemple les tableaux, `StringBuilder`, collections, ...

## Exceptions

* Ne jamais masquer un problème, les exceptions sont typiquement faites pour identifier ou alerter sur quelque chose d'exceptionel
* Ne pas attraper `java.lang.Exception` / `java.lang.RuntimeException` / `java.lang.Error` / `java.lang.Throwable`
* Toujours s'assurer de la fermeture des ressources ouvertes
* Utiliser "try-with-resources" (depuis Java 7)
* Ne pas utiliser d'instruction `return` dans un bloc `finally`
* Ne pas lever d'exception dans un bloc `finally`
* Ne pas lever d'exception pour l'attraper immédiatement
* Ne pas attraper une exception juste pour la logguer (log & re-throw)

## Favoriser le typage fort

* Utiliser des `enum` plutôt que des `String` ou des `int`
* Très dangereux sinon en cas de _refactoring_

## Java 8 "Optional"

* Utiliser `Optional` dès que possible. Le code est dès lors auto-documenté, plus besoin d'aller voir le source pour vérifier si `null` peut être retourné.
* Encapsuler les retours d'une bibliothèque externes dans un `Optional` via `Optional.ofNullable()` 

## JPA

* Favoriser l’utilisation de JPQL / HQL par rapport au SQL et l'API `Criteria`
* Favoriser l'utilisation de `NamedQueries`
* Eviter l'utilisation de `NativeQueries`
* Les champs de type date doivent être précisés à l’aide de l’annotation `@Temporal`
* Pour limiter le nombre de résulats d'une requête utiliser `query.setMaxResults(max);`
* Pour les clefs composites favoriser l'utilisation du couple `@Embeddable` / `@EmbeddedId ` plutôt que le couple `@Id` / `IdClass`

## Injection de dépendances

* Favoriser l'injection par constructeur dont les avantages sont :
  * Plus facilement testable
  * Le membre de classe peut être déclaré `final`, la classe peut devenir immuable
  * C'est également le pattern appliqué dans Angular
  * L'annotation (`@Autowired`) devient optionnelle

## Divers

* Comparator vs Comparable  : On utilise en général `Comparable` pour l'ordre naturel et l'on écrit un ou plusieurs `Comparator` pour les autres besoins, où si l'on est pas le propriétaire de la classe
* Ne jamais utiliser la méthode `close` sur un objet `Scanner`initialisé avec `System.in` (sinon celui-ci deviendra inutilisable jusqu'à l'arrêt de la JVM)