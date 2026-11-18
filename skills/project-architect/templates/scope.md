# Périmètre du Projet (Scope) — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/01-discovery/scope.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Project Brief](./project-brief.md) | [Exigences](../03-product-design/requirements.md) | [Roadmap](../07-delivery/roadmap.md)

## 1. Définition du MVP (Minimum Viable Product)
[Justification du découpage du MVP : quel est le plus petit ensemble cohérent permettant de résoudre le problème central sans dette critique ?]

## 2. Périmètre fonctionnel par version

### 2.1. Inclus dans le MVP (`IN_SCOPE_MVP`)
| Domaine / Module | Capacités incluses | Références `FR-xxx` | Statut décisionnel |
| :--- | :--- | :--- | :--- |
| [Module 1] | [Capacité indispensable] | `FR-001`, `FR-002` | `[DECISION VALIDEE]` / `[DECISION PROPOSEE]` |

### 2.2. Reporté après le MVP (`POST_MVP`)
| Domaine / Module | Capacités reportées | Raison du report | Version cible |
| :--- | :--- | :--- | :--- |
| [Module 2] | [Capacité secondaire] | [Non bloquant pour la validation initiale] | V1.1 / V2 |

### 2.3. Explicitement hors périmètre (`OUT_OF_SCOPE`)
- **[Exclusion 1] :** [Pourquoi cet élément est exclu afin d'éviter toute ambiguïté avec l'équipe de développement.]
- **[Exclusion 2] :** [...]

## 3. Périmètre des plateformes, langues et intégrations
- **Plateformes supportées au lancement :** [Ex. Web responsive Desktop & Mobile ; pas d'application native iOS/Android au MVP.]
- **Langues et localisation (i18n/l10n) :** [Ex. Français uniquement au MVP, fuseaux horaires, devises.]
- **Intégrations tierces incluses au MVP :** [Ex. Paiement, e-mail transactionnel, authentification.]
- **Intégrations tierces reportées :** [...]

## 4. Règles de maîtrise du périmètre (Anti-Scope Creep)
Toute demande d'ajout d'une fonctionnalité au MVP après passage de ce document au statut `APPROVED` nécessite :
1. L'évaluation de son impact sur les écrans (`SCR-xxx`), le modèle de données (`ENT-xxx`), l'API (`API-xxx`) et la roadmap.
2. Le retrait ou le report d'une fonctionnalité de complexité équivalente, ou l'acceptation explicite du décalage associé.
