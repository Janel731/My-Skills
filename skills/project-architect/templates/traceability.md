# Matrice de Traçabilité Relationnelle — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/07-delivery/traceability.md`
- **Profil documentaire :** `Compact` | `Standard` | `Complet`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Exigences](../03-product-design/requirements.md) | [Sitemap](../03-product-design/sitemap.md) | [Vue d'ensemble du système](../05-architecture/system-overview.md) | [Décisions d'architecture](../05-architecture/architecture-decisions.md) | [Critères d'acceptation](../06-quality/acceptance-criteria.md) | [Stratégie de Tests](../06-quality/test-strategy.md)

## 1. Principes de traçabilité proportionnée et flexible

La traçabilité relie les exigences aux artefacts de conception et de vérification **selon la pertinence métier et technique réelle**, et non selon une chaîne linéaire rigide :

- **Relations multiples ou optionnelles :** Une exigence peut être liée à plusieurs écrans, plusieurs endpoints ou plusieurs règles métier. Inversement, certaines dimensions peuvent être légitimement `N/A` (ex. un traitement batch ou une exigence de chiffrement base de données n'a ni écran `SCR-xxx` ni composant UI `COMP-xxx` ; une page d'information statique n'a ni contrat `API-xxx` ni entité `ENT-xxx`).
- **Justification des absences significatives :** Lorsqu'une relation habituellement attendue est absente (`N/A`), une justification courte explique pourquoi afin de prouver qu'il ne s'agit pas d'un oubli.
- **Proportionnalité au profil documentaire :**
  - *Profil Compact :* Traçabilité essentielle reliant `FR-xxx` / `NFR-xxx` → `SCR-xxx` (ou composant technique) → `AC-xxx` / `TEST-xxx` (peut être intégrée directement à la fin de `requirements.md`).
  - *Profil Standard :* Matrice complète ci-dessous couvrant les exigences du MVP et leurs relations pertinentes.
  - *Profil Complet :* Matrice exhaustive bidirectionnelle + audit des éléments orphelins et suivi individuel par critère d'acceptation `AC-xxx`.

## 2. Nomenclature des identifiants reliés

- `FR-001`... : Exigence fonctionnelle (*Functional Requirement*)
- `NFR-001`... : Exigence non fonctionnelle (*Non-Functional Requirement*)
- `BR-001`... : Règle métier (*Business Rule*)
- `UJ-001` / `UF-001`... : User Journey / User Flow
- `SCR-001`... : Écran ou vue spécifiée
- `COMP-001`... : Composant du Design System
- `API-001`... : Contrat d'API, webhook ou événement
- `ENT-001`... : Entité ou structure de données
- `ADR-001`... : Décision architecturale (*Architecture Decision Record*)
- `AC-001`... : Critère d'acceptation (*Acceptance Criterion*)
- `TEST-001`... : Scénario ou suite de test

## 3. Matrice des relations de traçabilité

| ID Exigence (`FR` / `NFR`) | Description synthétique | Règles & Parcours (`BR`, `UJ`, `UF`) | Interface (`SCR`, `COMP`) | Architecture & Données (`API`, `ENT`, `ADR`) | Validation (`AC`, `TEST`) | Justification des relations absentes (`N/A`) | Statut de couverture | Documents de référence |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `FR-001` | [Création d'une commande par un client connecté] | `BR-001`, `UJ-001`, `UF-001` | `SCR-002`, `COMP-001`, `COMP-002` | `API-001`, `ENT-001`, `ENT-002`, `ADR-002` | `AC-001`, `AC-002`, `TEST-001`, `TEST-004` | — (Toutes dimensions applicables) | `COMPLET` | [requirements.md](../03-product-design/requirements.md), [screen-002.md](../04-ux-ui/screens/screen-002.md), [api-specification.md](../05-architecture/api-specification.md) |
| `FR-002` | [Purge nocturne automatique des sessions expirées] | `BR-002` | `N/A` | `ENT-001`, `ADR-003` | `AC-003`, `TEST-002` | `UJ/UF/SCR/COMP/API : N/A` (Tâche cron purement interne au backend sans interaction utilisateur ni endpoint public) | `COMPLET` | [requirements.md](../03-product-design/requirements.md), [data-model.md](../05-architecture/data-model.md) |
| `FR-003` | [Consultation de la page statique d'aide et mentions] | `UF-002` | `SCR-001`, `COMP-003` | `N/A` | `AC-004`, `TEST-003` | `BR/API/ENT/ADR : N/A` (Contenu éditorial statique pré-rendu sans persistance ni appel API) | `COMPLET` | [requirements.md](../03-product-design/requirements.md), [screen-001.md](../04-ux-ui/screens/screen-001.md) |
| `NFR-001` | [Accessibilité clavier et contraste WCAG 2.1 AA] | `UF-001`, `UF-002` | Tous les `SCR-xxx` & `COMP-xxx` | `ADR-004` | `AC-005`, `TEST-005` | `BR/API/ENT : N/A` (Exigence transverse de couche présentation) | `COMPLET` | [design-system.md](../04-ux-ui/design-system.md), [test-strategy.md](../06-quality/test-strategy.md) |

## 4. Contrôle d'intégrité et de couverture

- **Exigences du MVP sans critère d'acceptation (`AC-xxx`) ni test (`TEST-xxx`) :** `Aucune` (ou lister les éléments `PARTIEL` / `À COMPLÉTER`).
- **Artefacts aval orphelins (Écran `SCR-xxx`, Endpoint `API-xxx` ou Entité `ENT-xxx` non reliés à au moins une exigence `FR-xxx` ou `NFR-xxx`) :** `Aucun` (garantit l'absence de sur-ingénierie hors périmètre).
