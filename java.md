# Bonnes pratiques Java

## Exceptions

* Ne jamais masquer un problème, les exceptions sont typiquement faites pour identifier ou alerter sur quelque chose d'exceptionel

## Favoriser le typage fort

* Très dangereux en cas de _refactoring_
* Utiliser des `enum` plutôt que des `String` ou des `int`

## Java 8 "Optional"

* Utiliser `Optional` dès que possible. Le code est dès lors auto-documenté, plus besoin d'aller voir le source pour vérifier si `null` peut être retourné.
* Encapsuler les retours d'une bibliothèque externes dans un `Optional` via `Optional.ofNullable()` 
