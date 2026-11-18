# Documentation d'Architecture & Product Design — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Profil documentaire retenu :** `Compact` | `Standard` | `Complet`
- **Statut global du blueprint :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Dernière mise à jour :** [YYYY-MM-DD]
- **Version :** [0.1]

## 1. Vue d'ensemble du projet et justification du profil documentaire
- **Résumé du projet :** [Description en 3 à 5 lignes de la proposition de valeur, des utilisateurs cibles et de la nature du système.]
- **Justification du profil retenu (`Compact` / `Standard` / `Complet`) :** [Expliquer pourquoi ce niveau de granularité documentaire est proportionné à la complexité du projet.]

## 2. Règles de qualification des documents selon le profil

Chaque document de l'architecture cible `docs/` est qualifié dans l'index ci-dessous selon l'une des 4 catégories suivantes :
- **Obligatoire (`OBLIGATOIRE`)** : Document produit sous forme de fichier dédié dans le profil retenu.
- **Conditionnel (`CONDITIONNEL`)** : Document produit uniquement si le projet comporte la dimension concernée (ex. `references-analysis.md` si des références existent, `api-specification.md` s'il y a une API, `screens/` s'il y a une interface utilisateur).
- **Fusionné (`FUSIONNÉ -> [fichier hôte]`)** : En profil `Compact` (ou `Standard`), les informations essentielles de ce document sont intégrées dans une section dédiée d'un fichier principal afin d'éviter la multiplication de petits fichiers.
- **Non applicable (`N/A`)** : Document omis car sans objet pour ce projet (avec justification explicite).

## 3. Index central des documents (`docs/`)

