# Notions de dette technique

## Définition

Appliqué au domaine du développement logiciel le concept de dette technique est l'accumulation de risques impliqués
par les choix techniques effectués tout au long de la vie d'un projet.

### Constats

La détection de cette dette se fait par les constats suivants :

* Peur de modifier une partie du code 
* Difficultés pour ajouter de nouvelles fonctionnalités
* Duplication de fonctionnalités d'un composant dans un autre ou tout autres duplications
* Chiffrages évolutifs anormalement élevés pour une partie du code
* Seules certaines personnes sont capables de maintenir une partie du code ou pire, la connaissance s'est perdue avec le temps ou les changements de personnes
* Utilisation de technologies obsolètes (frameworks, composants applicatifs, ...)
* Mauvais choix d'architecture ou architecture obsolète
* Absence de tests automatisés
* Absence de revues de code régulières
* Absence de documentations (techniques et fonctionnelle)
* Absence d'intégration continue et d'outillage qualité (exemple Sonar)
* Non-respect des normes et standards
* Application Web ne fonctionnant que sur un seul type de Browser Web (exemple IE8)

### Risques identifiés

* La dette s'accroît tout au long de la vie du projet
* Des temps de développement de plus en plus long, une augmentation des régressions et des bugs de plus en plus fréquents
* Le coût de la dette augmente jusqu'à un point où il n'est plus possible de la rembourser intégralement

## Dette "technologique"

Quelques exemples :

* Absence de montée de version des dépendances et framework
* Absence de montée de version des serveurs d'applications ou web
* Absence de montée de version des infrastructures
* Absence d'outillage et d'automatisation du packaging
* Absence d'outillage du poste de travail

## Dette "méthodologique"

Quelques exemples :

* Pas de ligne d’intégration continue
* Pas ou peu de contrôles qualité (Sonarqube, selenium, ...)
* Pas ou peu de tests unitaires
* Pas ou peu de revue
