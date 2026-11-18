# Changelog — Project Architect & Product Designer

Toutes les modifications notables apportées au skill `project-architect` sont documentées dans ce fichier.

## [2.1.0] — 2026-11-18 — Mise à jour corrective et de consolidation (V2 → V2.1)

### 1. Fichiers ajoutés (5 nouveaux fichiers)
- `templates/adr-readme.md` : Nouveau template dédié à la génération de `docs/adr/README.md` (rôle des ADR, convention de nommage `ADR-NNN.md`, règles de création/modification/remplacement `SUPERSEDED`, index des décisions et statuts).
- `templates/architecture-decisions.md` : Nouveau template dédié à la génération de `docs/05-architecture/architecture-decisions.md`, distinct de `system-overview.md` (tableau de synthèse avec identifiant, sujet, décision, justification synthétique, statut et lien vers l'ADR détaillé, sans duplication inutile).
- `CHANGELOG.md` : Journal détaillé des modifications entre la V2 et la V2.1.
- `AUDIT-REPORT.md` : Rapport complet des vérifications structurelles, méthodologiques, documentaires et des limites de validation de la V2.1.
- `MIGRATION-GUIDE.md` : Guide de migration expliquant les changements de la V2.1, leurs conséquences pour les utilisateurs de la V2 et la procédure de mise à jour.

### 2. Fichiers modifiés (25 fichiers mis à jour)
- **Racine du skill** :
  - `SKILL.md` : Mise à jour vers la V2.1 (intégration des 2 nouveaux templates dans la table de routage de la Phase 5 ; règle d'examen des 6 états d'écran en `Applicable` / `Non applicable (N/A + justification)` / `À déterminer` ; distinction explicite entre spécifications d'interface textuelles et livrables visuels avec les 6 règles obligatoires ; opérationnalisation des 3 profils `Compact`, `Standard`, `Complet` et de la règle d'évolution de profil ; traçabilité relationnelle souple et harmonisation des identifiants `FR-001` et `AC-001`).
  - `README.md` : Clarification de la portabilité et de l'installation (distinction entre le standard Agent Skills, le contenu méthodologique indépendant de la plateforme et les modalités propres à Claude, ChatGPT et aux environnements d'agents ; avertissement explicite qu'une archive ZIP n'est pas universellement reconnue sans extraction ou Code Interpreter ; mise à jour de l'arborescence à 54 fichiers).
- **Références (`references/`)** :
  - `references/documentation-standards.md` : Table de correspondance 1-pour-1 entre les 28 templates et leurs chemins de destination dans `docs/` ; définition opérationnelle des 3 profils (`Compact`, `Standard`, `Complet`) ; qualification des documents (`OBLIGATOIRE`, `CONDITIONNEL`, `FUSIONNÉ`, `N/A`) ; règles de fusion autorisées ; procédure d'évolution `Compact → Standard → Complet` sans rupture de liens ; traçabilité relationnelle non linéaire et nomenclature `FR-001`, `AC-001`, `TEST-001`.
  - `references/screen-specifications.md` : Ajout de la Section 1 sur la distinction entre *Spécification d'interface* et *Livrable visuel* (et ses 6 règles impératives) ; refonte de la Section 4 sur la grille des 6 états des écrans (examen systématique avec qualification `Applicable` / `N/A` justifié / `À déterminer` et exemples concrets écran statique vs formulaire vs liste dynamique).
  - `references/ui-design-and-design-system.md` : Ajout de la Section 7 sur la distinction entre spécifications UX/UI textuelles et livrables visuels.
  - `references/functional-specification.md` : Harmonisation des identifiants `FR-001` (exigence fonctionnelle) et `AC-001` (critère d'acceptation) et alignement avec la traçabilité souple.
  - `references/testing-strategy.md` : Harmonisation des identifiants `TEST-001` et `AC-001`, et alignement des tests UI sur les seuls états qualifiés `Applicable` de chaque écran.
  - `references/product-design-and-ux.md`, `references/software-architecture.md`, `references/database-design.md`, `references/api-design.md` : Harmonisation des références `FR-xxx`.
- **Workflows (`workflows/`)** :
  - `workflows/03-product-design.md` : Adoption de `FR-xxx` et `AC-xxx` et règles de fusion en profil `Compact`.
  - `workflows/04-ux-ui-design.md` : Intégration de la distinction spécification textuelle vs livrable visuel et de la qualification `Applicable` / `N/A` / `À déterminer` des 6 états d'écran.
  - `workflows/05-technical-architecture.md` : Intégration de `templates/architecture-decisions.md` (`docs/05-architecture/architecture-decisions.md`) et `templates/adr-readme.md` (`docs/adr/README.md`) distincts de `system-overview.md`.
  - `workflows/06-critical-review.md` : Contrôle de cohérence mis à jour sur l'examen proportionné des 6 états, l'honnêteté des livrables visuels et les identifiants `FR-xxx` / `AC-xxx` / `TEST-xxx`.
  - `workflows/07-delivery-and-handoff.md` : Mise à jour de l'étape de traçabilité vers le modèle relationnel souple avec justification des `N/A`.
- **Templates (`templates/`)** :
  - `templates/technical-architecture.md` : Recentré exclusivement sur `docs/05-architecture/system-overview.md` (vue d'ensemble, contexte et frontières, composants `MOD-xxx`, responsabilités, communications inter-composants, dépendances internes/externes, diagrammes Mermaid, contraintes techniques et renvoi vers `architecture-decisions.md` et `adr/`).
  - `templates/screen-specification.md` : Ajout du champ *Type de livrable*, de la grille de qualification des 6 états (`Applicable` / `N/A` / `À déterminer`), de la section *Livrables visuels associés* et des identifiants `FR-xxx` / `AC-xxx`.
  - `templates/docs-readme.md` : Refonte complète avec qualification par profil (`OBLIGATOIRE`, `CONDITIONNEL`, `FUSIONNÉ`, `N/A`), registre des fusions et journal d'évolution de profil (`Compact → Standard → Complet`).
  - `templates/traceability.md` : Refonte complète vers une matrice relationnelle souple incluant identifiant (`FR-xxx`/`NFR-xxx`), description, relations pertinentes, justification des relations absentes (`N/A`), statut de couverture et références documentaires.
  - `templates/requirements.md`, `templates/acceptance-criteria.md`, `templates/test-strategy.md`, `templates/developer-handoff.md`, `templates/roadmap.md`, `templates/scope.md`, `templates/personas.md`, `templates/user-journeys.md`, `templates/user-flows.md`, `templates/sitemap.md`, `templates/api-specification.md`, `templates/security.md`, `templates/risk-register.md`, `templates/adr.md` : Harmonisation des identifiants `FR-001`, `AC-001`, `TEST-001` et alignement avec les règles V2.1.

### 3. Fichiers conservés à l'identique (24 fichiers de la V2 déjà conformes)
- `references/project-discovery.md`, `references/research-methodology.md`, `references/visual-references-analysis.md`, `references/security-guidelines.md`, `references/devops-and-deployment.md`.
- `workflows/01-discovery.md`, `workflows/02-research.md`.
- `templates/project-brief.md`, `templates/product-vision.md`, `templates/research-report.md`, `templates/references-analysis.md`, `templates/visual-direction.md`, `templates/design-system.md`, `templates/responsive-guidelines.md`, `templates/database-schema.md`.
