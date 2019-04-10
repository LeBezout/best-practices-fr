# Bonnes pratiques de rédaction en Markdown

![Markdown logo](https://upload.wikimedia.org/wikipedia/commons/4/48/Markdown-mark.svg)

## Avant-propos : pourquoi utiliser Markdown ?

* Contrairement à d'autres langages de balisage (comme HTML) son apprentissage est très facile et rapide, voire quasi immédiat.
* Partage simple et rapide de la documentation pour les développeurs car elle est directement intégrée et interprétée par GitHub ou GitLab.
* Profiter du versioning GIT car c'est un format textuel.
* La documentation produite peut être ensuite facilement exportée vers d'autres formats : PDF, HTML, ...
* C'est un bon début et un pré-requis pour appréhender un langage plus évolué comme le standard AsciiDoc.
* Pouvoir faire abstraction complètement de la mise en forme qui est une tâche hautement chronophage.
* La mise en forme des blocs de code indiqués en exemple est automatique (rapide, lisible).
* L'édition est rapide (soit directement depuis GitHub, GitLab) ou via n'importe quel éditeur de texte.
* La syntaxe _Markdown_ est également connue et interprétée dans différents outils : Mattermost, Trello, ... ou d'autres qui s'en rapprochent : Slack, Jira/Confluence, ...

## Utiliser un éditeur évolué

Un éditeur évolué propose :

* la coloration syntaxique
* les contrôles de validation syntaxique
* l'aperçu du rendu final

Par exemple _Visual Studio Code_ qui propose quelques extensions :

* **indispensable** : `davidanson.vscode-markdownlint` _Markdown linting and style checking for Visual Studio Code_
* `yzane.markdown-pdf` _Convert Markdown to PDF_
* `bierner.markdown-preview-github-styles` _Changes VS Code's built-in markdown preview to match Github's style_

Autres outils :

* Sous Windows [MarkdownPad](http://markdownpad.com/) (la version gratuite se limite à la syntaxe standard, pas de tableaux par exemple)
* Sous MacOS [Mou](http://mouapp.com/) ou [MarkdownNote](http://www.codingrobots.com/markdownnote/)
* Sous Gnome [Builder](https://wiki.gnome.org/Apps/Builder)
* en ligne [StackEdit!](https://stackedit.io/app#) ou [Dillinger](https://dillinger.io/)

## Utiliser un outil de contrôle de la syntaxe

Utiliser un outil de contrôle d'écriture (_Linter_) tel que [Markdown Lint](https://github.com/markdownlint/markdownlint).

Disponible sous forme de _command-line_ ou d'extensions :

* [pour VS Code](https://github.com/DavidAnson/markdownlint)
* [pour NodeJS](https://github.com/igorshubovych/markdownlint-cli)

## Normaliser

* Favoriser le plus possible la syntaxe standard en évitant les syntaxes alternatives (par exemple la syntaxe `Setext` et les blocs de code via indentation).
* Partager vos conventions entre tous les membres de l'équipe.
* Ajouter ou configurer un fichier `.editorconfig` pour gérer vos normes en rajoutant un bloc `[*.md]`.

## Améliorer la lisibilité du document

* Découper en sections et sous-sections.
* Utiliser les mises en formes gras ou italiques ou les citations pour mettre en évidence des éléments.
* Agrémenter vos publications de petites icônes (mais sans en abuser) : information :information_source:, warning :warning:, astuce :bulb:, etc... Elles sont exprimées sous la forme `:code:` et directement interprétées par GitLab ou GitHub.
* Les liens doivent toujours être encadrés de balises, soit `<lien>` soit `[libellé](lien)`.
* Éviter les tabulations.
* Favoriser les blocs de code multi-lignes. Réserver la syntaxe `code` pour mettre en évidence un nom de fichier, une commande, ...
* Spécifier toujours le langage dans les blocs de code multi-lignes : `shell`, `java`, `json`, `xml`, ..., par défaut utiliser `text`.
* Ajouter des schémas explicatifs, soit sous forme d'image référencée (PNG de préférence) ou directement avec la syntaxe [mermaid](https://mermaidjs.github.io/) connue et directement interprétée par GitLab ou GitHub.

## Attention aux fonctionnalités avancées

Il faut être conscient que certaines fonctionnalités ne sont pas dans le standard et que d'un interpréteur à l'autre le rendu peut être différent.

* des liens hypertextes automatiques
* une listes de tâches `* [ ] tâche`
* un texte barré `~~strike~~`
* un emoji :+1:
* des mentions d'un utilisateur `@user`, d'une _merge/pull request_ ou d'une _Issue_
* l'alignement à l'intérieur des cellules dans une table (`|:------------|` gauche, `|------------:|` droite, `|:------------:|` centré)
* des notes de bas de page

## Trucs et astuces

* Nommer vos points d'entrée documentaire `README.md` comme çà ils seront automatiquement affichés sous forme de page HTML dans GitLab ou GitHub.
* Installer pour vos _browsers_ des extensions permettant de convertir (afficher) les fichiers Markdown sous forme de pages Web. Ces extensions se nomment souvent _Markdown Viewer_.
* Pour de plus grosses documentations ou des possibilités d'export plus évoluées (PDF, ePub, ..) penser au format **AsciiDoc**.
* Un outil comme [DocToc](https://github.com/thlorenz/doctoc) permet de générer votre table des matières.

## Liens utiles

* [CommonMark Spec](https://spec.commonmark.org)
* [Adam Pritchard Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
