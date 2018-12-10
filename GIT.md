# Bonnes pratiques d'utilisation de GIT

## La configuration utilisateur

* Chaque utilisateur doit avoir un fichier `.gitconfig` correctement renseigné (à minima avec `user.name` et `user.email`)

## L'initialisation du dépôt

* Chaque dépôt doit contenir à la racine un fichier `README.md` permettant de décrire celui-ci
* Chaque dépôt doit contenir à la racine un fichier `.gitignore` permettant de na pas remonter n'importe quoi dans le système
* Chaque dépôt doit contenir à la racine un fichier `.gitattributes` permettant de gérer correctement le format des fichiers (binaire ou texte, windows ou unix)

## Le format des fichiers

* Toujours terminer ses fichiers par une ligne vide
* Préférer les espaces (2 à 4) par rapport aux tabulations

## Méthodologies

* Travailler dans ses propres branches (et les mettre à jour régulièrement via merge pour éviter d'avoir trop de conflits à résoudre lors du merge final)
* Favoriser l'utilisation de _Pull Requests_ (github) ou _Merge Requests_ (gitlab) et de revues collégiales

## Les commits

* Ecrire de bons messages de commits comme expliqué ici <https://chris.beams.io/posts/git-commit/>
* Préciser les numéros des Issues, des Tickets ou autres tâches (JIRA, ...) dans le message du commit (1 commit par tâche)

## Références

### Anti-sèches

* [Git Commands and Best Practices Cheat Sheet](https://zeroturnaround.com/rebellabs/git-commands-and-best-practices-cheat-sheet/)

### Liens

* <https://guillaumebriday.fr/comment-jutilise-git-mes-astuces-et-bonnes-pratiques>
* <https://wiki.resel.fr/Guides/bonnes-pratiques/git>
* <https://danielkummer.github.io/git-flow-cheatsheet/index.fr_FR.html>
* <http://blog.soat.fr/2016/12/avoir-une-bonne-strategie-avec-git-flow/>
* <https://www.grafikart.fr/formations/git/git-flow>
* <http://nvie.com/posts/a-successful-git-branching-model/>

### Vidéos

* [[Devoxx 2016] Git : tips & tricks](https://www.youtube.com/watch?v=B5F1tU9dFOo)
* [[Devoxx 2015] Comment git a sauvé notre projet ou presque](https://www.youtube.com/watch?v=WVZKzFnfii4)
* [[Grafikart.fr] Comprendre Git](https://www.youtube.com/watch?v=D5QGiIM1j20)
* [[DevFest Nantes 2018] Git Dammit !](https://www.youtube.com/watch?v=Rnh5QK__pLA) - [Présentation](https://mghignet.github.io/git-dammit-talk/)