| Domaine | Document cible | Qualification par défaut (`Compact` / `Standard` / `Complet`) | Qualification retenue pour ce projet | Fichier ou Emplacement réel | Statut | Version |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Index** | `README.md` | Obligatoire / Obligatoire / Obligatoire | `OBLIGATOIRE` | [README.md](./README.md) | `DRAFT` | 0.1 |
| **01 — Discovery** | `project-brief.md` | Obligatoire / Obligatoire / Obligatoire | `OBLIGATOIRE` | [01-discovery/project-brief.md](./01-discovery/project-brief.md) | `DRAFT` | 0.1 |
| **01 — Discovery** | `product-vision.md` | Fusionnable (`project-brief.md`) / Conditionnel / Obligatoire | `OBLIGATOIRE` \| `FUSIONNÉ` | [01-discovery/product-vision.md](./01-discovery/product-vision.md) | `DRAFT` | 0.1 |
| **01 — Discovery** | `scope.md` | Fusionnable (`requirements.md` ou `project-brief.md`) / Obligatoire / Obligatoire | `OBLIGATOIRE` \| `FUSIONNÉ` | [01-discovery/scope.md](./01-discovery/scope.md) | `DRAFT` | 0.1 |
| **02 — Research** | `research-report.md` | Conditionnel / Obligatoire / Obligatoire | `OBLIGATOIRE` \| `CONDITIONNEL` | [02-research/research-report.md](./02-research/research-report.md) | `DRAFT` | 0.1 |
| **02 — Research** | `references-analysis.md` | Conditionnel / Conditionnel / Obligatoire | `CONDITIONNEL` \| `N/A` | [02-research/references-analysis.md](./02-research/references-analysis.md) | `DRAFT` | 0.1 |
| **03 — Product Design** | `requirements.md` | Obligatoire / Obligatoire / Obligatoire | `OBLIGATOIRE` | [03-product-design/requirements.md](./03-product-design/requirements.md) | `DRAFT` | 0.1 |
| **03 — Product Design** | `personas.md` | Fusionnable (`requirements.md`) / Conditionnel / Obligatoire | `CONDITIONNEL` \| `FUSIONNÉ` | [03-product-design/personas.md](./03-product-design/personas.md) | `DRAFT` | 0.1 |
| **03 — Product Design** | `user-journeys.md` | Fusionnable (`user-flows.md`) / Conditionnel / Obligatoire | `CONDITIONNEL` \| `FUSIONNÉ` | [03-product-design/user-journeys.md](./03-product-design/user-journeys.md) | `DRAFT` | 0.1 |
| **03 — Product Design** | `user-flows.md` | Fusionnable (`requirements.md`) / Obligatoire / Obligatoire | `OBLIGATOIRE` \| `FUSIONNÉ` | [03-product-design/user-flows.md](./03-product-design/user-flows.md) | `DRAFT` | 0.1 |
| **03 — Product Design** | `sitemap.md` | Fusionnable (`requirements.md`) / Conditionnel / Obligatoire | `CONDITIONNEL` \| `FUSIONNÉ` | [03-product-design/sitemap.md](./03-product-design/sitemap.md) | `DRAFT` | 0.1 |
| **04 — UX/UI Design** | `visual-direction.md` | Fusionnable (`design-system.md`) / Conditionnel / Obligatoire | `CONDITIONNEL` \| `FUSIONNÉ` | [04-ux-ui/visual-direction.md](./04-ux-ui/visual-direction.md) | `DRAFT` | 0.1 |
| **04 — UX/UI Design** | `design-system.md` | Conditionnel (si UI) / Obligatoire (si UI) / Obligatoire | `OBLIGATOIRE` \| `N/A` | [04-ux-ui/design-system.md](./04-ux-ui/design-system.md) | `DRAFT` | 0.1 |
| **04 — UX/UI Design** | `responsive-guidelines.md` | Fusionnable (`design-system.md`) / Conditionnel / Obligatoire | `CONDITIONNEL` \| `FUSIONNÉ` | [04-ux-ui/responsive-guidelines.md](./04-ux-ui/responsive-guidelines.md) | `DRAFT` | 0.1 |
| **04 — UX/UI Design** | `screens/screen-001.md` | Conditionnel (1 fiche ou regroupé) / Obligatoire (si UI) / Obligatoire | `OBLIGATOIRE` \| `N/A` | [04-ux-ui/screens/screen-001.md](./04-ux-ui/screens/screen-001.md) | `DRAFT` | 0.1 |
| **05 — Architecture** | `system-overview.md` | Obligatoire / Obligatoire / Obligatoire | `OBLIGATOIRE` | [05-architecture/system-overview.md](./05-architecture/system-overview.md) | `DRAFT` | 0.1 |
| **05 — Architecture** | `architecture-decisions.md` | Fusionnable (`system-overview.md`) / Obligatoire / Obligatoire | `OBLIGATOIRE` \| `FUSIONNÉ` | [05-architecture/architecture-decisions.md](./05-architecture/architecture-decisions.md) | `DRAFT` | 0.1 |
| **05 — Architecture** | `data-model.md` | Fusionnable (`system-overview.md`) / Conditionnel (si DB) / Obligatoire | `CONDITIONNEL` \| `FUSIONNÉ` | [05-architecture/data-model.md](./05-architecture/data-model.md) | `DRAFT` | 0.1 |
| **05 — Architecture** | `api-specification.md` | Conditionnel (si API) / Conditionnel (si API) / Obligatoire | `CONDITIONNEL` \| `N/A` | [05-architecture/api-specification.md](./05-architecture/api-specification.md) | `DRAFT` | 0.1 |
| **05 — Architecture** | `security.md` | Fusionnable (`system-overview.md`) / Obligatoire / Obligatoire | `OBLIGATOIRE` \| `FUSIONNÉ` | [05-architecture/security.md](./05-architecture/security.md) | `DRAFT` | 0.1 |
| **06 — Quality** | `test-strategy.md` | Fusionnable (`developer-handoff.md`) / Obligatoire / Obligatoire | `OBLIGATOIRE` \| `FUSIONNÉ` | [06-quality/test-strategy.md](./06-quality/test-strategy.md) | `DRAFT` | 0.1 |
| **06 — Quality** | `acceptance-criteria.md` | Fusionnable (`requirements.md`) / Fusionnable / Obligatoire | `OBLIGATOIRE` \| `FUSIONNÉ` | [06-quality/acceptance-criteria.md](./06-quality/acceptance-criteria.md) | `DRAFT` | 0.1 |
| **06 — Quality** | `risk-register.md` | Fusionnable (`project-brief.md`) / Obligatoire / Obligatoire | `OBLIGATOIRE` \| `FUSIONNÉ` | [06-quality/risk-register.md](./06-quality/risk-register.md) | `DRAFT` | 0.1 |
| **07 — Delivery** | `roadmap.md` | Fusionnable (`developer-handoff.md`) / Obligatoire / Obligatoire | `OBLIGATOIRE` \| `FUSIONNÉ` | [07-delivery/roadmap.md](./07-delivery/roadmap.md) | `DRAFT` | 0.1 |
| **07 — Delivery** | `traceability.md` | Fusionnable (`requirements.md`) / Obligatoire / Obligatoire | `OBLIGATOIRE` \| `FUSIONNÉ` | [07-delivery/traceability.md](./07-delivery/traceability.md) | `DRAFT` | 0.1 |
| **07 — Delivery** | `developer-handoff.md` | Obligatoire / Obligatoire / Obligatoire | `OBLIGATOIRE` | [07-delivery/developer-handoff.md](./07-delivery/developer-handoff.md) | `DRAFT` | 0.1 |
| **ADR** | `adr/README.md` | Conditionnel / Obligatoire / Obligatoire | `OBLIGATOIRE` \| `CONDITIONNEL` | [adr/README.md](./adr/README.md) | `DRAFT` | 0.1 |
| **ADR** | `adr/ADR-001.md` | Obligatoire (au moins 1 ADR) / Obligatoire / Obligatoire | `OBLIGATOIRE` | [adr/ADR-001.md](./adr/ADR-001.md) | `DRAFT` | 0.1 |

