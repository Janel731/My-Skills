# Project Architect & Product Designer — From Idea to Blueprint (V2.1)

Skill de **cadrage produit, Product Design, UX/UI Design, ingénierie des exigences et architecture logicielle**, structuré selon le format ouvert **Agent Skills** et conçu pour être utilisé de manière portable dans différents environnements d'agents IA (notamment **Claude**, **ChatGPT** et les plateformes compatibles).

## 1. Philosophie et rôle de la V2.1

**Project Architect & Product Designer (V2.1)** accompagne un porteur de projet depuis une idée initiale jusqu'à un **blueprint complet, validé, cohérent et directement exploitable** par une équipe de développement.

Cette version **V2.1** consolide la V2 autour de six principes structurants :

- **Équilibre entre Product Design, UX/UI et Architecture logicielle** : analyse des références visuelles en 12 dimensions et 4 catégories (*À reproduire, À adapter, À éviter, À clarifier*), personas, user journeys, user flows, sitemap, direction artistique, design system complet et spécifications détaillées des écrans (`SCR-001`...).
- **Examen proportionné de la grille des 6 états d'écran** : examen systématique des 6 catégories de référence (*Initial, Chargement, Vide, Erreur, Succès, Désactivé*) sur chaque écran, avec qualification explicite entre `Applicable` (spécifié en détail), `Non applicable (N/A + justification)` et `À déterminer` (`[POINT EN ATTENTE]`).
- **Distinction stricte entre spécifications d'interface et livrables visuels** : différenciation transparente entre les spécifications textuelles d'écran et les représentations graphiques (wireframes, maquettes, prototypes), sans jamais prétendre qu'une maquette graphique existe lorsqu'elle n'a pas été produite.
- **Documentation distribuée `docs/` et 3 profils opérationnels (`Compact`, `Standard`, `Complet`)** : qualification claire des documents (*Obligatoire, Conditionnel, Fusionnable, Non applicable*), règles de fusion pour les petits projets et procédure d'évolution sans rupture de `Compact` vers `Standard` puis `Complet`.
- **Traçabilité relationnelle souple et identifiants harmonisés** : mise en relation pertinente (multiples, optionnelles ou `N/A` justifiées) entre exigences (`FR-001`, `NFR-001`), règles métier (`BR-001`), parcours (`UJ-001`, `UF-001`), écrans (`SCR-001`), composants (`COMP-001`), API (`API-001`), données (`ENT-001`), décisions (`ADR-001`), critères d'acceptation (`AC-001`) et tests (`TEST-001`).
- **Frontière stricte entre conception et implémentation** : le skill conçoit, arbitre, documente et prépare le `developer-handoff.md` ; il ne développe pas arbitrairement le code source du produit.

## 2. Organisation du paquet du skill

