# Standards de Documentation Distribuée, Profils, Traçabilité et ADR (V2.1)

## 1. Principe fondamental : Documentation distribuée dans `docs/`

La documentation produite pour le projet de l'utilisateur est organisée dans un dossier `docs/` modulaire, indépendant de tout IDE, agent de codage ou plateforme.

### Séparation stricte entre le Skill et le Projet
1. **Fichiers internes du skill** (`SKILL.md`, `references/`, `workflows/`, `templates/`) : instructions et modèles destinés à l'agent. Ils ne doivent jamais être confondus avec les livrables d'un projet.
2. **Fichiers générés pour le projet** (`README.md` racine et `docs/...`) : blueprint spécifique au projet de l'utilisateur.
3. **Neutralité vis-à-vis des outils** : N'impose jamais de dossier `.opencode/`, `.claude/`, `.cursor/` ou `.windsurf/`. Ces fichiers ne sont générés que si l'utilisateur les demande explicitement.

## 2. Arborescence cible et correspondance exacte avec `templates/`

Chaque fichier de l'arborescence cible `docs/` possède son template dédié dans `templates/` :

| Chemin de destination dans le projet (`docs/...`) | Template source dans le skill (`templates/...`) | Rôle du document |
| :--- | :--- | :--- |
| `docs/README.md` | `templates/docs-readme.md` | Index central, profil retenu, qualification et statut des documents |
| `docs/01-discovery/project-brief.md` | `templates/project-brief.md` | Problème, acteurs, proposition de valeur, objectifs `OBJ-xxx`, contraintes |
| `docs/01-discovery/product-vision.md` | `templates/product-vision.md` | Vision long terme, principes produit, boucle de valeur, horizons |
| `docs/01-discovery/scope.md` | `templates/scope.md` | Périmètre MVP, reports post-MVP, exclusions explicites |
| `docs/02-research/research-report.md` | `templates/research-report.md` | Benchmark solutions existantes, dépôts open source, licences, options tech |
| `docs/02-research/references-analysis.md` | `templates/references-analysis.md` | Analyse UX/UI des références visuelles (12 axes & 4 catégories) |
| `docs/03-product-design/requirements.md` | `templates/requirements.md` | Acteurs `ACT-xxx`, règles `BR-xxx`, exigences `FR-xxx` et `NFR-xxx` |
| `docs/03-product-design/personas.md` | `templates/personas.md` | Fiches personas `PER-xxx` et contextes d'utilisation |
| `docs/03-product-design/user-journeys.md` | `templates/user-journeys.md` | Parcours utilisateurs macroscopiques `UJ-xxx` |
| `docs/03-product-design/user-flows.md` | `templates/user-flows.md` | Flux opérationnels détaillés `UF-xxx` (nominaux, alternatifs, erreurs) |
| `docs/03-product-design/sitemap.md` | `templates/sitemap.md` | Architecture de l'information, arborescence des écrans `SCR-xxx` et navigation |
| `docs/04-ux-ui/visual-direction.md` | `templates/visual-direction.md` | Direction artistique, ambiance, thème, typographie et surfaces |
| `docs/04-ux-ui/design-system.md` | `templates/design-system.md` | Tokens (couleurs WCAG, typo, espace), composants `COMP-xxx` et états |
| `docs/04-ux-ui/responsive-guidelines.md` | `templates/responsive-guidelines.md` | Breakpoints, grilles et règles d'adaptation multi-supports |
| `docs/04-ux-ui/screens/screen-NNN.md` | `templates/screen-specification.md` | Spécification détaillée de l'écran `SCR-NNN` (grille des 6 états qualifiés) |
| `docs/05-architecture/system-overview.md` | `templates/technical-architecture.md` | Vue d'ensemble du système, contexte, composants `MOD-xxx`, flux, dépendances |
| `docs/05-architecture/architecture-decisions.md` | `templates/architecture-decisions.md` | Synthèse structurée des décisions architecturales avec renvoi vers `adr/` |
| `docs/05-architecture/data-model.md` | `templates/database-schema.md` | Entités `ENT-xxx`, dictionnaire de données, relations, index, ERD, rétention |
| `docs/05-architecture/api-specification.md` | `templates/api-specification.md` | Contrats d'API `API-xxx`, schémas, validations, erreurs, sécurité |
| `docs/05-architecture/security.md` | `templates/security.md` | Actifs, modèle de menaces, auth, matrice d'autorisation, secrets, RGPD |
| `docs/06-quality/test-strategy.md` | `templates/test-strategy.md` | Stratégie de tests multi-niveaux et catalogue `TEST-xxx` |
| `docs/06-quality/acceptance-criteria.md` | `templates/acceptance-criteria.md` | Référentiel consolidé des critères d'acceptation `AC-xxx` (Given/When/Then) |
| `docs/06-quality/risk-register.md` | `templates/risk-register.md` | Registre des risques `RISK-xxx` et plans de mitigation |
| `docs/07-delivery/roadmap.md` | `templates/roadmap.md` | Feuille de route par lots incrémentaux, jalons et dépendances |
| `docs/07-delivery/traceability.md` | `templates/traceability.md` | Matrice de traçabilité relationnelle souple et justification des `N/A` |
| `docs/07-delivery/developer-handoff.md` | `templates/developer-handoff.md` | Dossier de passation autonome et Definition of Done |
| `docs/adr/README.md` | `templates/adr-readme.md` | Rôle des ADR, conventions, règles de cycle de vie et index des décisions |
| `docs/adr/ADR-NNN.md` | `templates/adr.md` | Fiche détaillée d'un Architecture Decision Record (`ADR-001`...) |

