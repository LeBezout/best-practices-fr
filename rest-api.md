# Conception d'API REST

## Utilisation des verbes HTTP

* **GET** est utilisé pour lire des collections `orders` ou des instances `orders/128`.
* **POST**  est utilisé pour créer une nouvelle instance. On retournera alors dans le _header_ `location` l'emplacement de l'élément créé et l'on retournera généralement un statut 201 (_Created_).
* **PUT**  est utilisé pour mettre à jour une instance avec l'intégralité des données.
* **PUT**  est utilisé pour créer une nouvelle instance **si l'ID est fourni par le client** (ce qui est rare).
* **PATCH**  est utilisé pour mettre à jour une instance avec des données partielles.
* **DELETE**  est utilisé pour supprimé un élement, on retournera généralement un statut 204 (_No Content_).

## Utilisation des status HTTP

### Succès

* Utiliser **200** pour le cas général indiquant un succès.
* Utiliser **201** pour indiquer une création.
* Utiliser **202** dans le cas d'un traitement asynchrone.
* Utiliser **204** pour indiquer un contenu vide, par exemple après un _DELETE_.

### Erreurs du client

* Utiliser **400** pour le cas général indiquant au client qu'il pas fournie les données attendues ou qu'elle ne sont pas dans le bon format.
* Utiliser **401** pour indiquer une erreur d'authentification (sans préciser la raison).
* Utiliser **403** pour indiquer un manque d'habilitations (l'authentification est quant à elle OK).
* Ne pas utiliser **404** (préférer plutôt retourner une liste vide ou un élément vide) car se code sera automatiquement utilisé dans les cas d'URL invalide.
* Utiliser **406**  pour indiquer un contenu_partiel, comme par exemple une liste paginée.

### Erreurs du server

* Utiliser uniquement  **500** avec un message générique masquant l'erreur (_une erreur est survenue, veuillez contacter ..._).

## Le nommage

* Contrairement à SOAP on l'on utilisait des **verbes** pour décrire les opérations, en REST on expose des ressources on utilise donc des **noms**.
* Pour certains cas à la marge on pourra exposer des opérations ou des services, on utilisera alors le verbe POST et on terminera l'URI par un verbe.
* Utiliser le pluriel pour identifier les ressources : `orders`, `orders/128`, `users`, `users/256`, ...
* Standardiser le nommage et ne pas mélanger les styles : `PascalCase`, `camelCase`, `snake_case`, `spinal-­case`, `UPPERCASE`, `lowercase`, en choisir un et s'y tenir sur toute l'API.
* Pour trier, filtrer ou affiner on utilisera les paramètres de requêtes : `/orders?page=2`,  `/orders?state=paied` `/orders?sortBy=name`.

## La sécurité

* Utiliser le protocole HTTPS.
* Utiliser les protocoles OpenID Connect & OAuth2 pour gérer l'authentification.
* Utiliser un message générique en cas d'erreur d'authentification, n'indiquer si pas si c'est un mauvais compte ou un mauvais mot de passe.
* Ne pas utiliser de session, rester _stateless_.
* Tracer les appels critiques dans les journaux de l'application (qui fait quoi, quand et sur quelle ressource).

## La performance

* Exposer les données suivant les besoins des clients des API par suivant notre modèle, par exemple en n'exposant que le strict nécessaire.
* Toutes les listes doivent **obligatoirement** être paginées, sans paramètres reçu du client une pagination par défaut sera utilisée.
* Retourner des réponses (JSON principalement) minifiées.

## L'interopérabilité

* Utiliser le format ISO 8601 comme format de date.
* Standardiser et document le format des réponses en cas d'erreur.

## Liens utiles

* :gb: [HTTP API Design](https://legacy.gitbook.com/book/geemus/http-api-design)