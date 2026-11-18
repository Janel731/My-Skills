# Spécification des Exigences Fonctionnelles et Non Fonctionnelles — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/03-product-design/requirements.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Périmètre](../01-discovery/scope.md) | [Personas](./personas.md) | [User Flows](./user-flows.md) | [Critères d'Acceptation](../06-quality/acceptance-criteria.md) | [Traçabilité](../07-delivery/traceability.md)

## 1. Acteurs et Matrice des Permissions (`ACT-xxx`)
| ID | Acteur / Rôle | Description | Permissions accordées | Restrictions explicites |
| :--- | :--- | :--- | :--- | :--- |
| `ACT-001` | [Rôle 1] | [Description] | [Actions autorisées] | [Actions interdites] |

## 2. Règles Métier transverses (`BR-xxx`)
| ID | Règle métier | Formulation exacte (Invariant ou calcul) | Exigences & Écrans impactés (`FR-xxx`, `SCR-xxx`) | Origine & Statut |
| :--- | :--- | :--- | :--- | :--- |
| `BR-001` | [Nom de la règle] | [Définition sans ambiguïté] | `FR-001`, `SCR-001` | `EXPLICIT` — `[DECISION VALIDEE]` |

## 3. Inventaire synthétique des Exigences Fonctionnelles (`FR-xxx`)
| ID | Fonctionnalité | Acteur(s) | Priorité (MoSCoW) | Version cible | Origine (`EXPLICIT`/`INFERRED`/`RECOMMENDED`) | Écrans liés (`SCR-xxx` ou `N/A`) | Statut |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `FR-001` | [Titre atomique] | `ACT-001` | `Must` | MVP | `EXPLICIT` | `SCR-001` | `[DECISION VALIDEE]` |

## 4. Spécification détaillée des Exigences Fonctionnelles

### `FR-001` — [Nom de la fonctionnalité]
- **Priorité & Version :** `Must (MVP)` | **Origine :** `EXPLICIT` | **Statut :** `[DECISION VALIDEE]`
- **Acteurs & Personas :** `ACT-001` (`PER-001` ou `N/A`)
- **Objectif / Valeur :** [Quel problème cette exigence résout-elle ?]
- **User Flows & Écrans liés :** `UF-001`, `SCR-001` (ou `N/A — traitement backend sans interface`)
- **Préconditions :** [État requis avant l'action.]
- **Scénario nominal :**
  1. [Étape 1]
  2. [Étape 2]
- **Scénarios alternatifs :**
  - [Variante A]
- **Cas d'erreur et cas limites :**
  - [Erreur 1 -> comportement système et message utilisateur]
- **Règles métier appliquées :** `BR-001` (ou `N/A`)
- **Données manipulées & API :** `ENT-001`, `API-001` (ou `N/A`)
- **Critères d'acceptation (`AC-xxx` — `Given / When / Then`) :**
  - **`AC-001` (Nominal) :** *Given* [contexte], *When* [action], *Then* [résultat observable].
  - **`AC-002` (Erreur/Validation) :** *Given* [contexte], *When* [action invalide], *Then* [message et état conservé].

## 5. Exigences Non Fonctionnelles (`NFR-xxx`)
| ID | Catégorie | Exigence mesurable et seuil cible | Critère & Test associés (`AC-xxx`, `TEST-xxx`) | Priorité | Statut |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `NFR-001` | Performance | [Ex. Temps de réponse API `p95 < 300ms` sous charge nominale] | `AC-010`, `TEST-007` | `Must` | `[RECOMMANDATION]` |
| `NFR-002` | Accessibilité | [Ex. Conformité WCAG 2.1 AA, contraste `>= 4.5:1`, navigation 100 % clavier] | `AC-011`, `TEST-005` | `Must` | `[DECISION VALIDEE]` |
| `NFR-003` | Sécurité | [Ex. Contrôle d'accès serveur par ressource et sessions HTTP-only] | `AC-012`, `TEST-006` | `Must` | `[DECISION VALIDEE]` |
