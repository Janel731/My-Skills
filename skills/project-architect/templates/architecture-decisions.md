# Synthèse des Décisions Architecturales — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/05-architecture/architecture-decisions.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Vue d'ensemble du système](./system-overview.md) | [Registre des ADR](../adr/README.md) | [Modèle de données](./data-model.md) | [Sécurité](./security.md) | [Traçabilité](../07-delivery/traceability.md)

## 1. Objectif de ce document

Ce document fournit une **vue synthétique et opérationnelle des décisions architecturales et technologiques** qui structurent le système. Il est distinct de la [vue d'ensemble du système](./system-overview.md) (qui décrit la topologie, les composants et leurs flux) et ne duplique pas l'analyse détaillée des alternatives, qui réside dans chaque fichier du dossier [../adr/](../adr/README.md).

## 2. Tableau récapitulatif des décisions architecturales

| Identifiant | Sujet / Domaine | Décision retenue | Justification synthétique | Statut | Lien ADR |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `ADR-001` | Style architectural | [Ex. Monolithe modulaire full-stack] | [Ex. Réduit la complexité opérationnelle du MVP tout en isolant les domaines métiers] | `APPROVED` | [ADR-001](../adr/ADR-001.md) |
| `ADR-002` | Persistance & Données | [Ex. PostgreSQL relationnel] | [Ex. Garantit l'intégrité transactionnelle ACID des commandes et paiements] | `APPROVED` | [ADR-002](../adr/ADR-002.md) |
| `ADR-003` | Authentification & Accès | [Ex. Sessions serveur HTTP-only + RBAC] | [Ex. Réduit la surface d'exposition XSS et simplifie la révocation immédiate] | `REVIEW` | [ADR-003](../adr/ADR-003.md) |
| `ADR-004` | Frontend & Design System | [Ex. Approche par Design Tokens CSS & composants accessibles] | [Ex. Assure la fidélité avec `04-ux-ui/design-system.md` et la conformité WCAG AA] | `APPROVED` | [ADR-004](../adr/ADR-004.md) |

## 3. Arbitrages techniques en attente (`[POINT EN ATTENTE]`)

| ID Question | Sujet | Options en balance | Condition pour trancher | ADR cible |
| :--- | :--- | :--- | :--- | :--- |
| `Q-ARCH-01` | [Sujet à trancher] | [Option A vs Option B] | [Validation budget / contrainte hébergeur] | `ADR-005` (à créer) |

## 4. Règles de gouvernance architecturale pour le développement

1. **Respect des décisions `APPROVED` :** Toute brique technologique ou règle architecturale marquée `APPROVED` ci-dessus fait foi pour le [Developer Handoff](../07-delivery/developer-handoff.md).
2. **Procédure de révision :** Si une contrainte découverte lors de l'implémentation remet en cause une décision, consulter l'ADR lié dans [../adr/README.md](../adr/README.md) et créer un ADR de remplacement avant de modifier la stack ou les frontières de composants.
