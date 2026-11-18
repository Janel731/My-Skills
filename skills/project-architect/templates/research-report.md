# Rapport d'Étude de l'Existant et de Recherche Technique — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/02-research/research-report.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Project Brief](../01-discovery/project-brief.md) | [Analyse des Références](./references-analysis.md) | [Décisions d'Architecture](../05-architecture/architecture-decisions.md)

## 1. Périmètre et conditions de la recherche
- **Objectifs de l'étude :** [Ce que cette recherche devait vérifier ou comparer.]
- **Outils de recherche disponibles :** [Recherche web en direct / Analyse des sources fournies / Recherche hors ligne avec éléments à vérifier.]
- **Date de vérification des informations :** [YYYY-MM-DD]

## 2. Analyse des solutions et produits existants (Benchmark)
| ID | Solution / Produit | Type (SaaS / OSS) | Forces observées | Limites & Irritants utilisateurs | Enseignement pour notre projet | Source & URL |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `REF-SOL-01` | [Nom] | [Type] | [Points forts] | [Points faibles] | [Ce qu'on retient ou évite] | [Lien vérifié] |

## 3. Audit des dépôts Open Source et bibliothèques candidates
| Dépôt / Librairie | URL canonique | Licence vérifiée | Stack & Langage | Activité & Dernière release | Qualité doc & tests | Risques / Limites | Verdict |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| [Nom] | [URL ou `Non vérifié`] | [`MIT` / `Apache-2.0` / `AGPLv3` / `Non vérifié`] | [Stack] | [Date vérifiée] | [Évaluation] | [Dépendances, lock-in...] | Retenu / Écarté |

## 4. Comparaison des options technologiques structurantes
### Sujet de comparaison : [Ex. Stack Backend / Base de données / Moteur de recherche / Auth]
| Critère | Option A (Recommandée) | Option B (Alternative) | Option C |
| :--- | :--- | :--- | :--- |
| **Adéquation fonctionnelle** | [...] | [...] | [...] |
| **Complexité d'intégration & Maintenance** | [...] | [...] | [...] |
| **Performance & Évolutivité** | [...] | [...] | [...] |
| **Sécurité & Conformité** | [...] | [...] | [...] |
| **Coût total (Initial + Exploitation)** | [...] | [...] | [...] |
| **Licence & Portabilité** | [...] | [...] | [...] |

## 5. Synthèse : Arbitrage Build vs Buy vs Reuse
- **À réutiliser tel quel (Bibliothèques / Services managés) :** [...]
- **À adapter ou configurer :** [...]
- **À concevoir et développer sur mesure (Cœur différenciant) :** [...]
- **Risques de dépendance ou de licence identifiés (`RISK-xxx`) :** [...]

## 6. Sources consultées
1. `[FAIT VERIFIE]` [Titre de la source] — [Organisation/Auteur] — [URL exacte] (Consulté le [YYYY-MM-DD]).