*(Note à l'agent lors de la génération d'un projet réel : dans la colonne « Fichier ou Emplacement réel », ne conserver un lien Markdown actif `[...](./...)` que vers les fichiers effectivement créés pour ce projet ; pour un document `FUSIONNÉ`, pointer vers le fichier hôte ; pour un document `N/A`, écrire `N/A — [Justification]` sans lien.)*

## 4. Registre des fusions et omissions du projet
- **Documents fusionnés :**
  - [Ex. En profil Compact : `product-vision.md` est intégré à la Section 4 de `./01-discovery/project-brief.md`.]
- **Documents non applicables (`N/A`) :**
  - [Ex. `04-ux-ui/screens/` : `N/A` pour un projet d'API backend sans interface graphique.]

## 5. Journal d'évolution du profil documentaire (`Compact` → `Standard` → `Complet`)
Si le projet monte en complexité et passe à un profil supérieur :
1. Extraire la section fusionnée vers son fichier dédié standard (ex. extraire la section Modèle de données de `system-overview.md` vers `05-architecture/data-model.md`).
2. Conserver exactement tous les identifiants stables déjà attribués (`FR-xxx`, `SCR-xxx`, `ENT-xxx`, `ADR-xxx`, `AC-xxx`).
3. Remplacer la section extraite dans le fichier d'origine par un renvoi explicite (`Voir [data-model.md](./05-architecture/data-model.md)`) afin de ne jamais perdre le fil de lecture.
4. Mettre à jour le tableau de la Section 3 ci-dessus.

## 6. Légende des statuts et marqueurs décisionnels
- **Statuts documentaires** : `DRAFT` (brouillon) | `REVIEW` (à valider) | `APPROVED` (approuvé et protégé) | `SUPERSEDED` (remplacé).
- **Marqueurs décisionnels** : `[FAIT VERIFIE]` | `[HYPOTHESE]` | `[RECOMMANDATION]` | `[DECISION PROPOSEE]` | `[DECISION VALIDEE]` | `[POINT EN ATTENTE]`.
