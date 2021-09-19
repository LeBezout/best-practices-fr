
# Bonnes pratiques d'écriture des tests

## Principes généraux

* Un test ne doit tester qu'une seule chose : un test = une assertion.
* Un test doit être autonome = ne pas dépendre de l'exécution d'un autre test.
* S'il doit échouer le test doit bien sur le faire le plus rapidement possible.
* Respecter le format : Given->When->Then.
* Pratiquer autant que possible _Test First_ et son évolution _TDD_.
* Ne tester que son propre code pas celui d'une bibliothèque ou d'un composant tier.
* Valider les méthodes privées en effectuant un test unitaire des méthodes publiques sans avoir forcément besoin de changer le _scope_ de celles-ci.

## Maintenabilité

* Il faut apporter au code de test la même attention et la même qualité qu'au code de production.
* Le code doit être pensé et écrit de façon à ce qu’il soit naturellement et unitairement testable.
* Les tests doivent être le plus simples possible et rapides à écrire et facilement compréhensibles.
* Favoriser la lisibilité au détriment parfois de certains principes que l'on applique sur le code "de production" : duplication, _magic numbers_, ...
* Le nom d'un test doit être normalisé (la lecture du nom doit permettre de savoir exactement ce que va faire le test).
* Donner un nom le plus explicite possible à la méthode du test, on n'appelle ou on n’utilise jamais une méthode de test, c'est le framework de test / l'IDE qui le fait. Donc il ne faut pas être avare sur les caractères.

## Code Legacy

* La correction d'un bug doit entraîner automatiquement l'écriture du ou des tests correspondant afin que celui-ci ne puisse jamais ré-apparaître.
* Corriger ou à défaut supprimer des tests échouant par intermittence.
* Les parties critiques de l'application sont testées en priorité.
* Approcher de 100% de couverture sur tout le nouveau code.
* Il n'y a pas de _refactoring_ possible s'il n'y a pas de tests ou si les tests ne sont pas au vert.

## Ressources

* :fr: [Les 10 commandements des tests unitaires](https://blog.xebia.fr/2008/04/11/les-10-commandements-des-tests-unitaires/)
* :fr: [Meilleures pratiques pour les tests unitaires avec .NET Core et .NET Standard](https://docs.microsoft.com/fr-fr/dotnet/core/testing/unit-testing-best-practices)
* :gb: [30 best practices for software development and testing](https://opensource.com/article/17/5/30-best-practices-software-development-and-testing)
* :gb: [Why Good Developers Write Bad Unit Tests](https://mtlynch.io/good-developers-bad-tests/)
* :gb: [Seven Testing Sins and How To Avoid Them](https://www.javacodegeeks.com/2019/08/seven-testing-sins-and-how-to-avoid-them.html)
