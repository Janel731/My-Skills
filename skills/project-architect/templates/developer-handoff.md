# Developer & Designer Handoff (Dossier de Passation) — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/07-delivery/developer-handoff.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Index central](../README.md) | [Roadmap](./roadmap.md) | [Traçabilité](./traceability.md) | [Design System](../04-ux-ui/design-system.md) | [Vue d'ensemble du système](../05-architecture/system-overview.md) | [Décisions d'architecture](../05-architecture/architecture-decisions.md)

## 1. Mission et objectif du produit
[Synthèse directe de ce qui doit être construit, pour qui, et quel est le résultat attendu du MVP.]

## 2. Périmètre approuvé du MVP
- **Inclus dans cette livraison (`Must` / `Should` retenus) :** [Références `FR-001` à `FR-0NN` — voir `../01-discovery/scope.md`.]
- **Strictement exclu de cette livraison (Ne pas développer) :** [Exclusions explicites pour éviter toute sur-ingénierie.]

## 3. Stack technologique verrouillée
| Couche | Technologie | Version / Contrainte | Justification & ADR |
| :--- | :--- | :--- | :--- |
| **Frontend & UI** | [Framework + approche CSS/Tokens] | [Version] | [ADR-001](../adr/ADR-001.md) |
| **Backend & API** | [Framework / Runtime] | [Version] | [ADR-002](../adr/ADR-002.md) |
| **Base de données** | [SGBD] | [Version] | [ADR-003](../adr/ADR-003.md) |
| **Infrastructure & CI** | [Hébergeur / Pipeline] | [Contrainte] | [ADR-004](../adr/ADR-004.md) |

## 4. Structure cible du dépôt de code
```text
project-repo/
├── README.md
├── docs/                        # Ce dossier de blueprint complet (vérité de référence)
├── src/                         # Code source applicatif à implémenter selon les lots
└── tests/                       # Suites de tests (unitaires, intégration, E2E, a11y)
```

## 5. Instructions d'implémentation UX/UI et Design System
1. **Nature des livrables UX/UI fournis :** Vérifier dans chaque fiche `../04-ux-ui/screens/` s'il s'agit d'une **spécification textuelle d'interface** (avec wireframe ASCII / diagrammes) ou si des **livrables visuels graphiques** (maquettes, captures, prototypes) sont joints.
2. **Implémenter d'abord les Design Tokens** définis dans [../04-ux-ui/design-system.md](../04-ux-ui/design-system.md) (couleurs sémantiques, typographie, échelle d'espacement, rayons, ombres, focus ring).
3. **Construire les composants réutilisables (`COMP-001`...)** avec leurs variantes et états interactifs avant d'assembler les pages.
4. **Pour chaque écran (`SCR-001`...)**, suivre sa fiche dans `../04-ux-ui/screens/` :
   - Implémenter tous les états qualifiés **`Applicable`** parmi la grille des 6 états (Initial, Chargement, Vide, Erreur sans perte de saisie, Succès, Désactivé/Lecture seule), sans créer artificiellement de code pour les états marqués `N/A`.
   - Respecter les règles de transformation mobile/tablette/desktop de [../04-ux-ui/responsive-guidelines.md](../04-ux-ui/responsive-guidelines.md).
   - Respecter la navigation clavier, les attributs ARIA et `@media (prefers-reduced-motion: reduce)`.

## 6. Instructions d'implémentation Backend, Données et API
1. **Schéma et migrations :** Implémenter les entités `ENT-xxx`, contraintes et index décrits dans [../05-architecture/data-model.md](../05-architecture/data-model.md).
2. **Contrats d'API :** Respecter les routes, schémas de validation, codes HTTP et format d'erreur standardisé de [../05-architecture/api-specification.md](../05-architecture/api-specification.md).
3. **Sécurité :** Appliquer tous les contrôles d'authentification, d'autorisation par ressource et de gestion des secrets de [../05-architecture/security.md](../05-architecture/security.md).

## 7. Ordre d'exécution recommandé (Lot par Lot)
Suivre l'ordre séquentiel défini dans [./roadmap.md](./roadmap.md) :
1. **Lot 0 :** Initialisation, variables d'environnement, base de données et tokens/composants UI (`COMP-xxx`).
2. **Lot 1 :** Authentification, layout de navigation et écran `SCR-001`.
3. **Lot 2 :** Flux métier principal (`UF-001`, écrans `SCR-002`+, endpoints `API-xxx` et règles `BR-xxx`).
4. **Lot 3 :** Cas limites, tests E2E/sécurité/accessibilité et préparation du déploiement.

## 8. Configuration et Variables d'environnement requises (`.env.example`)
| Variable | Rôle | Exemple de format (non secret) | Obligatoire en Prod |
| :--- | :--- | :--- | :--- |
| `DATABASE_URL` | Connexion base de données | `postgresql://user:pass@localhost:5432/db` | Oui |
| `APP_SECRET` | Signature des sessions / jetons | `[Générer 32+ octets aléatoires]` | Oui |

## 9. Definition of Done (Critères de fin de développement)
- [ ] Toutes les exigences `Must (MVP)` (`FR-xxx`, `NFR-xxx`) de `requirements.md` sont implémentées.
- [ ] Tous les écrans `SCR-xxx` du MVP gèrent leurs états qualifiés `Applicable` et sont responsive de `320px` à `1440px+`.
- [ ] Les critères d'acceptation (`AC-xxx`) de `../06-quality/acceptance-criteria.md` sont vérifiés.
- [ ] Les tests (`TEST-xxx`) requis dans `../06-quality/test-strategy.md` sont écrits et passent en CI.
- [ ] Les permissions et l'isolation des données entre utilisateurs sont testées.
- [ ] Aucun secret, clé privée ou donnée sensible n'est présent dans le dépôt Git.
- [ ] La documentation de démarrage local et de déploiement est à jour.

## 10. Décisions verrouillées et Points restant en attente
- **Décisions verrouillées (`[DECISION VALIDEE]`) :** Ne pas remettre en cause les choix documentés dans [../05-architecture/architecture-decisions.md](../05-architecture/architecture-decisions.md) et [../adr/README.md](../adr/README.md) sans créer un nouvel ADR et faire valider l'impact.
- **Points en attente (`[POINT EN ATTENTE]`) à confirmer avant ou pendant le Lot concerné :**
  - [Lister ici toute clé d'API tierce, contenu éditorial final ou validation juridique restant à fournir par le porteur de projet.]
