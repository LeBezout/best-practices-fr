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
* Eviter les syntaxes alternatives 
* Partager vos conventions entre tous les membres de l'équipe

## Améliorer la lisbilité du document

* Découper en sections et sous-sections
* Utiliser les mises en formes gras ou italiques pour mettre en évidence des élements
* Agrémenter vos publications de petites icônes : information :information_source:, warning :warning:, astuce :bulb:, etc... Elles sont exprimées sous la forme `:code:` et directement interprétées par GitLab ou GitHub.
* Les liens doivent toujours être être encadrés de balises, soit `<lien>` soit `[libellé](lien)`
* Eviter les tabulations
* Spécifier toujours le langage dans les blocs de code multi-lignes : `shell`, `java`, `json`, `xml`, ..., par défaut utiliser `text`

## Trucs et astuces

* Nommer vos points d'entrée documentaire `README.md` comme çà ils seront automatiquement affichés sous forme de page HTML dans GitLab ou GitHub.
* Installer pour vos _browsers_ des extensions permettant de convertir (afficher) les fichiers Markdown sous forme de pages Web. Ces extensions se nomment souvent _Markdown Viewer_.
