# La documentation

## Considérations générales

### Les différents types

* **La documentation technique**
  * Architecture logicielle
  * Architecture technique
  * Conception technique
  * Guide du développeur
  * Normes de développement
  * Guide de bonnes pratiques
  * FAQ (interne ou externe)
* **La documentation fonctionnelle**
  * Guides ou manuels utilisateurs (externe)
  * Spécifications, expressions des besoins
  * FAQ (interne ou externe)

### Les différents formats

* **Pour la rédaction :**
  * Propriétaire (Word, PPT, Confluence)
  * Markdown
  * Asciidoc
* **Pour l'export :**
  * PDF
  * HTML

### La documentation implicite

* Les commentaires (attention peuvent rapidement devenir obsolètes ou erronés)
* La Javadoc
* Swagger / OpenAPI (documentation d'API)
* Les tests unitaires
* Les scénarios de tests
* Les _changelog_ ou _Release Notes_
* L'historique des _commits_ Git
* Les discussions des _issues_ GitLab/GitHub
* Les discussions de _Merge Requests_ GitLab / _Pull Requests_ GitHub

### Les contraintes à prendre en compte

* La durée de validité des informations
* La pertinence des informations
* La population ciblée (type, niveau de connaissance, ...)

## Bonnes pratiques

### Ne documenter que l'essentiel

:pushpin: La documentation prend du temps il est donc important de se concentrer sur ce qui apporte de la valeur.

* Valider préalablement en équipe les besoins ou manques.
* Ne pas dupliquer, ré-écrire ou paraphraser une documentation existante : référencer la documentation officielle et ajouter vos éventuelles spécificités ou vos remarques.
* Considérer l'écriture des ADR (_Architectural Decision Records_) :
  * C'est le journal de toutes les décisions architecturales prises durant la vie du projet.
  * Ce journal permet de connaître l'historique et surtout les justifications des grandes décisions techniques prises au cours de la vie du projet.
  * Il devient particulièrement utile quand les personnes qui ont prises les décisions ne sont plus la et pour les nouveaux arrivants.
  * Ce journal fait partie intégrante du dépôt de sources, le format Markdown est donc le plus adapté, sa structure doit être standardisée.

### Assurer la maintenabilité

:pushpin: Il n'y a rien de pire qu'une documentation erronée ou obsolète. La documentation pour être utile doit être fiable, à jour et vivante et donc elle doit pouvoir être facilement mise à jour.

* Choisir l'outil validé par l'équipe qui va maintenir la documentation (qui n'est pas forcément celle qui va la lire ou la valider).
* Éviter les gros pavés, les gros fichiers, favoriser une documentation modulaire, bien découpée.
* Favoriser les pratiques de type _Documentation as Code_ :
  * Gestion des versions et des retours en arrière.
  * Pratique de revues collectives.
  * Soumissions de _Pull/Merge Request_.
* Limiter le copier-coller (blocs de code, ...) qui peut vite engendrer de l'obsolèscence et donc de la maintenance.

### Améliorer la lisibilité

:pushpin: Personne n'aime lire ou maintenir de la documentation il faut donc la rendre la plus claire et lisible possible.

* Les titres doivent être explicites et clairs.
* Éviter les blocs trop longs, essayer d'être synthétique.
* Rester concis et pertinent, éviter le superflus et le trop littéraire.
* Soigner l'orthographe et les accords (utiliser des _spell checker_ dans vos outils et IDE) et la ponctuation.
* Lever les ambiguïtés :
  * Écrire au présent et à la voix active.
  * Éviter les synonymes, utiliser toujours le même terme pour désigner la même chose.
* Garder le même style et les mêmes normes tout au long de la documentation :
  * Polices de caractères.
  * Format des titres et sous-titres.
  * Format des sections (blocs de code, ...).
  * Format des listes à puces.
* Ne pas négliger l'ajout de schémas ou d'images, ou d'extraits de code source :
  * Rend la documentation plus facile à lire, plus compréhensible.
  * Attire le regard, attise la curiosité.
  * Attention néanmoins aux copie d'écrans et blocs de code qui peuvent vite devenir obsolètes.

### Impliquer toute l'équipe

:pushpin: La documentation est l'effort de toute l'équipe. Il est important que toute l'équipe y soit impliquée.

* C'est un processus collaboratif : plusieurs cerveaux valent mieux qu'un.
* C'est un processus itératif : on a rarement bon du 1er coup, tout seul.
* La documentation doit être revue et validée par l'équipe.

### Utilisez l'outil de documentation approprié

:pushpin: Le choix du bon outil de rédaction peut permettre de gagner du temps ainsi qu'en qualité sur le résultat produit.

On choisira un outil :

* adapté au type de documentation :
  * des graphiques, schémas, diagrammes : draw.io, ...
  * une documentation fonctionnelle : page Confluence, ...
  * une documentation technique : outil et format à valider par l'équipe de développement.
* adapté à la population ciblée :
  * Développeurs du projet : Markdown intégré au dépôt de sources.
  * Équipe projet : espace Confluence, ...
  * Utilisateurs du produit : directement intégrée au produit.

## Annexes

### Annexe 1 : quelques outils de génération de diagrammes

* [PlantUML](https://plantuml.com/fr/) : génération de diagrammes sous forme d'images à partir d'une syntaxe textuelle
* [Mermaid](https://mermaid-js.github.io/mermaid/#/) : génération de diagrammes à partir d'une syntaxe textuelle, directement insérable dans des fichiers au format Markdown
* [Draw.io](https://www.draw.io/) : outil graphique gratuit de génération de diagrammes avec possibilité d'export dans différents formats.
* [MagicDraw](https://www.nomagic.com/products/magicdraw) : outil payant

### Annexe 2 : quelques outils de génération de sites

* [GitHub Pages](https://pages.github.com/)
* [GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/)
* [Hugo](https://gohugo.io/)
* [Jekyll](https://jekyllrb.com/)
* [Apache Maven](https://maven.apache.org/) et tous les types de plugins de _reporting_

### Annexe 3 : outils conseillés pour Markdown

* [MarkText](https://marktext.app/) : _Simple and Elegant Markdown Editor : Focused on speed and usability_
* [Microsoft Visual Studio Code](https://code.visualstudio.com/)
  * Extension _MarkdownLint_ `davidanson.vscode-markdownlint` _Markdown linting and style checking for Visual Studio Code_
  * Extension _Markdown Emoji_ `bierner.markdown-emoji` _Adds emoji syntax support to VS Code's built-in markdown preview_
  * Extension _Markdown Preview Github Styling_ `bierner.markdown-preview-github-styles` _Changes VS Code's built-in markdown preview to match Github's style_
  * Extension _Code Spell Checker_`streetsidesoftware.code-spell-checker` _Spelling checker for source code_
  * Extension _French - Code Spell Checker_ `streetsidesoftware.code-spell-checker-french` _French dictionary extension for VS Code_

### Annexe 4 : outils conseillés pour AsciiDoc

* [Microsoft Visual Studio Code](https://code.visualstudio.com/)
  * Extension _AsciiDoc_ `joaompinto.asciidoctor-vscode` _Provides rich language support for AsciiDoc_
* [AsciiDocFX](https://asciidocfx.com/)
* [Ruby](https://www.ruby-lang.org/fr/) installé via [Ruby Version Manager](http://rvm.io/)
  * Le "gem" [asciidoctor](https://asciidoctor.org/)
  * Le "gem" asciidoctor-diagram
  * Le "gem" [asciidoctor-pdf](https://github.com/asciidoctor/asciidoctor-pdf)
  * Le "gem" rouge (source-highlighter)
  * Le "gem" asciidoctor-plantuml

### Annexe 5 : conseils pour la rédaction des Javadocs

* Documenter toutes les classes et méthodes publiques ou _protected_.
* Préciser les comportements :
  * Préciser si une méthode peut engendrer un effet de bord (modification d'un élément fourni en paramètre).
  * Préciser si pour un paramètre de méthode la valeur `null` est acceptée.
  * Préciser si une méthode peut retourner `null`.
  * Dans le cas d'une méthode qui retourne une collection, préciser si celle-ci est mutable ou non.
  * Préciser si une classe est _Thread-Safe_ ou non.
* Ne pas surcharger inutilement la javadoc d'une méthode si elle n'apporte rien de plus que celle de la méthode parente.
* Syntaxe :
  * Utiliser les éléments de syntaxes évolués : `{@link Classe#methode(ParamType)}`, `{@code exemple("xxx");}`, `{@value}`, ...
  * Utiliser les tags HTML simples et non les tags XHTML. Exemple  `<br>` au lieu de `<br/>`.
  * Documenter les types génériques utilisés dans une méthode : `@param <T> le type`.
  * Préciser `@since X.y.Z` (méthodes et classes).
  * Préciser `@version` (classes, interfaces, enums uniquement).
* Compléter via `@deprecated raison` si une annotation `@Deprecated` est utilisée.
* Générer et valider les javadocs simplement en exécutant via Maven la commande `mvn javadoc:javadoc`.
