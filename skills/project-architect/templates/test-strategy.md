# Stratégie de Tests & Plan d'Assurance Qualité — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/06-quality/test-strategy.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Exigences](../03-product-design/requirements.md) | [Critères d'Acceptation](./acceptance-criteria.md) | [Sécurité](../05-architecture/security.md) | [Traçabilité](../07-delivery/traceability.md)

> **Note d'intégrité :** Ce document définit la **stratégie et les scénarios de tests planifiés (`TEST-xxx`)** pour valider le produit. Aucun test listé ici ne doit être déclaré comme « réussi » tant qu'il n'a pas été exécuté sur le code réel.

## 1. Niveaux de tests et responsabilités
| Niveau de test | Catégorie | Périmètre vérifié | Approche recommandée | Exécution |
| :--- | :--- | :--- | :--- | :--- |
| **1. Tests Unitaires** | `Unit` | Règles métier (`BR-xxx`), calculs, validations pures | Runner unitaire standard de la stack | À chaque commit (CI) |
| **2. Tests UI & États** | `UI` | Composants (`COMP-xxx`) et états qualifiés `Applicable` des écrans (`SCR-xxx`) | Tests de composants + revue visuelle | À chaque PR (CI) |
| **3. Tests d'Intégration & API** | `Integration` | Contrats `API-xxx`, base de données `ENT-xxx`, permissions | Base de test isolée | À chaque PR (CI) |
| **4. Tests End-to-End (E2E)** | `E2E` | Parcours critiques (`UF-xxx`) de bout en bout | Navigateur headless / appareil réel | Avant merge / release |
| **5. Tests d'Accessibilité** | `A11Y` | Navigation clavier, focus, contrastes WCAG AA, ARIA | Audit axe-core + test manuel clavier | Avant release |
| **6. Tests de Sécurité** | `Security` | Contrôles d'accès croisés (IDOR), auth, injections, quotas | Suite dédiée + audit dépendances | Avant release |
| **7. Tests de Performance** | `Performance` | Temps de réponse API (`p95`), chargement initial (`LCP`) | Tir de charge léger & profilage | En staging |

## 2. Catalogue des scénarios de tests critiques (`TEST-xxx`)
| ID Test | Catégorie | Cible (`FR` / `NFR` / `BR` / `SCR` / `API`) | Critères couverts (`AC-xxx`) | Scénario vérifié | Résultat attendu |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `TEST-001` | `Unit` | `BR-001`, `FR-001` | `AC-002` | Vérification de la règle métier `BR-001` aux valeurs limites | Calcul exact et rejet des valeurs hors bornes |
| `TEST-002` | `UI` | `SCR-001` | `AC-001`, `AC-003` | Vérification de l'état Initial et des états qualifiés `Applicable` dans `screen-001.md` | Affichage conforme sans perte de saisie ni saut de layout |
| `TEST-003` | `Integration` | `API-001`, `ENT-001` | `AC-001`, `AC-002` | Appel nominal et appel avec données invalides (`422`) | Persistance conforme et format d'erreur standardisé |
| `TEST-004` | `E2E` | `UF-001`, `FR-001` | `AC-001` | Parcours complet cœur de valeur du MVP | Accomplissement de bout en bout sans erreur |
| `TEST-005` | `A11Y` | `SCR-001`, `NFR-002` | `AC-005` | Parcours 100 % au clavier (`Tab`, `Enter`, `Escape`) et contrastes | Focus visible continu et 0 violation critique WCAG AA |
| `TEST-006` | `Security` | `API-001`, `NFR-003` | `AC-006`, `AC-007` | Tentative d'accès par l'utilisateur A aux ressources de l'utilisateur B | Rejet `403 Forbidden` ou `404` et aucune fuite de données |
| `TEST-007` | `Performance` | `API-001`, `NFR-001` | `AC-010` | Mesure de latence `p95` sous charge nominale | Temps de réponse conforme au seuil `NFR-001` |

## 3. Jeux de données de test et environnements
- **Données de seed reproductibles :** Cas nominal, compte vierge (pour tester l'état Vide lorsqu'il est applicable), compte avec volume élevé (pour tester la pagination), compte à droits restreints (pour tester l'état Désactivé / Lecture seule lorsqu'il est applicable).
- **Isolation des services tiers :** Utilisation des modes Sandbox (paiement, e-mail) ou de doublures de test déterministes.

## 4. Critères de sortie qualité (Go / No-Go Release)
- [ ] Tous les scénarios `TEST-xxx` liés aux exigences `Must (MVP)` passent avec succès.
- [ ] Tous les états qualifiés `Applicable` de chaque écran du MVP ont été vérifiés sur Desktop et Mobile.
- [ ] Aucun bug bloquant ou critique (perte de données, faille de sécurité, impasse UX) n'est actif.
