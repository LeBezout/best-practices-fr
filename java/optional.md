# Bonnes et mauvaises pratiques d'utilisation de java.util.Optional

## Pourquoi Optional ?

José Paumard :

> Cette classe a été introduite pour modéliser le fait qu'une méthode peut très bien ne pas pouvoir retourner de valeur.

Javadoc :

> **Optional is primarily intended for use as a method return type where there is a clear need to represent "no result," and where using null is likely to cause errors.**

Utiliser `java.util.Optional` en retour de méthodes pour indiquer clairement à l'appelant qu'aucun résultat peut être produit et qu'il devra traiter ce cas.

## Règles de base et bonnes pratiques

* Ne jamais retourner `null` pour un `Optional` ou ne jamais affecter une instance à `null`. Et indirectement ne jamais tester si un `Optional` est `null`.
  * **Une instance d'`optional` ne doit jamais être nulle**.
* Ne jamais appeler `get()` directement.
* Eviter d'utiliser `Optional` pour autre chose que pour retour de méthodes. Exemples d'utilisations conformes :
  * `Stream#findFirst`
  * Spring Data `@Repository`
* `Optional` n'est pas forcément fait pour remplacer tous les `null`.
* Ne pas généraliser, à utiliser à bon escient.
  * Ne pas utiliser avec des tableaux ou des collections : retourner une liste vide.
  * Ne pas utiliser en paramètre de méthodes (force l'appelant à créer des instances souvent inutiles).
  * Ne pas utiliser en membre de classe. **Attention `Optional` n'est délibérément pas `Serializable` !**
  * Ne pas créer d'instance juste pour récupérer une potentielle valeur, plutôt tester directement le `null`.
* Ne pas se limiter à remplacer `if (x != null)` par `if (y.isPresent())`, `Optional` propose d'autres types de méthodes comme `map()`, `orElse()`, ... Exemple : `final String withDefault = Optional.ofNullable(test).map(String::trim).filter(s -> s.length() > 0).orElse("Valeur par défaut");`
* Ne pas utiliser pour encapsuler des collections ou des tableaux, retourner directement des collections ou des tableaux vides.

## Détection des mauvaises pratiques

* Finalement renvoyer `null` : `orElse(null)` (ce que `Optional` est censé éviter)
* Instanciations inutiles `if (Optional.ofNullable(something).isPresent() {})`
* Finalement devoir faire un `if`:
  * `if (myOpt.isPresent)`
  * `if (myOpt.isEmpty)`
* Ne pas utiliser comme attribut de classe et encore moins si la classe `implements Serializable`
  * _Using a field with the `java.util.Optional` type is also problematic if the class needs to be Serializable, as `java.util.Optional` is not serializable._
  * `java.util.Optional` n'est délibérément pas `Serializable` !
* Une instance de `java.util.Optional` ne doit jamais être null : `return null;` au lieu de `Optional.empty()`
* Encapsuler une collection : `Optional<Collection<T>>` au lieu de `Collections.emptyList()` (java 8) / `List.of()` (java 9)
* Une collection d'Optional `Collection<Optional<T>>`
* Une instanciation inutile `if (Optional.ofNullable(un_truc_potentiellement_null).isPresent())`
* `orElse(operationCouteuse())` au lieu de `orElseGet(() -> operationCouteuse())`
* `opt.stream().map(X::Y)` au lieu de `opt.map(X::Y)`
* Il est tentant d'utiliser `java.util.Optional` pour distinguer les paramètres obligatoires des paramètres facultatifs
  * A l'usage cette approche alourdit le code, force l'appelant à créer des instances souvent inutiles
  * On peut toujours passer `null` en argument de la méthode (qu'il soit Optional ou non)
  * Solutions ? Le pattern Builder, le polymorphisme, les _varargs_, un bon vieux `null`

## Trucs et astuces

* Penser à utiliser les dérivés pour les primitives :
  * `OptionalInt`
  * `OptionalLong`
  * `OptionalDouble`
* Encapsuler les retours d'une bibliothèque externes dans un `Optional` via `Optional.ofNullable()` (= principe de la Couche d'anti-corruption).
* Utiliser `Optional` dès que possible :
  * Le code est dès lors auto-documenté, plus besoin d'aller voir le source pour vérifier si `null` peut être retourné.
  * Ne plus jamais retourner `null`.

## Annexes

### Javadoc

> * A container object which may or may not contain a non-null value.
> * A variable whose type is Optional should never itself be null; it should always point to an Optional instance.
> * Use of identity-sensitive operations on instances of Optional may have unpredictable results and should be avoided.

### Citations

* :gb: **JetBrains** : _`Optional` was designed to provide a limited mechanism for library method return types in which a clear way to represent "no result" was needed_
* :gb: **Brian Goetz** : _we did have a clear intention when adding this feature, and it was not to be a general purpose Maybe type, as much as many people would have liked us to do so._ [on stackoverflow](https://stackoverflow.com/questions/26327957/should-java-8-getters-return-optional-type/26328555#26328555)
* :gb: **Brian Goetz** : _You probably should never use it for something that returns an array of results, or a list of results; instead return an empty array or list. You should almost never use it as a field of something or a method parameter._ [on stackoverflow](https://stackoverflow.com/questions/26327957/should-java-8-getters-return-optional-type/26328555#26328555)
* :gb: **Joshua Blosh** : _it is almost never appropriate to use an optional as a key, value, or element in a collection or array._
* :gb: **Indrek Ots** : _The problem with `Optional::get` is that it leads us to write the same style of code that we wrote when we explicitly checked for null reference._

### Historique de la classe

* Java 8 - 2014 - Création de la classe
  * `of()`, `ofNullable()`, `empty()`
  * `get()`
  * `isPresent()`
  * `ifPresentOrElse(Consumer<>)`
  * `filter(Predicate<>)`
  * `map(Function)`, `flatMap(Function<>)`
  * `orElse()`, `orElseGet(Supplier<>)`, `orElseThrow(Supplier<Exception>)`
* Java 9 - 2017
  * `or(Supplier<Optional>)`
  * `stream()`
  * `ifPresentOrElse(Consumer<>, Runnbale)`
* Java 10 - 2018
  * `orElseThrow()` le nouveau nom de `get` (mais qui n'est pas dépréciée pour autant)
* Java 11 - 2018
  * `isEmpty()` comme complément à `isPresent()`

## Ressources / Références

* :gb: [dzone.com - Understand when to use Optional](https://dzone.com/refcardz/java-api-best-practices?chapter=14#section-14)
* :gb: [blog.indrek.io - Misusing Java’s Optional type](https://blog.indrek.io/articles/misusing-java-optional/)
* :gb: [blog.oracle.com - 12 recipes for using the Optional class as it’s meant to be used](https://blogs.oracle.com/javamagazine/post/12-recipes-for-using-the-optional-class-as-its-meant-to-be-used)
* :gb: [javacodegeeks - Optional Does Not Supplant All Traditional if-null-else or if-not-null-else Checks](https://www.javacodegeeks.com/2021/09/javas-optional-does-not-supplant-all-traditional-if-null-else-or-if-not-null-else-checks.html)
* :fr: [blog.paumard.org - Patterns optionels](https://blog.paumard.org/2014/12/07/patterns-optionels/)

---
:point_left: [Retour](../java.md)