## 3. Les Trois Profils Documentaires Opérationnels (`Compact`, `Standard`, `Complet`)

### 3.1. Définition des profils
1. **Profil `Compact`** :
   - *Projets cibles :* Projets simples — site vitrine, landing page, petit outil interne, script/CLI ou application à périmètre limité.
   - *Objectif :* Conserver toutes les décisions essentielles (problème, périmètre, UX/UI, architecture, passation) avec une documentation minimale (typiquement 6 à 9 fichiers) sans aucun fichier artificiel ou redondant.
2. **Profil `Standard`** :
   - *Projets cibles :* Applications comportant plusieurs fonctionnalités, plusieurs rôles, une API, une base de données ou des parcours utilisateurs significatifs (SaaS MVP, application web/mobile métier).
   - *Objectif :* Documenter de manière structurée et modulaire les principales dimensions du produit, de son UX/UI et de son architecture (typiquement 13 à 20 fichiers).
3. **Profil `Complet`** :
   - *Projets cibles :* Systèmes complexes — SaaS avancé multi-rôles, plateforme multi-services, système distribué, application critique, projet IA/Data complexe ou système IoT.
   - *Objectif :* Assurer une documentation granulaire complète, une traçabilité exhaustive de bout en bout et une gestion formalisée des risques, de la sécurité et des ADR (22+ fichiers).

### 3.2. Qualification des documents (`Obligatoire`, `Conditionnel`, `Fusionnable`, `Non applicable`)
Dans `docs/README.md`, chaque document est qualifié explicitement :
- `OBLIGATOIRE` : Fichier créé de manière autonome.
- `CONDITIONNEL` : Fichier créé uniquement si la dimension existe dans le projet (ex. `references-analysis.md` si des références visuelles sont étudiées ; `api-specification.md` si le système expose ou consomme une API ; `04-ux-ui/` si le système comporte une interface utilisateur).
- `FUSIONNÉ -> [fichier hôte]` : Les sections essentielles du document sont intégrées dans un fichier hôte pour alléger l'arborescence.
- `N/A` (Non applicable) : Document sans objet pour la nature du projet (avec justification).

### 3.3. Règles de fusion autorisées (Profil `Compact` et allègements `Standard`)
Lorsqu'une fusion est appliquée, **aucune responsabilité ni information essentielle ne doit disparaître** ; le fichier hôte intègre une section clairement titrée reprenant les éléments clés du document fusionné :
- **Vision + Brief** → fusionnés dans `01-discovery/project-brief.md` (conserve la déclaration de vision et les principes directeurs).
- **Requirements + Scope (+ Personas / Flows / Sitemap simples + Traçabilité légère)** → fusionnés dans `03-product-design/requirements.md` (conserve les inclusions/exclusions MVP, les exigences `FR-xxx`/`NFR-xxx`, les critères `AC-xxx` et le tableau de traçabilité).
- **Direction visuelle + Design System (+ Responsive)** → fusionnés dans `04-ux-ui/design-system.md` (conserve le positionnement esthétique, les tokens couleurs/typo/espacements, les composants `COMP-xxx` et les breakpoints).
- **Architecture + Modèle de données (+ Synthèse des décisions / Sécurité simple)** → fusionnés dans `05-architecture/system-overview.md` si le schéma comporte peu d'entités (conserve le diagramme ERD, les entités `ENT-xxx`, les contrôles de sécurité et le tableau des décisions renvoyant à `adr/ADR-001.md`).
- **Roadmap + Handoff (+ Stratégie de tests essentielle)** → fusionnés dans `07-delivery/developer-handoff.md` (conserve le découpage par lots, les tests requis et la Definition of Done).

