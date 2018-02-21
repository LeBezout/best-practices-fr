# Bonnes pratiques Java

## Constantes

* Il ne faut rendre `public` que des constantes qui le sont réellement (utilisées par plusieurs classes) sinon elles doivent être déclarées comme `private` dans les classes qui les utilisent.
* Ne pas mettre en constante (`static final`) des objets mutables. Par exemple les tableaux, `StringBuilder`, collections, ...

## Exceptions

* Ne jamais masquer un problème, les exceptions sont typiquement faites pour identifier ou alerter sur quelque chose d'exceptionel

## Favoriser le typage fort

* Très dangereux en cas de _refactoring_
* Utiliser des `enum` plutôt que des `String` ou des `int`

## Java 8 "Optional"

* Utiliser `Optional` dès que possible. Le code est dès lors auto-documenté, plus besoin d'aller voir le source pour vérifier si `null` peut être retourné.
* Encapsuler les retours d'une bibliothèque externes dans un `Optional` via `Optional.ofNullable()` 

## JPA

* Favoriser l'utilisation de `NamedQueries`
* Eviter l'utilisation de `NativeQueries`
* Les champs de type date doivent être précisés à l’aide de l’annotation `@Temporal`
* Pour limiter le nombre de résulats d'une requête utiliser `query.setMaxResults(max);`
