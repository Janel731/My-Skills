# Roadmap de Livraison par Lots — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/07-delivery/roadmap.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Périmètre](../01-discovery/scope.md) | [Traçabilité](./traceability.md) | [Developer Handoff](./developer-handoff.md)

## 1. Stratégie de découpage incrémental
La réalisation est organisée en **lots verticaux cohérents et vérifiables**. Chaque lot produit un incrément fonctionnel et/ou visuel testable, plutôt que de développer tout le backend puis tout le frontend en silo.

## 2. Découpage détaillé des Lots du MVP
| Lot | Objectif du lot | Livrables UX/UI (`SCR-xxx`, `COMP-xxx`) | Livrables Tech (`MOD-xxx`, `ENT-xxx`, `API-xxx`) | Exigences couvertes (`FR-xxx`, `NFR-xxx`) | Dépendances | Critère de sortie (`AC-xxx`, `TEST-xxx`) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Lot 0 — Fondations & Design System** | Socle technique, CI/CD et tokens/composants de base | Tokens `design-system.md`, `COMP-001` à `COMP-005` | Structure repo, DB, config env, CI | `NFR-001` à `NFR-003` | Aucune | Application démarre en local/staging et catalogue UI validé |
| **Lot 1 — Accès, Navigation & Modèle cœur** | Authentification, layout responsive et premier écran | `SCR-001` (états applicables), Navigation globale | `MOD-001`, `ENT-001`, Auth | `FR-001` | Lot 0 | Connexion, déconnexion et redirections testées (`TEST-006`) |
| **Lot 2 — Boucle de valeur principale (Core Loop)** | Parcours métier central de bout en bout | `SCR-002` (états applicables) | `MOD-002`, `ENT-002`, `API-001`, `API-002` | `FR-002`, `FR-003` | Lot 1 | Parcours `UF-001` complet validé (`TEST-004`) |
| **Lot 3 — Cas limites, Qualité & Pré-production** | Durcissement sécurité, accessibilité, états d'erreur et mise en ligne | Polissage responsive & accessibilité clavier | Sauvegardes, monitoring, rate limiting | Toutes exigences MVP | Lot 2 | 100 % des critères `acceptance-criteria.md` validés |

## 3. Jalons de validation (Milestones)
| Jalon | Lot associé | Résultat démontrable attendu | Validation requise |
| :--- | :--- | :--- | :--- |
| **M1 — Socle & UI Kit prêt** | Fin Lot 0 | Thème, typographie et composants de base visibles | Revue Design System |
| **M2 — Parcours cœur fonctionnel** | Fin Lot 2 | Démonstration du parcours principal `UF-001` avec vraies données | Recette fonctionnelle MVP |
| **M3 — Go-Live MVP** | Fin Lot 3 | Produit déployé, sécurisé, sauvegardé et testé | Validation de mise en production |

## 4. Estimations d'effort et Hypothèses de planification
- **Hypothèses de capacité (`[HYPOTHESE]`) :** [Taille de l'équipe, disponibilité hebdomadaire, maîtrise de la stack retenue.]
- **Fourchette d'effort relatif par lot :** [Ex. Lot 0 (15 %), Lot 1 (20 %), Lot 2 (45 %), Lot 3 (20 %) — avec niveau de confiance et facteurs de variation.]

## 5. Évolutions Post-MVP (Backlog V1.1 / V2)
- **V1.1 (Améliorations rapides après retours utilisateurs) :** [Références `FR-xxx` classées `Should` / `Could`.]
- **V2 (Extensions majeures) :** [Éléments reportés dans `scope.md`.]
