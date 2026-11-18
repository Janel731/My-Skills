# Conception et Spécification d'API (`docs/05-architecture/api-specification.md`)

## 1. Principes directeurs

1. **Orientation métier et expérience client** : Les contrats d'API (`API-001`...) sont conçus pour servir efficacement les parcours utilisateurs (`UF-xxx`), les écrans (`SCR-xxx`) et les consommateurs externes, sans exposer aveuglément la structure brute de la base de données.
2. **Cohérence des conventions globales** :
   - Format d'échange (JSON UTF-8 par défaut), convention de nommage (`camelCase` ou `snake_case` uniforme).
   - Gestion standardisée des dates/heures (ISO 8601 en UTC : `2026-11-18T14:30:00Z`), des identifiants (`UUIDv4/v7` ou IDs opaques) et des montants monétaires (en unité mineure entière — centimes — + code devise ISO 4217, ou décimal exact sous forme de chaîne pour éviter toute erreur de virgule flottante).
   - Format d'erreur unique et prévisible (inspiré de la RFC 9457 / Problem Details : `code`, `message`, `details` par champ, `requestId`) permettant à l'interface (`SCR-xxx`) d'afficher l'état d'erreur exact sans exposer de stacktrace interne.

## 2. Spécification de chaque endpoint ou opération (`API-xxx`)

Pour chaque contrat d'API (`API-001`, `API-002`...), précise :

- **Identifiant et Nom** : ex. `API-001 — Créer une commande`.
- **Exigences et Écrans liés** : `FR-xxx`, `SCR-xxx`, `UF-xxx`.
- **Méthode et Route / Canal** : ex. `POST /api/v1/orders` (ou opération GraphQL / événement WebSocket / commande RPC).
- **Authentification et Autorisation** : Type de jeton/session requis, rôle(s) autorisé(s) (`ACT-xxx`) et règle de vérification de propriété de la ressource (prévention IDOR / BOLA).
- **Paramètres d'entrée** : Path params, Query params (pagination, filtres, tri), Headers requis (ex. `Idempotency-Key`).
- **Schéma de la requête (Request Payload)** : Champs, types, caractère obligatoire et règles de validation serveur strictes.
- **Schéma de la réponse nominale (Response Payload)** : Code HTTP (`200`, `201`, `204`) et structure exacte retournée.
- **Codes HTTP et Erreurs métier possibles** :
  - `400 / 422` : Erreur de validation ou règle métier violée (`BR-xxx`).
  - `401` : Non authentifié.
  - `403` : Accès interdit à cette ressource.
  - `404` : Ressource introuvable.
  - `409` : Conflit d'état ou doublon.
  - `429` : Limite de débit dépassée (`Retry-After`).
  - `500 / 503` : Défaillance interne ou dépendance indisponible.
- **Idempotence, Rate Limiting et Cache** : Comportement en cas de double clic ou de réessai réseau.

## 3. Pagination, Filtrage, Webhooks et Événements

- **Collections et listes** : Toute route retournant une liste DOIT être paginée (pagination par curseur pour les flux temps réel/volumineux ou `page`/`limit` avec plafond strict `max_limit <= 100`) et documenter sa métadonnée de pagination.
- **Webhooks entrants et sortants** : Vérification obligatoire de la signature cryptographique (HMAC), traitement idempotent (déduplication par `event_id`), accusé de réception rapide et mécanisme de retry avec backoff exponentiel.
- **Versionnement** : Stratégie d'évolution sans rupture brutale pour les clients actifs (compatibilité ascendante, politique de dépréciation).