```text
project-architect/
├── README.md                                    # Architecture du paquet, portabilité, installation et utilisation
├── SKILL.md                                     # Instructions maîtresses indépendantes de la plateforme (< 500 lignes)
├── CHANGELOG.md                                 # Historique détaillé des modifications V2 → V2.1
├── AUDIT-REPORT.md                              # Rapport d'audit structurel, méthodologique et limites de validation
├── MIGRATION-GUIDE.md                           # Guide de passage de la V2 à la V2.1
├── references/                                  # 14 guides méthodologiques et standards de référence
│   ├── project-discovery.md                     # Cadrage initial, problème, valeur, contraintes et KPI (OBJ-xxx)
│   ├── research-methodology.md                  # Recherche technique, dépôts GitHub, licences et sources
│   ├── visual-references-analysis.md            # Grille d'analyse visuelle en 12 dimensions et 4 catégories
│   ├── product-design-and-ux.md                 # Personas (PER-xxx), journeys (UJ-xxx), flows (UF-xxx), IA, a11y
│   ├── ui-design-and-design-system.md           # Direction artistique, tokens, composants (COMP-xxx), livrables visuels
│   ├── screen-specifications.md                 # Spécification des écrans (SCR-xxx) et grille des 6 états qualifiés
│   ├── functional-specification.md              # Exigences (FR-xxx, NFR-xxx, BR-xxx), MoSCoW, critères AC-xxx
│   ├── software-architecture.md                 # Styles architecturaux, composants (MOD-xxx), diagrammes Mermaid
│   ├── database-design.md                       # Modélisation des données (ENT-xxx), dictionnaire, ERD, rétention
│   ├── api-design.md                            # Contrats d'API (API-xxx), schémas, erreurs, sécurité, idempotence
│   ├── security-guidelines.md                   # Modèle de menaces, auth, permissions, secrets, RGPD
│   ├── testing-strategy.md                      # Stratégie de tests (TEST-xxx) et critères d'acceptation (AC-xxx)
│   ├── devops-and-deployment.md                 # Environnements, CI/CD, observabilité, exploitation et coûts
│   └── documentation-standards.md               # Architecture docs/, 3 profils, règles de fusion/évolution, ADR
├── workflows/                                   # 7 procédures opérationnelles phase par phase
│   ├── 01-discovery.md                          # Phase 1 — Discovery & Cadrage
│   ├── 02-research.md                           # Phase 2 — Research & Analyse des références
│   ├── 03-product-design.md                     # Phase 3 — Product Design, Exigences & UX
│   ├── 04-ux-ui-design.md                       # Phase 4 — UX/UI Design, Design System & Écrans
│   ├── 05-technical-architecture.md             # Phase 5 — Technical Architecture, Décisions, Données, API & ADR
│   ├── 06-critical-review.md                    # Phase 6 — Critical Review, Qualité & Risques
│   └── 07-delivery-and-handoff.md               # Phase 7 — Delivery, Traçabilité & Developer Handoff
└── templates/                                   # 28 modèles Markdown couvrant toute l'arborescence cible docs/
    ├── docs-readme.md                           # -> docs/README.md
    ├── project-brief.md                         # -> docs/01-discovery/project-brief.md
    ├── product-vision.md                        # -> docs/01-discovery/product-vision.md
    ├── scope.md                                 # -> docs/01-discovery/scope.md
    ├── research-report.md                       # -> docs/02-research/research-report.md
    ├── references-analysis.md                   # -> docs/02-research/references-analysis.md
    ├── requirements.md                          # -> docs/03-product-design/requirements.md
    ├── personas.md                              # -> docs/03-product-design/personas.md
    ├── user-journeys.md                         # -> docs/03-product-design/user-journeys.md
    ├── user-flows.md                            # -> docs/03-product-design/user-flows.md
    ├── sitemap.md                               # -> docs/03-product-design/sitemap.md
    ├── visual-direction.md                      # -> docs/04-ux-ui/visual-direction.md
    ├── design-system.md                         # -> docs/04-ux-ui/design-system.md
    ├── responsive-guidelines.md                 # -> docs/04-ux-ui/responsive-guidelines.md
    ├── screen-specification.md                  # -> docs/04-ux-ui/screens/screen-NNN.md
    ├── technical-architecture.md                # -> docs/05-architecture/system-overview.md
    ├── architecture-decisions.md                # -> docs/05-architecture/architecture-decisions.md [NOUVEAU V2.1]
    ├── database-schema.md                       # -> docs/05-architecture/data-model.md
    ├── api-specification.md                     # -> docs/05-architecture/api-specification.md
    ├── security.md                              # -> docs/05-architecture/security.md
    ├── test-strategy.md                         # -> docs/06-quality/test-strategy.md
    ├── acceptance-criteria.md                   # -> docs/06-quality/acceptance-criteria.md
    ├── risk-register.md                         # -> docs/06-quality/risk-register.md
    ├── roadmap.md                               # -> docs/07-delivery/roadmap.md
    ├── traceability.md                          # -> docs/07-delivery/traceability.md
    ├── developer-handoff.md                     # -> docs/07-delivery/developer-handoff.md
    ├── adr-readme.md                            # -> docs/adr/README.md [NOUVEAU V2.1]
    └── adr.md                                   # -> docs/adr/ADR-NNN.md
```

## 3. Portabilité et distinction des trois niveaux d'architecture

Pour déployer ce skill correctement, il est essentiel de distinguer trois éléments :

1. **Le format de structuration Agent Skills** :
   - Prérequis structurels : un dossier portant le nom en kebab-case (`project-architect/`), contenant à sa racine un fichier `SKILL.md` doté d'un en-tête YAML (`name` et `description`) et d'un corps d'instructions concis (`< 500` lignes), complété par des sous-dossiers de ressources (`references/`, `workflows/`, `templates/`).
2. **Le contenu méthodologique indépendant de la plateforme** :
   - Les instructions de `SKILL.md`, les méthodes de `references/`, les séquences de `workflows/` et les modèles de `templates/` sont rédigés en Markdown pur et ne dépendent d'aucun outil propriétaire, IDE ou API spécifique.
