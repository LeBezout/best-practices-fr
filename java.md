# Bonnes pratiques de développement Java

## Styles

* Utiliser les conventions de _Sun_ les créateurs du langage [Sun Java Coding Style Guide](https://www.oracle.com/technetwork/java/javase/overview/codeconvtoc-136057.html)
* Ne pas utiliser d'outil du type `Format on Save`
* Utiliser `EditorConfig`
* Éviter les parenthèses inutiles
* Ajouter toujours une javadoc aux composants publics (classes, méthodes, constantes, enum, ...)
* Soigner l'ordre de déclaration des éléments dans une classe : membres statiques -> membres -> méthodes statiques -> constructeur(s) -> méthodes d'instance (_Java Coding Style Guide de Sun_)
* Limiter la taille des méthodes
* Les classes générées doivent être dans des modules séparés
* Soigner le nommage
  * Un nom doit expliquer ce que fait / ce qu'est l'élément nommé mais pas comment il le fait
  * Éviter les préfixes et suffixes
* Le code doit être assez clair pour se passer de commentaires. Limiter leur utilisation car ils deviennent vite obsolètes ou erronés
* Les commentaires sous la forme `/** xxx */` (avec 2 \*) sont exclusivement réservés à la Javadoc. Dans le code il faut utiliser soit `//` soit `/* xxx */` (avec 1 \*)

## Généralités

* Favoriser l'utilisation des interfaces (`List`, `Map`, `Set`, ...) pour déclarer les objets : `List<String> l = new ArrayList<>();` plutôt que `ArrayList<String> l = new ArrayList<>();`

## Constantes

* Il ne faut rendre `public` que des constantes qui le sont réellement (utilisées par plusieurs classes) sinon elles doivent être déclarées comme `private` dans les classes qui les utilisent.
* Ne pas mettre en constante (`static final`) des objets mutables. Par exemple les tableaux, `StringBuilder`, collections, ...

## Exceptions

* Ne jamais masquer un problème, les exceptions sont typiquement faites pour identifier ou alerter sur quelque chose d'exceptionnel
* Ne pas attraper `java.lang.Exception` / `java.lang.RuntimeException` / `java.lang.Error` / `java.lang.Throwable`
* Toujours s'assurer de la fermeture des ressources ouvertes
* Utiliser "try-with-resources" (depuis Java 7)
* Ne pas utiliser d'instruction `return` dans un bloc `finally`
* Ne pas lever d'exception dans un bloc `finally`
* Ne pas lever d'exception pour l'attraper immédiatement
* Ne pas attraper une exception juste pour la logguer (log & re-throw)

:uk: [Best (and Worst) Java Exception Handling Practices](https://able.bio/DavidLandup/best-and-worst-java-exception-handling-practices--18h55kh)

## Favoriser le typage fort

* Utiliser des `enum` plutôt que des `String` ou des `int`
* Très dangereux sinon en cas de _refactoring_

## Java 8 "Optional"

* Utiliser `Optional` dès que possible. Le code est dès lors auto-documenté, plus besoin d'aller voir le source pour vérifier si `null` peut être retourné.
* Encapsuler les retours d'une bibliothèque externes dans un `Optional` via `Optional.ofNullable()`

## JPA

* Favoriser l’utilisation de JPQL / HQL par rapport au SQL et l'API `Criteria`
* Favoriser l'utilisation de `NamedQueries`
* Éviter l'utilisation de `NativeQueries`
* Les champs de type date doivent être précisés à l’aide de l’annotation `@Temporal`
* Pour limiter le nombre de résultats d'une requête utiliser `query.setMaxResults(max);`
* Pour les clefs composites favoriser l'utilisation du couple `@Embeddable` / `@EmbeddedId` plutôt que le couple `@Id` / `IdClass`

## Injection de dépendances

* **Spring :** Favoriser l'injection par constructeur dont les avantages sont :
  * Plus facilement testable
  * Le membre de classe peut être déclaré `final`, la classe peut devenir immuable
  * C'est également le pattern appliqué dans Angular
  * L'annotation (`@Autowired`) devient optionnelle

## Conception d'API

:uk: [Java API Design Best Practices](https://jonathangiles.net/presentations/java-api-design-best-practices/)

* Considérer l'utilisation des _Static Factory Methods_ (Joshua Bloch's Effective Java)
  * Les noms des méthodes sont plus parlant sur les intentions que les constructeurs
  * Celles-ci peuvent retourner différents types
  * Celles-ci peuvent encapsuler la logique nécessaire à la création des instances, par exemple on peut utiliser un simple `Objects.requireNonNull(param, "message")`
  * Celles-ci permettent de contrôler les instanciations, voire les limiter

## Ne pas faire apparaître les éléments implicites

* Ne pas utiliser inutilement `this`
* Ne pas initialiser inutilement un objet à `null`
* Ne pas initialiser un type primitif à sa valeur par défaut :  `0`, `0L`, `0d`, `false`
* Ne pas déclarer de méthodes `public` dans une interface (elles le sont obligatoirement)
* Ne pas déclarer de constantes `public static final` dans une interface (elles le sont obligatoirement)
* Ne pas spécifier que le constructeur de l'`enum` est `private` (il y est obligatoirement)
* Ne pas mettre de `;` à la fin d'une déclaration des éléments d'une `enum` : `VALEUR1, VALEUR2, VALEUR3,`
* Ne pas mettre de `;` à la fin d'une déclaration des éléments d'un bloc `try-with-resource` : `try (element = new Element())`
* Ne pas tester le `null` avant d'utiliser une instruction `instanceof` (qui retourne `false` si l'élément est `null`)

## Divers

* Comparator vs Comparable  : On utilise en général `Comparable` pour l'ordre naturel et l'on écrit un ou plusieurs `Comparator` pour les autres besoins, ou si l'on n'est pas le propriétaire de la classe
* Ne jamais utiliser la méthode `close` sur un objet `Scanner` initialisé avec `System.in` (sinon celui-ci deviendra inutilisable jusqu'à l'arrêt de la JVM)
* Encapsuler les `switch` dans une méthode dédiée : permet de faire des `return` de valeurs directement (pas besoin de `break`, le compilateur nous dira si on oublie le `default`, permet de nommer clairement l'intention via le nom de la méthode)
