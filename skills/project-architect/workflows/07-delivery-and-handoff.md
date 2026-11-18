# Workflow 07 — Delivery, Traçabilité & Developer Handoff

## 1. Objectif de la phase
Finaliser l'ensemble de l'arborescence documentaire `docs/` selon le profil retenu (`Compact`, `Standard` ou `Complet`), établir la matrice de traçabilité relationnelle souple, structurer la feuille de route d'implémentation par lots incrémentaux et livrer un dossier de passation (`developer-handoff.md`) permettant à une équipe ou à un agent de développement de construire le produit sans ambiguïté.

## 2. Ressources internes du skill à mobiliser
- **Références** : `references/documentation-standards.md`, `references/devops-and-deployment.md`
- **Templates** : `templates/roadmap.md`, `templates/traceability.md`, `templates/developer-handoff.md`, `templates/docs-readme.md`

## 3. Entrées
- L'ensemble des livrables `docs/01-discovery/` à `docs/06-quality/` et `docs/adr/` révisés lors de la Phase 6.

## 4. Déroulement opérationnel

1. **Construction de la Matrice de Traçabilité Relationnelle (`docs/07-delivery/traceability.md`)** :
   - Relie chaque exigence `FR-xxx` et `NFR-xxx` à ses artefacts pertinents (multiples, optionnels ou `N/A` justifiés) parmi :
     - Règles métier (`BR-xxx`) et parcours (`UJ-xxx`, `UF-xxx`).
     - Écrans (`SCR-xxx`) et composants UI (`COMP-xxx`).
     - Contrats d'API (`API-xxx`), entités de données (`ENT-xxx`) et décisions architecturales (`ADR-xxx`).
     - Critères d'acceptation (`AC-xxx`) et tests (`TEST-xxx`).
   - N'impose aucune relation artificielle : lorsqu'une dimension est `N/A` (ex. traitement interne sans écran ou écran statique sans API), indique `N/A` avec sa justification courte.
   - Adapte la granularité au profil documentaire (*Compact*, *Standard*, *Complet*).
2. **Planification de la Feuille de Route par lots (`docs/07-delivery/roadmap.md`)** :
   - Découpe la réalisation en lots incrémentaux logiques et testables (ex. Lot 0 : Fondations, CI & Design System tokens/primitives ; Lot 1 : Authentification, modèle de données cœur & navigation ; Lot 2 : Parcours cœur de valeur MVP ; Lot 3 : Cas limites, durcissement sécurité & tests E2E/a11y).
   - Pour chaque lot, précise l'objectif, les livrables (`FR-xxx`, `SCR-xxx`, `API-xxx`), les dépendances et le critère de sortie (`AC-xxx`, `TEST-xxx`).
   - N'invente jamais de dates calendaires fixes sans connaître la vélocité de l'équipe : donne une estimation relative ou en fourchette assortie de ses hypothèses explicites.
3. **Rédaction du Dossier de Passation (`docs/07-delivery/developer-handoff.md`)** :
   - Produis le guide opérationnel de référence pour les développeurs et designers : synthèse du périmètre approuvé, stack verrouillée, nature des livrables UX/UI fournis (spécifications textuelles vs livrables visuels), conventions d'architecture et de Design System, ordre d'implémentation, variables d'environnement requises, règles de sécurité et d'accessibilité, Definition of Done et liste des points restant en attente (`[POINT EN ATTENTE]`).
4. **Contrôle final et mise à jour de `docs/README.md` et `docs/adr/README.md`** :
   - Vérifie que chaque document est qualifié (`OBLIGATOIRE`, `CONDITIONNEL`, `FUSIONNÉ` ou `N/A`) et que tous les liens Markdown relatifs entre fichiers `docs/` réellement créés sont valides.
   - Mets à jour `docs/README.md` et `docs/adr/README.md` avec les statuts (`DRAFT`, `REVIEW`, `APPROVED`, `SUPERSEDED`) et versions à jour.

## 5. Definition of Ready for Development (Checklist finale avant passation)
Le blueprint est prêt pour le développement lorsque :
- [ ] Le problème, les personas et le périmètre MVP sont validés (`01-discovery/`, `03-product-design/`).
- [ ] La direction artistique, le Design System et les fiches des écrans clés avec leurs états applicables sont documentés (`04-ux-ui/`).
- [ ] L'architecture (`system-overview.md`), la synthèse des décisions (`architecture-decisions.md`), le modèle de données, les contrats d'API, la sécurité et les ADR (`adr/README.md`, `adr/ADR-NNN.md`) sont cohérents.
- [ ] La stratégie de tests (`TEST-xxx`), les critères `AC-xxx` (Given/When/Then) et le registre des risques (`RISK-xxx`) sont établis (`06-quality/`).
- [ ] La matrice de traçabilité relationnelle, la roadmap par lots et le developer handoff sont complets (`07-delivery/`).
- [ ] Les questions bloquantes sont résolues ou isolées avec une consigne claire dans `developer-handoff.md`.