3. **Les modalités d'intégration propres à chaque plateforme hôte** :
   - **Attention :** Une archive `.zip` n'est **pas** automatiquement reconnue comme un skill exécutable par toutes les plateformes conversationnelles. Le mode d'installation réel dépend des mécanismes d'importation et de gestion de contexte propres à chaque environnement.

## 4. Procédures d'installation selon l'environnement

### A. Environnements d'agents supportant nativement les dossiers Agent Skills
*(Agents disposant d'un gestionnaire de skills multi-fichiers lisant `SKILL.md` et ses sous-dossiers)*
1. Extraire le dossier `project-architect/` (ou importer le paquet selon le mécanisme supporté par le gestionnaire de skills de l'environnement).
2. Vérifier que le fichier `SKILL.md` est reconnu avec l'identifiant `project-architect`.
3. S'assurer que l'agent a accès en lecture aux dossiers `references/`, `workflows/` et `templates/`.

### B. Intégration dans Claude (Claude Projects / Conversationnel)
1. Décompresser l'archive `project-architect-v2.1.zip` sur votre machine (ne pas téléverser le fichier `.zip` brut dans un Project Claude standard si l'environnement d'exécution de code n'est pas sollicité pour le décompresser).
2. Créer un **Project** dans Claude.
3. Copier le contenu de `SKILL.md` dans les **Project Instructions** (Instructions du projet).
4. Ajouter les fichiers Markdown contenus dans `references/`, `workflows/` et `templates/` dans la **Project Knowledge** (Base de connaissances du projet) afin que Claude les consulte automatiquement selon la table de routage de `SKILL.md`.

### C. Intégration dans ChatGPT (Custom GPTs ou ChatGPT Projects)
1. Créer un **Custom GPT** ou un **Project** dans ChatGPT.
2. Copier le contenu de `SKILL.md` dans le champ **Instructions**.
3. **Gestion des fichiers de connaissance (`Knowledge / Files`)** :
   - Les interfaces Custom GPTs et Projects imposent souvent une limite sur le nombre de fichiers individuels téléversés simultanément dans *Knowledge*.
   - *Option 1 (Fichiers Markdown individuels ou regroupés)* : Téléverser les fichiers de `references/`, `workflows/` et les principaux `templates/` directement en Markdown.
   - *Option 2 (Archive ZIP avec Code Interpreter activé)* : Si vous fournissez l'archive `project-architect-v2.1.zip` dans un environnement où **Code Interpreter & Data Analysis** est activé, l'agent peut extraire et lire les fichiers depuis son sandbox Python, mais uniquement lorsque l'exécution de code est active dans la session.
4. Activer **Web Search** pour permettre les vérifications factuelles de la Phase 2 (Research).

### D. Limitations et différences de capacités entre plateformes
- **Accès Web et GitHub** : Certains environnements bloquent l'accès direct à certaines URLs ou à l'API GitHub. Le skill instruit alors l'agent de signaler explicitement `[POINT EN ATTENTE : vérification externe requise]` au lieu d'inventer des licences ou des métriques.
- **Analyse de références visuelles** : L'inspection visuelle nécessite que l'utilisateur fournisse des images (captures d'écran, exports de maquettes) à un modèle doté de capacités de vision multimodale. Une simple URL fournie à un outil de lecture textuelle ne permet pas d'auditer la mise en page graphique.
- **Production des fichiers `docs/`** : Si l'environnement dispose d'un sandbox de génération de fichiers, l'agent crée l'arborescence `docs/` et peut l'exporter en archive ZIP. Dans une session purement conversationnelle sans écriture de fichiers, l'agent restitue les documents Markdown dans la conversation avec leur chemin cible exact (`docs/01-discovery/project-brief.md`, etc.).

## 5. Utilisation et commandes naturelles

- **Cadrage complet** : `« Cadre ce projet : [description de l'idée et des contraintes] »`
- **Analyse visuelle & UX/UI** : `« Analyse ces références visuelles et conçois la direction artistique, le design system et les écrans principaux »`
- **Audit critique** : `« Challenge mon idée et fais la revue critique de mon périmètre et de mon architecture »`
- **Passation développeur** : `« Finalise le dossier docs/, la matrice de traçabilité et le developer-handoff.md »`
