# Registre des Architecture Decision Records (ADR) — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/adr/README.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Index central](../README.md) | [Synthèse des décisions d'architecture](../05-architecture/architecture-decisions.md) | [Vue d'ensemble du système](../05-architecture/system-overview.md)

## 1. Rôle des ADR dans ce projet

Un **Architecture Decision Record (ADR)** documente une décision structurante (architecture logicielle, choix de stack, modélisation des données, sécurité, infrastructure ou parti pris majeur de Design System / UX) ainsi que le contexte, le problème résolu, les alternatives étudiées et les conséquences acceptées.

L'objectif de ce registre est d'éviter que l'équipe de développement ne réinterprète ou ne remette en cause des arbitrages déjà validés sans connaître les contraintes qui les ont motivés.

## 2. Convention de nommage et d'identifiants

- **Emplacement :** Tous les ADR détaillés résident dans `docs/adr/`.
- **Format du nom de fichier :** `ADR-NNN.md` où `NNN` est un numéro séquentiel sur 3 chiffres (`ADR-001.md`, `ADR-002.md`...).
- **Identifiant stable :** L'identifiant `ADR-NNN` est unique et permanent. Un identifiant attribué n'est jamais réutilisé, même si la décision est remplacée.

## 3. Cycle de vie et règles de gestion des décisions

### 3.1. Statuts autorisés
- `DRAFT` : Décision en cours d'analyse ou de rédaction.
- `REVIEW` : Décision proposée (`[DECISION PROPOSEE]`), soumise à la validation du porteur de projet.
- `APPROVED` : Décision validée (`[DECISION VALIDEE]`), applicable comme référence par l'équipe de développement.
- `SUPERSEDED` : Décision antérieure remplacée par un nouvel ADR.

### 3.2. Règles de création, modification et remplacement
1. **Création :** Toute décision ayant un impact fort sur le coût, la sécurité, la maintenabilité, le modèle de données, l'expérience utilisateur ou la dépendance à un service tiers donne lieu à la création d'un nouveau fichier `ADR-NNN.md` à partir du modèle `templates/adr.md`.
2. **Modification d'un ADR `DRAFT` ou `REVIEW` :** Le fichier peut être mis à jour directement tant qu'il n'a pas été approuvé.
3. **Interdiction d'écrasement d'un ADR `APPROVED` :** Une décision au statut `APPROVED` ne doit pas être réécrite silencieusement pour inverser un choix.
4. **Remplacement (`SUPERSEDED`) :** Si un changement de contexte ou de périmètre oblige à modifier une décision `APPROVED` :
   - Créer un nouvel ADR (`ADR-MMM.md`) expliquant le nouveau contexte et la nouvelle décision.
   - Mettre à jour le statut de l'ancien fichier (`ADR-NNN.md`) à `SUPERSEDED` en ajoutant en en-tête le lien explicite : *Remplacé par [ADR-MMM](./ADR-MMM.md)*.
   - Mettre à jour le tableau ci-dessous et le fichier [../05-architecture/architecture-decisions.md](../05-architecture/architecture-decisions.md).

## 4. Index des décisions (`ADR-xxx`)

| ID | Titre de la décision | Statut | Date | Remplacé par | Fichier détaillé |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `ADR-001` | [Titre de la décision 1] | `APPROVED` | [YYYY-MM-DD] | — | [ADR-001.md](./ADR-001.md) |
| `ADR-002` | [Titre de la décision 2] | `REVIEW` | [YYYY-MM-DD] | — | [ADR-002.md](./ADR-002.md) |
