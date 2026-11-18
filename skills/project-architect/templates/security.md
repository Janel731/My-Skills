# Architecture de Sécurité & Confidentialité — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/05-architecture/security.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Architecture](./system-overview.md) | [Modèle de données](./data-model.md) | [API](./api-specification.md) | [Registre des Risques](../06-quality/risk-register.md)

## 1. Actifs critiques et classification des données
| Actif / Donnée (`ENT-xxx`) | Niveau de sensibilité | Impact en cas de compromission | Mesure de protection principale |
| :--- | :--- | :--- | :--- |
| Identifiants & Sessions (`ENT-001`) | Secret / Critique | Usurpation de compte | Hachage Argon2id / Cookie `HttpOnly; Secure` |
| Données personnelles (PII) | Sensible (RGPD) | Fuite de données, risque légal | Contrôle d'accès strict, TLS, minimisation |

## 2. Frontières de confiance et Modèle de menaces (Threat Modeling)
| Scénario de menace | Vecteur d'attaque | Cible (`API-xxx` / `SCR-xxx`) | Mesure de prévention / contrôle | Test associé (`TEST-xxx`) |
| :--- | :--- | :--- | :--- | :--- |
| Accès aux données d'un autre utilisateur (IDOR/BOLA) | Modification d'ID dans l'URL ou l'API | `API-001`, `SCR-002` | Filtrage serveur obligatoire par `owner_id` / Row-Level Security | `TEST-006` |
| Force brute ou abus de quota | Appels automatisés massifs | `/login`, endpoints coûteux | Rate limiting par IP et par compte + verrouillage progressif | `TEST-008` |
| Injection (XSS / SQL / Commande) | Champs de saisie ou fichiers | Tous les formulaires | Requêtes paramétrées, validation serveur, CSP et échappement HTML | `TEST-009` |

## 3. Authentification et Gestion des Sessions
- **Mécanisme retenu :** [Ex. Session serveur / JWT court + Refresh token rotatif / OAuth2] (voir [ADR-002](../adr/ADR-002.md)).
- **Cycle de vie :** Expiration, révocation à la déconnexion, réinitialisation de mot de passe par jeton à usage unique limité dans le temps.

## 4. Matrice d'Autorisation et Contrôle d'Accès (`ACT-xxx`)
| Ressource / Action | Anonyme | `ACT-001` (Utilisateur) | `ACT-002` (Admin) | Règle d'isolation |
| :--- | :--- | :--- | :--- | :--- |
| Consulter ses propres données | Refus (`401`) | Autorisé (`owner_id == self`) | Autorisé | Isolation stricte par propriétaire |
| Administrer la plateforme | Refus (`401`) | Refus (`403`) | Autorisé | Journalisation d'audit obligatoire |

## 5. Sécurité applicative, Secrets et Dépendances
- **En-têtes et transport :** HTTPS/TLS obligatoire, `Content-Security-Policy`, `X-Content-Type-Options: nosniff`, `Referrer-Policy`, CORS restrictif.
- **Gestion des secrets :** Aucun secret dans Git ni dans le bundle frontend ; variables injectées côté serveur uniquement.
- **Téléversement de fichiers (si applicable) :** Contrôle MIME réel, taille maximale, stockage isolé, URLs signées à durée limitée.

## 6. Confidentialité et Conformité (RGPD / Données personnelles)
- **Minimisation et finalité :** [...]
- **Durées de conservation et purge :** [...]
- **Exercice des droits utilisateurs (Export, Suppression) :** [...]
- **Points juridiques à confirmer :** `[POINT EN ATTENTE : validation mentions légales / politique de confidentialité par le porteur de projet]`.
