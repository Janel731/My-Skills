# Registre des Risques (Risk Register) — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/06-quality/risk-register.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Project Brief](../01-discovery/project-brief.md) | [Architecture](../05-architecture/system-overview.md) | [Sécurité](../05-architecture/security.md) | [Roadmap](../07-delivery/roadmap.md)

## 1. Échelle d'évaluation qualitative
- **Probabilité :** `Faible` (peu probable) | `Moyenne` (plausible) | `Élevée` (fréquent ou quasi certain sans action).
- **Impact :** `Faible` (gêne mineure) | `Moyen` (dégradation partielle ou retard modéré) | `Élevé` (blocage d'un parcours clé, dépassement fort) | `Critique` (perte de données, faille de sécurité, arrêt du service, blocage légal).
- **Niveau de risque :** Croisement Probabilité x Impact (`Faible`, `Modéré`, `Élevé`, `Critique`). *Ne pas utiliser de pourcentages fictifs non fondés.*

## 2. Tableau des Risques identifiés (`RISK-xxx`)
| ID | Catégorie (Produit / UX / Tech / Sécu / Tiers / Coût) | Scénario de risque & Cause racine | Probabilité | Impact | Niveau initial | Stratégie de prévention & Plan de secours (Mitigation) | Éléments liés (`FR` / `SCR` / `ADR`) | Responsable | Risque résiduel |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `RISK-001` | Produit / Périmètre | Dérive du périmètre MVP retardant la mise en ligne | Moyenne | Élevé | **Élevé** | Verrouillage strict de `scope.md` et report systématique des demandes `Could` en V1.1 | `scope.md` | Porteur de projet | Faible |
| `RISK-002` | UX / Adoption | Abandon lors de la première utilisation faute de données initiales | Moyenne | Élevé | **Élevé** | Conception soignée de l'état Vide avec guidage immédiat sur `SCR-001` / `SCR-002` | `SCR-001`, `UF-001` | Product Designer | Faible |
| `RISK-003` | Technique / Tiers | Indisponibilité ou latence d'une API externe critique | Moyenne | Élevé | **Élevé** | Timeout strict, retry avec backoff et affichage d'un état d'erreur dégradé non bloquant | `API-001`, `ADR-001` | Lead Dev | Modéré |
| `RISK-004` | Sécurité | Accès croisé aux données d'un autre compte (IDOR) | Faible | Critique | **Élevé** | Filtrage serveur systématique par propriétaire et test automatisé `TEST-006` | `security.md` | Lead Dev | Faible |

## 3. Hypothèses critiques sous surveillance
- [Lister ici les hypothèses `[HYPOTHESE]` de `project-brief.md` qui se transformeraient en risques majeurs si elles s'avéraient invalides.]
