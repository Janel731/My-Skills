# Workflow 03 — Product Design (Exigences, UX & Architecture de l'Information)

## 1. Objectif de la phase
Traduire la vision et les enseignements de la recherche en une conception produit et UX complète : utilisateurs et personas (`PER-xxx`), parcours macro (`UJ-xxx`), flux opérationnels détaillés (`UF-xxx`), architecture de l'information et sitemap (`SCR-xxx`), exigences fonctionnelles priorisées (`FR-xxx`), règles métier (`BR-xxx`), exigences non fonctionnelles (`NFR-xxx`) et critères d'acceptation (`AC-xxx`).

## 2. Ressources internes du skill à mobiliser
- **Références** : `references/product-design-and-ux.md`, `references/functional-specification.md`, `references/documentation-standards.md`
- **Templates** : `templates/requirements.md`, `templates/personas.md`, `templates/user-journeys.md`, `templates/user-flows.md`, `templates/sitemap.md`

## 3. Entrées
- Livrables de `docs/01-discovery/` et `docs/02-research/`.

## 4. Déroulement opérationnel

1. **Modélisation des utilisateurs et Personas (`ACT-xxx`, `PER-xxx`)** :
   - Définis les acteurs, leurs rôles et leurs permissions.
   - Crée les fiches Personas (`PER-001`...) pertinentes centrées sur le contexte d'usage réel, les objectifs, les points de douleur et les besoins d'accessibilité (fusionnables dans `requirements.md` en profil `Compact`).
2. **Conception des User Journeys (`UJ-xxx`) et User Flows (`UF-xxx`)** :
   - Décris les parcours macro de bout en bout (`docs/03-product-design/user-journeys.md`).
   - Modélise les flux opérationnels précis (`docs/03-product-design/user-flows.md`) avec diagrammes Mermaid incluant parcours nominal, parcours alternatifs, erreurs de validation, pertes réseau et cas limites.
3. **Architecture de l'information et Sitemap** :
   - Organise la hiérarchie des contenus et des fonctionnalités selon le modèle mental utilisateur.
   - Établis le Sitemap (`docs/03-product-design/sitemap.md`) attribuant à chaque écran ou vue son identifiant stable (`SCR-001`, `SCR-002`...) et son modèle de navigation (ou marque `N/A` pour un projet purement backend/API).
4. **Spécification des exigences (`FR-xxx`, `BR-xxx`, `NFR-xxx`) et critères (`AC-xxx`)** :
   - Rédige `docs/03-product-design/requirements.md` (qui peut intégrer `scope.md` en profil `Compact`).
   - Décompose chaque besoin en exigences atomiques (`FR-001`...), priorisées en **MVP (Must/Should)**, **Après MVP (Could)** et **Hors périmètre (Won't now)**.
   - Associe à chaque fonctionnalité ses règles métier (`BR-001`...) et ses critères d'acceptation testables (`AC-001`...) en **Given / When / Then**.
   - Définit les seuils mesurables des exigences non fonctionnelles (`NFR-001`...), y compris l'accessibilité WCAG et la performance perçue.

## 5. Arbitrages d'autonomie
- **Tu décides seul** : la découpe granulaire des User Flows, la gestion des cas d'erreur UX standards, la structuration atomique des exigences `FR-xxx` et la rédaction des critères `AC-xxx` en Given/When/Then.
- **Tu fais valider par l'utilisateur** : la liste finale des fonctionnalités incluses dans le MVP vs reportées après le MVP, l'organisation majeure de la navigation (Sitemap) et les règles métier critiques.

## 6. Critères de sortie (Passage à la Phase 4)
- [ ] Chaque acteur et persona pertinent est documenté.
- [ ] Les parcours nominaux, alternatifs et cas d'erreur sont couverts sans impasse.
- [ ] Le Sitemap recense tous les écrans (`SCR-001`...) nécessaires au MVP (si le projet comporte une interface).
- [ ] Toutes les exigences du MVP possèdent un identifiant stable (`FR-xxx`, `BR-xxx`, `NFR-xxx`) et des critères d'acceptation vérifiables (`AC-xxx`).
