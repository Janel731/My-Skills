# Workflow 05 — Technical Architecture, Données, API, Sécurité & ADR

## 1. Objectif de la phase
Concevoir une architecture technique cohérente, simple, sécurisée et parfaitement alignée avec les exigences produit (`03-product-design/`) et les spécifications d'écrans (`04-ux-ui/`), puis documenter la synthèse des décisions dans `docs/05-architecture/architecture-decisions.md` et chaque décision structurante sous forme d'ADR dans `docs/adr/`.

## 2. Ressources internes du skill à mobiliser
- **Références** : `references/software-architecture.md`, `references/database-design.md`, `references/api-design.md`, `references/security-guidelines.md`, `references/devops-and-deployment.md`, `references/documentation-standards.md`
- **Templates** : `templates/technical-architecture.md`, `templates/architecture-decisions.md`, `templates/database-schema.md`, `templates/api-specification.md`, `templates/security.md`, `templates/adr-readme.md`, `templates/adr.md`

## 3. Entrées
- Exigences fonctionnelles et non fonctionnelles (`docs/03-product-design/requirements.md`).
- Design System et spécifications des écrans (`docs/04-ux-ui/`).
- Résultats de la recherche technologique (`docs/02-research/research-report.md`).

## 4. Déroulement opérationnel

1. **Vue d'ensemble du système (`docs/05-architecture/system-overview.md` via `templates/technical-architecture.md`)** :
   - Sélectionne l'architecture la plus simple qui satisfait les exigences (monolithe modulaire par défaut sauf justification démontrable).
   - Définit le contexte, les frontières, les composants (`MOD-001`...), leurs responsabilités, leurs modes de communication, leurs dépendances internes/externes et les contraintes techniques.
   - Produis les diagrammes Mermaid pertinents (contexte, composants/conteneurs, séquences critiques) strictement fidèles au texte.
   - En profil `Compact`, si le modèle de données est très simple, il peut être fusionné dans une section dédiée de `system-overview.md`.
2. **Synthèse des décisions et Registre ADR (`docs/05-architecture/architecture-decisions.md`, `docs/adr/README.md` et `docs/adr/ADR-NNN.md`)** :
   - Utilise `templates/architecture-decisions.md` pour créer `docs/05-architecture/architecture-decisions.md` (identifiant, sujet, décision, justification synthétique, statut et lien vers l'ADR, sans dupliquer tout le texte de l'ADR).
   - Utilise `templates/adr-readme.md` pour créer `docs/adr/README.md` (rôle des ADR, convention de nommage, règles de création/modification/remplacement et index des décisions).
   - Utilise `templates/adr.md` pour rédiger chaque fiche `docs/adr/ADR-NNN.md` détaillée.
3. **Modélisation des données (`docs/05-architecture/data-model.md` via `templates/database-schema.md`)** :
   - Définit toutes les entités (`ENT-001`...), leurs attributs, types logiques, clés, contraintes, sensibilité, relations, index justifiés par les écrans `SCR-xxx`, règles de rétention/sauvegarde et diagramme ERD Mermaid.
4. **Spécification des contrats d'API (`docs/05-architecture/api-specification.md` via `templates/api-specification.md`)** :
   - Vérifie que chaque action dynamique ou chargement de données requis par les écrans `SCR-xxx` et les flux `UF-xxx` est couvert par un contrat `API-001`... (route, méthode, auth, permissions, schémas requête/réponse, codes d'erreur métier, pagination, rate limiting, idempotence).
5. **Architecture de sécurité et confidentialité (`docs/05-architecture/security.md` via `templates/security.md`)** :
   - Documente les actifs, les frontières de confiance, le modèle de menaces, l'authentification, la matrice d'autorisation par rôle (`ACT-xxx`), la protection des données (RGPD), la gestion des secrets et la journalisation d'audit.

## 5. Arbitrages d'autonomie
- **Tu décides seul** : la normalisation du schéma de base de données, les index techniques, le format standardisé des erreurs API, les conventions de nommage et la découpe interne des modules.
- **Tu fais valider par l'utilisateur** : la stack technologique principale, le choix d'hébergement/services tiers payants et les compromis architecturaux à fort impact sur le coût ou l'exploitation.

## 6. Critères de sortie (Passage à la Phase 6)
- [ ] Chaque composant des diagrammes Mermaid est décrit dans `system-overview.md`.
- [ ] `architecture-decisions.md` et `adr/README.md` sont synchronisés avec les fichiers `adr/ADR-NNN.md`.
- [ ] Chaque donnée dynamique affichée ou saisie dans `04-ux-ui/screens/` existe dans `data-model.md` et transite par un contrat de `api-specification.md`.
- [ ] Les contrôles d'authentification, d'autorisation et de confidentialité sont spécifiés dans `security.md`.
