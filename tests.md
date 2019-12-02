
# Bonnes pratiques d'écriture des tests

## Principes généraux

* Un test ne doit tester qu'une seule chose : un test = une assertion.
* S'il doit échouer le test doit bien sur le faire le plus rapidement possible.
* Respecter le format : Given->When->Then.
* Pratiquer autant que possible _Test First_ et son évolution _TDD_.
* Ne tester que son propre code pas celui d'une bibliothèque ou d'un composant tier.
* Valider les méthodes privées en effectuant un test unitaire des méthodes publiques sans avoir forcément besoin de changer le _scope_ de celles-ci.

## Maintenabilité

* Le code doit être pensé et écrit de façon à ce qu’il soit naturellement et unitairement testable.
* Les tests doivent être le plus simples possible et rapides à écrire et facilement compréhensibles.
* Généraliser, ne pas dupliquer de code.
* Le nom d’un test doit être normalisé (la lecture du nom doit permettre de savoir exactement ce que va faire le test)

## Code Legacy

* La correction d'un bug doit entraîner automatiquement l'écriture du ou des tests correspondant afin que celui-ci ne puisse jamais ré-apparaître.
* Corriger ou à défaut supprimer des tests échouant par intermittence.
* Les parties critiques de l’application sont testées en priorité.
* Approcher de 100% de couverture sur tout le nouveau code.

## Fake, Stubs, Mocks, bouchons

Dans tous les cas ce sont des objets (classes, implémentations, ...) qui ne sont jamais utilisés dans le code de production, des outils pour le code de test. Néanmoins on peut imaginer, en production, des _fallback_ (solution alternative, solution de repli) utilisant des bouchons.

* **Fake** : Faux-objets
  * Souvent des objets au capacités limités.
  * Peut être un _stub_ ou _mock_.
* **Stub** : ébauche
  * Permet de remplacer une dépendance existante et non primodiale pour le test.
  * Peut être configuré pour les besoins du test.
  * On ne fait aucune assertions sur ces objets.
  * Sont utilisés dans la partie _Given_.
* **Mock** : Objet simulé
  * C'est un _stub_ sur lequel on va pouvoir faire des assertions.
  * Sont utilisés dans la partie _When_ et _Then_.
  
:gb: [Martin Fowler - Mocks Aren't Stubs](https://www.martinfowler.com/articles/mocksArentStubs.html)

:fr: [Benoît Sautel - Mock ou pas mock ?](https://www.fierdecoder.fr/2015/11/mock-ou-pas-mock/)

:warning: Les définitions peuvent variées il est donc conseillé de définir et de s'accorder sur une définition commmune au sein de l'équipe.

## Pour aller encore plus loin dans la pratique des tests

* [PITest](http://pitest.org/) : _Mutation Testing System._
* [Stan4j](http://stan4j.com/download/ide/) : _The dependency graph of packages or components should have no cycles._
* [ArchUnit](https://www.archunit.org/) : _Unit Test your Java Architecture._
* [jQAssistant](https://jqassistant.org/) : _Definition and validation of project specific rules on a structural level._
* [Infinitest](https://infinitest.github.io/) : _Each time you change the code Infinitest runs the relevant tests for you!_
