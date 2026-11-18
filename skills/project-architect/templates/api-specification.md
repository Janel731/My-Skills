# Spécification des Contrats d'API — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/05-architecture/api-specification.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Architecture](./system-overview.md) | [Modèle de données](./data-model.md) | [Sécurité](./security.md) | [Écrans](../04-ux-ui/screens/screen-001.md)

## 1. Conventions globales de l'API
- **Style et Base URL :** REST JSON sur HTTPS — `/api/v1`
- **Authentification :** [Ex. Cookie de session `HttpOnly; Secure; SameSite=Lax` ou Header `Authorization: Bearer <token>`]
- **Format des dates et fuseaux horaires :** ISO 8601 UTC (`YYYY-MM-DDTHH:mm:ssZ`).
- **Pagination standard des listes :**
  - Requête : `?cursor=<id>&limit=20` (ou `?page=1&limit=20`, avec `limit <= 100`).
  - Réponse : `{ "data": [...], "meta": { "nextCursor": "...", "total": 142 } }`.
- **Format standardisé des erreurs (compatible avec l'état Erreur des écrans `SCR-xxx`) :**
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Certains champs du formulaire sont invalides.",
    "requestId": "req_01J...",
    "details": [
      { "field": "email", "reason": "Format d'adresse e-mail invalide." }
    ]
  }
}
```

## 2. Inventaire synthétique des Endpoints (`API-xxx`)
| ID API | Méthode & Chemin | Objectif | Rôles autorisés (`ACT-xxx`) | Écrans consommateurs (`SCR-xxx`) | Exigence (`FR-xxx`) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `API-001` | `GET /api/v1/resources` | Lister et filtrer les ressources | `ACT-001` | `SCR-002` | `FR-001` |
| `API-002` | `POST /api/v1/resources` | Créer une ressource | `ACT-001` | `SCR-002`, `SCR-003` | `FR-002` |

## 3. Spécification détaillée des Endpoints

### `API-001` — `[METHOD] /api/v1/[resource]`
- **Objectif :** [Description précise]
- **Exigences, Règles métier & Écrans liés :** `FR-001`, `BR-001`, `SCR-001`
- **Authentification & Permissions :** Requis (`ACT-001`). Vérification serveur que `resource.owner_id == current_user.id`.
- **Rate Limiting & Idempotence :** [Ex. `60 req/min/user`, en-tête `Idempotency-Key` requis sur les mutations critiques.]
- **Paramètres de chemin / query :**
  - `status` (optionnel, `enum`: `PENDING | CONFIRMED`)
  - `limit` (optionnel, `integer`, défaut `20`, max `100`)
- **Schéma de la Requête (Request Body) :**
```json
{
  "title": "Chaîne obligatoire (3 à 120 caractères)",
  "amountCents": 12500
}
```
- **Règles de validation serveur :**
  - `title` : `trim()`, non vide, longueur `3..120`.
  - `amountCents` : entier strictement positif (`> 0`), conforme à `BR-001`.
- **Schéma de la Réponse nominale (`200 OK` / `201 Created`) :**
```json
{
  "data": {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "title": "Exemple",
    "amountCents": 12500,
    "status": "PENDING",
    "createdAt": "2026-11-18T14:30:00Z"
  }
}
```
- **Codes HTTP et Erreurs métier :**
  - `400 / 422 Unprocessable Entity` : `VALIDATION_ERROR` ou violation de `BR-001`.
  - `401 Unauthorized` : Session absente ou expirée (déclenche la redirection `SCR-001`).
  - `403 Forbidden` : Rôle insuffisant ou ressource appartenant à un autre compte.
  - `404 Not Found` : Identifiant inexistant.
  - `409 Conflict` : Doublon ou transition d'état illégale.
  - `429 Too Many Requests` : Quota dépassé.

## 4. Webhooks et Événements asynchrones (si applicable)
- **Origine / Destination :** [...]
- **Vérification de signature et sécurité :** [En-tête HMAC, fenêtre anti-rejeu (timestamp), déduplication par `event_id`.]