### 3.4. Règle d'évolution de profil (`Compact` → `Standard` → `Complet`)
Lorsqu'un projet initialement cadré en profil `Compact` (ou `Standard`) s'enrichit et nécessite de passer au profil supérieur :
1. **Extraction sans perte :** Extraire la section fusionnée du fichier hôte vers son nouveau fichier dédié (ex. extraire le modèle de données de `system-overview.md` vers `05-architecture/data-model.md` en utilisant `templates/database-schema.md`).
2. **Immuabilité des identifiants :** Conserver strictement tous les identifiants déjà attribués (`FR-001`, `SCR-001`, `ENT-001`, `ADR-001`, `AC-001`, etc.). Ne jamais renuméroter les éléments existants.
3. **Préservation des liens et de la continuité :** Dans le fichier hôte d'origine, remplacer la section extraite par un court paragraphe de renvoi avec un lien Markdown relatif valide (ex. `> Section extraite lors du passage au profil Standard : voir [Modèle de données](./data-model.md).`) afin qu'aucun lecteur ni lien existant ne soit perdu.
4. **Traçabilité du changement :** Mettre à jour `docs/README.md` (qualification `FUSIONNÉ` → `OBLIGATOIRE`) et incrémenter la version des documents touchés.

## 4. Cycle de vie et Statuts documentaires obligatoires

Chaque fichier de `docs/` affiche en en-tête l'un des **4 statuts normalisés** :
- `DRAFT` : Brouillon en cours d'élaboration.
- `REVIEW` : Soumis à la validation de l'utilisateur.
- `APPROVED` : Validé par l'utilisateur ; vérité de référence protégée contre tout écrasement arbitraire.
- `SUPERSEDED` : Remplacé par un nouveau document ou un nouvel ADR (avec lien explicite vers le remplaçant).

## 5. Convention d'identifiants stables et Traçabilité relationnelle souple

### 5.1. Nomenclature harmonisée des identifiants
| Préfixe | Type d'élément | Fichier principal |
| :--- | :--- | :--- |
| `OBJ-001` | Objectif métier / KPI | `01-discovery/project-brief.md` |
| `REF-001` | Référence visuelle ou solution étudiée | `02-research/references-analysis.md` |
| `ACT-001` | Acteur ou rôle système | `03-product-design/requirements.md` |
| `PER-001` | Persona utilisateur | `03-product-design/personas.md` |
| `UJ-001` | User Journey (parcours macro) | `03-product-design/user-journeys.md` |
| `UF-001` | User Flow (flux opérationnel) | `03-product-design/user-flows.md` |
| `FR-001` | Exigence fonctionnelle (*Functional Requirement*) | `03-product-design/requirements.md` |
| `NFR-001` | Exigence non fonctionnelle (*Non-Functional Requirement*) | `03-product-design/requirements.md` |
| `BR-001` | Règle métier (*Business Rule*) | `03-product-design/requirements.md` |
| `COMP-001` | Composant UI du Design System | `04-ux-ui/design-system.md` |
| `SCR-001` | Écran ou vue spécifiée | `04-ux-ui/screens/screen-001.md` |
| `MOD-001` | Composant ou module technique | `05-architecture/system-overview.md` |
| `ENT-001` | Entité ou donnée du modèle | `05-architecture/data-model.md` |
| `API-001` | Contrat d'API, endpoint ou événement | `05-architecture/api-specification.md` |
| `ADR-001` | Décision architecturale (*ADR*) | `adr/ADR-001.md` & `05-architecture/architecture-decisions.md` |
| `AC-001` | Critère d'acceptation (*Acceptance Criterion*) | `03-product-design/requirements.md` & `06-quality/acceptance-criteria.md` |
| `RISK-001` | Risque identifié | `06-quality/risk-register.md` |
| `TEST-001` | Scénario ou suite de test | `06-quality/test-strategy.md` |

### 5.2. Règles de traçabilité relationnelle (Non linéaire)
La traçabilité dans `docs/07-delivery/traceability.md` ne doit jamais forcer une chaîne artificielle où chaque exigence devrait obligatoirement posséder un écran, un composant, une API, une entité et un ADR :
- **Relations pertinentes uniquement :** Relier chaque exigence (`FR-xxx`, `NFR-xxx`) aux éléments réellement impliqués (`BR`, `UJ`/`UF`, `SCR`, `COMP`, `API`, `ENT`, `ADR`, `AC`, `TEST`).
- **Cardinalité souple :** `0`, `1` ou `N` éléments par catégorie.
- **Justification des `N/A` :** Lorsqu'une catégorie majeure est `N/A` pour une exigence (ex. exigence purement backend sans écran `SCR`, ou exigence purement éditoriale/UI sans `API` ni `ENT`), indiquer `N/A` et sa raison courte.
- **Exigence minimale universelle :** Toute exigence retenue dans le MVP (`FR-xxx` ou `NFR-xxx`) doit obligatoirement être reliée à au moins un **critère d'acceptation (`AC-xxx`)** et un **moyen de vérification (`TEST-xxx`)**.
