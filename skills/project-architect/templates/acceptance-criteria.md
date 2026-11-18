# Référentiel Consolidé des Critères d'Acceptation (`AC-xxx`) — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/06-quality/acceptance-criteria.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Exigences](../03-product-design/requirements.md) | [Écrans](../04-ux-ui/screens/screen-001.md) | [Stratégie de Tests](./test-strategy.md) | [Traçabilité](../07-delivery/traceability.md)

## 1. Critères d'acceptation Fonctionnels et Métier (`FR-xxx` & `BR-xxx`)

### `FR-001` — [Titre de l'exigence]
- **`AC-001` (Scénario nominal) :**
  - **Given** [contexte et état initial précis]
  - **When** [action déclenchée par l'acteur `ACT-001`]
  - **Then** [résultat observable exact dans l'interface `SCR-xxx` et/ou la persistance `ENT-xxx`]
- **`AC-002` (Validation et respect de `BR-001`) :**
  - **Given** [donnée violant `BR-001`]
  - **When** [soumission sur `SCR-xxx` / appel `API-xxx`]
  - **Then** [rejet propre avec message explicite et conservation de la saisie]

## 2. Critères d'acceptation UX/UI et Écrans transverses (`SCR-xxx`)
- **`AC-003` (Couverture des états applicables par écran) :** Pour chaque écran du MVP (`SCR-001`...), tous les états qualifiés `Applicable` parmi la grille de référence des 6 états (Initial, Chargement, Vide, Erreur, Succès, Désactivé) sont implémentés conformément à sa fiche de spécification (sans saut de layout au chargement, ni perte de saisie en cas d'erreur).
- **`AC-004` (Responsive multi-écrans) :** Sur une largeur de `320px` à `1440px+`, aucun écran ne présente de débordement horizontal involontaire, de texte tronqué illisible ou de cible tactile inférieure à `44x44px` sur mobile.
- **`AC-005` (Accessibilité WCAG 2.1 AA) :** Toute action réalisable à la souris est réalisable exclusivement au clavier avec un indicateur `:focus-visible` net, et les ratios de contraste respectent [../04-ux-ui/design-system.md](../04-ux-ui/design-system.md).

## 3. Critères d'acceptation Techniques et Sécurité (`NFR-xxx`)
- **`AC-006` (Sécurité des accès) :** Aucune route protégée (`API-xxx`) n'est accessible sans session valide (`401`) ni par un rôle non autorisé (`403`).
- **`AC-007` (Intégrité des erreurs) :** Aucune erreur serveur ne divulgue de trace technique interne, de requête SQL ou de secret à l'utilisateur final.
