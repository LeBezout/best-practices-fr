# Bonnes pratiques d'écriture des tests

## Principes généraux

* Un test ne doit tester qu'une seule chose : un test = une assertion.
* S'il doit échouer le test doit bien sur le faire le plus rapidement possible.
* Respecter le format : Given->When->Then.
* Pratiquer autant que possible _Test First_ et son évolution _TDD_.
* Ne tester que son propre code pas celui d'une bibliothèque ou d'un composant tier.
* Valider les méthodes privées en effectuant un test unitaire des méthodes publiques sans avoir forcément besoin de changer le _scope_ de celles-ci.

## Maintenabilité

* Les tests doivent être le plus simples possible et rapides à écrire et facilement compréhensibles.
* Généraliser, ne pas dupliquer de code.

## Code Legacy

* La correction d'un bug doit entraîner automatiquement l'écriture du ou des tests correspondant afin que celui-ci ne puisse jamais ré-apparaître.
* Corriger ou à défaut supprimer des tests échouant par intermittence.
* Les parties critiques de l’application sont testées en priorité.

## Fake, Stubs, Mocks, bouchons

TODO

## Pour aller encore plus loin dans la pratique des tests

* [PITest](http://pitest.org/) : _Mutation Testing System._
* [Stan4j](http://stan4j.com/download/ide/) : _The dependency graph of packages or components should have no cycles._
* [ArchUnit](https://www.archunit.org/) : _Unit Test your Java Architecture._
* [jQAssistant](https://jqassistant.org/) : _Definition and validation of project specific rules on a structural level._
* [Infinitest](https://infinitest.github.io/) : _Each time you change the code Infinitest runs the relevant tests for you!_
