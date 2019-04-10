# Bonnes pratiques d'utilisation de GIT

## Rappel des concepts

![concept](git_concepts_en.png)

## La configuration utilisateur

:pushpin: Pour éviter les problèmes et pouvoir interagir correctement avec GIT il faut une bonne configuration de son poste de travail :

* Chaque utilisateur doit avoir un fichier `.gitconfig` correctement renseigné (à minima avec `user.name` et `user.email`).
* Vérifier votre configuration personnelle en tapant `git config --global --list  --show-origin`.
* Vérifier que cette configuration est bien celle prise en compte par vos différents IDE.

## L'initialisation du dépôt

:pushpin: Respecter les quelques éléments présentés ci-dessous permet d'assurer pour le système sa maintenabilité et son exploitabilité.

* Chaque dépôt doit contenir à la racine un fichier `README.md` permettant de décrire celui-ci.
* Chaque dépôt doit contenir à la racine un fichier `.gitignore` permettant de ne pas remonter n'importe quoi dans le système.
* Chaque dépôt doit contenir à la racine un fichier `.gitattributes` permettant de gérer correctement le format des fichiers (binaire ou texte, windows ou unix).
* Optionnellement on peut rajouter à la racine un fichier `CONTRIBUTING.md` permettant de décrire les normes internes.

## Le format des fichiers

:pushpin: Quelques règles simples de mise en oeuvre pour éviter les problèmes liés au format des fichiers remontés :

* Toujours terminer ses fichiers par une ligne vide.
* Préférer les espaces (2 à 4) par rapport aux tabulations.
* Utiliser par exemple un fichier `.editorconfig` et les plugins associés dans les différents IDE.
* Vérifier que l'extension du fichier est bien gérée dans le fichier `.gitattributes`.

## Méthodologies

:pushpin: Utiliser et respecter et partager une certaine rigueur méthodologique va faciliter le travail en équipe et améliorer la qualité des livrables :

* Apprendre à maîtriser les principales commandes de bases : `add`, `commit`, `pull`, `push`, `checkout`, `branch`, ...
* Suivre le didacticiel en ligne [Leaning Git Branching](https://learngitbranching.js.org/) pour comprendre ou revoir certains concepts.
* Travailler dans ses propres branches (et les mettre à jour régulièrement via merge pour éviter d'avoir trop de conflits à résoudre lors du merge final)
* Pousser (`push`) régulièrement sur le serveur pour éviter de perdre malencontreusement son travail (idéalement sur sa propre branche).
* Favoriser l'utilisation de _Pull Requests_ (GitHub) ou _Merge Requests_ (GitLab) et de revues collégiales.
* Utiliser une méthode du type GitFlow, JGit-Flow, GitHub Flow, GitLab Flow, etc...

## Les commits

:pushpin: Les messages de commit, voir les commits sont souvent négligés. C'est une mauvaise pratique aboutissant à un historique peu clair (dégradant la maintenabilité). Quelques consignes à respecter :

* Écrire de bons messages de commits comme expliqué ici <https://chris.beams.io/posts/git-commit/>.
* Écrire des messages de commits clairs, explicites et concis. Partager votre norme entre tous les développeurs.
* Ne pas mélanger différentes choses : un commit = une fonctionnalité / une correction.
* Préciser quand c'est possible les numéros des Issues, des Tickets ou autres tâches (JIRA, ...) dans le message du commit (1 commit par tâche).
* Éviter les "commit merge" si ce n'est pas nécessaire, utiliser par exemple `git pull --rebase` ou la configuration `pull.rebase=true` par exemple.
* Avant de pousser des modifications liées ne pas hésiter à les regrouper dans un seul commit (fonctionnellement cohérent et homogène) via la fonctionnalité de "_squash_" (via `git rebase -i`).
* Limiter l'utilisation de la commande `git commit -m 'message'` car elle contraint le message à la première ligne, ce qui dans certains cas est insuffisant.

## Références

### Anti-sèches

* [Git Commands and Best Practices Cheat Sheet](https://zeroturnaround.com/rebellabs/git-commands-and-best-practices-cheat-sheet/) par _zeroturnaround_
* [GIT Cheat Sheet](https://groupe-sii.github.io/cheat-sheets/git/index.html) par _SII_
* [GIT Cheat Sheet](https://about.gitlab.com/images/press/git-cheat-sheet.pdf) par _GitLab_
* [GIT Cheat Sheets](https://github.github.com/training-kit/) par _GitHub_

### Liens

* [Lean Git Branching - site d'entraînement](https://pcottle.github.com/learnGitBranching/?demo)
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
