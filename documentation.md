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
  * Spécifications
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

* Ne pas dupliquer / ré-écrire / paraphraser une documentation existante
  * Référencer la documentation officielle et ajouter vos spécificités ou vos remarques
* Ne documenter que l'essentiel
  * La documentation prend du temps il est donc important de se concentrer sur ce qui apporte de la valeur
* La documentation doit être vivante et donc facilement modifiable
* La documentation doit être à jour et fiable
  * Rien de pire qu'une documentation erronée ou obsolète
* Ne pas négliger l'ajout de schémas ou d'images, ou d'extraits de code source :
  * Rend la documentation plus facile à lire, plus compréhensible
  * Attire le regard, la curiosité
  * Attention néanmoins aux copie d'écrans et blocs de code qui peuvent vite devenir obsolètes
* Favoriser les pratiques de type _Documentation as Code_ :
  * Versioning
  * Revue collectives
  * Pull/Merge Request
* La documentation est l'effort de toute l'équipe :
  * La documentation est un processus collaboratif
  * Toute l'équipe doit être impliquée
  * La documentation doit être revue et validée par l'équipe
* Lever les ambiguïtés :
  * Écrire au présent, à la voix active
  * Éviter les synonymes, utiliser toujours le même terme pour désigner la même chose
* Améliorer la lisibilité :
  * Les titres doivent être explicites et clairs
  * Éviter les blocs trop long, être synthétique
  * Rester concis et pertinent, éviter le superflus ou le trop littéraire
  * Éviter les gros pavés, les gros fichiers, favoriser une documentation modulaire
* Garder le même style et et les mes normes tout au long de la documentation :
  * Polices de caractères
  * Format des titres et sous-titres
  * Format des sections (blocs de code, ...)
  * Format des listes à puces
  * Majuscules, ponctuation, ...
* Utilisez l'outil de documentation approprié
  * Adapté au type de documentation
    * Graphiques, schémas, diagrammes : draw.io, ...
    * Fonctionnelle : page Confluence, ...
    * Technique : à valider avec l'équipe de développement
  * Adapté à la population ciblée
    * Développeurs du projet : Markdown intégré au dépôt de source
    * Équipe projet : espace Confluence, ...
* Considérer l'écriture des ADR (_Architectural Decision Records_)
  * C'est le journal de toutes les décisions architecturales prises durant la vie du projet.
  * Ce journal permet de connaître l'historique et surtout les justifications des grandes décisions techniques prises sur au cours de la vie du projet.
  * Particulièrement utile quand les personnes qui ont prises les décisions ne sont plus la.
  * Ce journal fait partie intégrante du dépôt de sources, le format Markdown est donc le plus adapté, sa structure doit être standardisée.
