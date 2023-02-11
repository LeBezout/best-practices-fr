# Bonnes pratiques de développement Java

## Styles

* Utiliser les conventions de _Sun_ les créateurs du langage [Sun Java Coding Style Guide](https://www.oracle.com/technetwork/java/javase/overview/codeconvtoc-136057.html).
* Ne pas utiliser d'outil du type `Format on Save`.
* Utiliser `EditorConfig`.
* Éviter les parenthèses inutiles.
* Ajouter toujours une javadoc aux composants publics (classes, méthodes, constantes, enum, ...).
* Soigner l'ordre de déclaration des éléments dans une classe : membres statiques -> membres -> méthodes statiques -> constructeur(s) -> méthodes d'instance (_Java Coding Style Guide de Sun_).
* Limiter la taille des méthodes.
* Les classes générées doivent être dans des modules séparés.
* Soigner le nommage :
  * Un nom doit expliquer ce que fait / ce qu'est l'élément nommé mais pas comment il le fait.
  * Éviter les préfixes et suffixes.
* Le code doit être assez clair pour se passer de commentaires. Limiter leur utilisation car ils deviennent vite obsolètes ou erronés.
* Les commentaires sous la forme `/** xxx */` (avec 2 \*) sont exclusivement réservés à la Javadoc. Dans le code il faut utiliser soit `//` soit `/* xxx */` (avec 1 \*). :link: :gb: [Kinds Of Comments par _Nicolai Parlog_](https://medium.com/97-things/kinds-of-comments-667a5b505ca8)

## Constantes

* Il ne faut rendre `public` que des constantes qui le sont réellement (utilisées par plusieurs classes) sinon elles doivent être déclarées comme `private` dans les classes qui les utilisent.
* Ne pas mettre en constante (`static final`) des objets mutables. Par exemple les tableaux, `StringBuilder`, collections, ...

## Exceptions

* Ne jamais masquer un problème, les exceptions sont typiquement faites pour identifier ou alerter sur quelque chose d'exceptionnel.
* Ne pas attraper `java.lang.Exception` / `java.lang.RuntimeException` / `java.lang.Error` / `java.lang.Throwable`.
* Toujours s'assurer de la fermeture des ressources ouvertes.
* Utiliser "try-with-resources" (depuis Java 7).
* Ne pas utiliser d'instruction `return` dans un bloc `finally`.
* Ne pas lever d'exception dans un bloc `finally`.
* Ne pas lever d'exception pour l'attraper immédiatement.
* Ne pas attraper une exception juste pour la logguer (log & re-throw).

:link: :gb: [Best (and Worst) Java Exception Handling Practices par _David Landup_](https://able.bio/DavidLandup/best-and-worst-java-exception-handling-practices--18h55kh)

## Threads et parallélisation

* Nommer les threads.
* Préférer utiliser les pools de threads de la JVM ou du serveur d'applications plutôt que de gérer soit même les threads.
* Préférer implémenter un `Runnable` (ou un `Callable`) plutôt que d'étendre la classe `Thread`.
* Démarrer un thread via la méthode `start()` plutôt que d'appeler `run()`.
* Utiliser des variables `volatile` pour gérer le comportement (l'arrêt par exemple) d'un thread.
* Ne pas utiliser les _ParallelStreams_ pour des petits ensembles (< 1000 éléments).
* N'utiliser la parallélisation qu'en cas de besoin : problème de performance avéré par exemple.
* Optimiser le nombre de threads alloués, par exemple en tenant compte de la fréquence des I/O :
  * si beaucoup d'I/O on peut augmenter le nombre de threads car ils seront souvent en attente
  * au contraire si beaucoup de calculs il faut limiter le nombre de threads (ne pas dépasser le nombre de coeurs par exemple)

## Nouveautés Java 8

### Optional

Voir [la page dédiée](java/optional.md)

### Lambda Expressions

* Favoriser l'utilisation des références de méthodes.
* Ne forcément réinventer des `@FunctionalInterface` il en existe déjà beaucoup de base dans `java.util.function` qui couvrent beaucoup de besoins (Supplier, Consumer, Predicate, Function, BiFunction, ...).
* Éviter ou limiter l'utilisation des blocs `() -> { /* bloc */ }` en favorisant l'utilisation de méthodes. 1 lambda = 1 ligne sinon faire une méthode.

### Streams

* Ne pas retourner de stream, préférer une collection ou un _array_. Un _stream_ n'est pas un conteneur de données !
* Attention à l'utilisation de la méthode `parallel()` qui utilise le **common Fork/join Pool** de la JVM. Les risques :
  * utilisation de tous les processeurs disponibles
  * pénurie de thread pour les autres tâches

## JPA

* Favoriser l'utilisation de JPQL / HQL par rapport au SQL et l'API `Criteria`.
* Favoriser l'utilisation de `NamedQueries`.
* Éviter l'utilisation de `NativeQueries`.
* Ne pas utiliser `@Enumerated(EnumType.ORDINAL)`, le simple ajout d'un élément ou un refactoring casserait l'intégrité de la base de données.
* Les champs de type date doivent être précisés à l’aide de l’annotation `@Temporal`.
* Pour limiter le nombre de résultats d'une requête utiliser `query.setMaxResults(max);`.
* Pour les clefs composites favoriser l'utilisation du couple `@Embeddable` / `@EmbeddedId` plutôt que le couple `@Id` / `@IdClass`.

## Injection de dépendances

* **Spring :** Favoriser l'injection par constructeur dont les avantages sont :
  * Plus facilement testable.
  * Le membre de classe peut être déclaré `final`, la classe peut devenir immuable.
  * C'est également le pattern appliqué dans Angular.
  * L'annotation (`@Autowired`) devient optionnelle.

## Conception / Design

:link: :gb: [Java API Design Best Practices par _Jonathan Giles_](https://jonathangiles.net/presentations/java-api-design-best-practices/)

* Favoriser l'utilisation des interfaces (`List`, `Map`, `Set`, ...) pour déclarer les objets : `List<String> l = new ArrayList<>();` plutôt que `ArrayList<String> l = new ArrayList<>();`.
* Favoriser les implémentations immuables : plus robustes, _thread-safe_, ...
* Éviter les paramètres booléens car peu clair et potentiellement source d'erreur (inversion).
* Considérer l'utilisation des _Static Factory Methods_ (Joshua Bloch's Effective Java) ou des méthodes de type _builder_ :
  * Les noms des méthodes sont plus parlant sur les intentions que les constructeurs.
  * On peut donc avoir des méthodes différentes avec des paramètres identiques.
  * Celles-ci peuvent retourner différents types (sous-types).
  * Celles-ci peuvent encapsuler la logique nécessaire à la création des instances, par exemple on peut utiliser un simple `Objects.requireNonNull(param, "message")`.
  * Celles-ci permettent de contrôler les instanciations, voire les limiter.
* Encapsuler les `switch` dans une méthode dédiée : permet de faire des `return` de valeurs directement (pas besoin de `break`, le compilateur nous dira si on oublie le `default`, permet de nommer clairement l'intention via le nom de la méthode).
* Favoriser le typage fort
  * Utiliser des `enum` plutôt que des `String` ou des `int`.
  * Très dangereux sinon en cas de _refactoring_.
  * Éviter la _Primitive Obsession_ : préférer encapsuler les concepts dans des types dédiés même s'ils peuvent être représentés simplement avec un type de base (int, String, ...).

## Ne pas faire apparaître les éléments implicites

* Ne pas utiliser inutilement `this`.
* Ne pas utiliser inutilement `@Annot(value = "xxx")` (mais directement `@Annot("xxx")`) pour une annotation si c'est l'unique attribut valorisé.
* Ne pas initialiser inutilement un objet à `null`.
* Ne pas initialiser un type primitif à sa valeur par défaut : `0`, `0L`, `0d`, `false`.
* Ne pas déclarer de méthodes `public` dans une interface (elles le sont obligatoirement).
* Ne pas déclarer de constantes `public static final` dans une interface (elles le sont obligatoirement).
* Ne pas spécifier que le constructeur de l'`enum` est `private` (il y est obligatoirement).
* Ne pas mettre de `;` à la fin d'une déclaration des éléments d'une `enum` : `VALEUR1, VALEUR2, VALEUR3,`.
* Ne pas mettre de `;` à la fin d'une déclaration des éléments d'un bloc `try-with-resource` : `try (element = new Element())`.
* Ne pas tester le `null` avant d'utiliser une instruction `instanceof` (qui retourne `false` si l'élément est `null`).

## Toujours positionner les _timeouts_

Afin d'éviter les timeouts infinis, souvent positionnés par défaut, on veillera à toujours positionner, paramétrer et externaliser les différentes valeurs des timeouts. Par exemple pour les appels suivants :

* WebServices SOAP JAX-WS
* WebServices REST JAX-RS
* Clients HTTP
* Clients SMTP

On différenciera et on positionnera :

* le **timeout de connexion** (_connection timeout_), relativement court (exemple : 10sec)
* le **timeout de réponse** (_read timeout_, _response timeout_) adapté à ce que l'on est sensé récupérer (un petit flux JSON ou un gros fichier), ni trop faible ni trop élevé (exemple : 60 sec).

## Ordre des annotations

:bulb: **Préconisation :** de la moins structurante à la plus structurante. En d'autres termes, plus l'annotation est proche de l'élément auquel elle fait référence plus elle est structurante. Enfin on placera la Javadoc en 1er avant les annotations.

1. Annotation processor : génération de byte code, _boiler plate_, ... (Lombok, MapStruct, ...)
1. Documentation (Swagger, ...)
1. Validation
1. Fonctionnalité

### Types

Exemple :

```java
@Slf4j
@RequiredArgsConstructor
@Api(value = "Service d'accès à XXX")
@Validated
@RestController
@RequestMapping(path = "/service")
public class MyService {

}
```

### Membres ou méthodes

Exemple :

```java
@Getter
@NotNull
@Column(name = "COL")
private String member;
```

### Paramètres de méthode

Exemple :

```java
public XXXResponse rechercher(@ApiParam(value = "Le critère de recherche") @Valid @NotBlank(message = "Critère de recherche obligatoire") @PathVariable(name = "value") String value) {

}
```

## Divers

* Comparator vs Comparable : On utilise en général `Comparable` pour l'ordre naturel et l'on écrit un ou plusieurs `Comparator` pour les autres besoins, ou si l'on n'est pas le propriétaire de la classe.
* Ne jamais utiliser la méthode `close` sur un objet `Scanner` initialisé avec `System.in` (sinon celui-ci deviendra inutilisable jusqu'à l'arrêt de la JVM).

## Liens

* :gb: [9 tips to Increase your Java performance](https://dev.to/sendilkumarn/9-tips-to-increase-your-java-performance-1l4d)
