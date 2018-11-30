# Bonnes pratiques de rédaction en Markdown

## Utiliser un éditeur évolué

Un éditeur évolué propose :

* la coloration syntaxique
* les contrôles de validation syntaxique
* l'aperçu du rendu final

Par exemple _Visual Studio Code_ qui propose quelques extensions :

* **indispensable** : `davidanson.vscode-markdownlint` Markdown linting and style checking for Visual Studio Code
* `yzane.markdown-pdf` Convert Markdown to PDF
* `bierner.markdown-preview-github-styles` Changes VS Code's built-in markdown preview to match Github's style

## Utiliser un outil de contrôle de la syntaxe

* Utiliser un outil de contrôle d'écriture (Linter) tel que "Markdown Lint".

## Normaliser

* Favoriser le plus possible la syntaxe standard
* Éviter les syntaxes alternatives (par exemple la syntaxe `Setext` et les blocs de code via indentation)
* Partager vos conventions entre tous les membres de l'équipe

## Améliorer la lisibilité du document

* Découper en sections et sous-sections
* Utiliser les mises en formes gras ou italiques ou les citations pour mettre en évidence des éléments
* Agrémenter vos publications de petites icônes : information :information_source:, warning :warning:, astuce :bulb:, etc... Elles sont exprimées sous la forme `:code:` et directement interprétées par GitLab ou GitHub.
* Les liens doivent toujours être être encadrés de balises, soit `<lien>` soit `[libellé](lien)`
* Éviter les tabulations
* Favoriser les blocs de code multi-lignes, réserver la syntaxe `code` pour mettre en évidence un nom de fichier, une commande, ...
* Spécifier toujours le langage dans les blocs de code multi-lignes : `shell`, `java`, `json`, `xml`, ..., par défaut utiliser `text`

## Attention aux fonctionnalités avancées

Il faut être conscient que certaines fonctionnalités ne sont pas dans le standard et que d'un interpréteur à l'autre le rendu peut être différent.

* des liens hypertextes automatiques
* une listes de tâches `* [ ] tâche`
* un texte barré `~~strike~~`
* un emoji :+1:
* des mentions d'un utilisateur, d'une _merge/pull request_ ou d'une _Issue_ `@user`
* l'alignement à l'intérieur des cellules dans une table (`|:------------|` gauche, `|------------:|` droite, `|:------------:|` centré)
* des notes de bas de page

## Trucs et astuces

* Nommer vos points d'entrée documentaire `README.md` comme çà ils seront automatiquement affichés sous forme de page HTML dans GitLab ou GitHub.
* Installer pour vos _browsers_ des extensions permettant de convertir (afficher) les fichiers Markdown sous forme de pages Web. Ces extensions se nomment souvent _Markdown Viewer_.
* Pour de plus grosses documentations ou des possibilités d'export plus évoluées (PDF, ePub, ..) penser au format **AsciiDoc**.

## Liens utiles

* [CommonMark Spec](https://spec.commonmark.org)
* [Adam Pritchard Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
