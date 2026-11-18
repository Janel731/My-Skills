# Guide de Migration — Project Architect & Product Designer (V2 → V2.1)

## 1. Objectif de la mise à jour V2.1

La version **V2.1** est une mise à jour corrective et de consolidation. Elle conserve 100 % de l'organisation, des 7 phases de workflow et de la richesse méthodologique de la V2, tout en supprimant les rigidités artificielles et en complétant la couverture des templates documentaires.

## 2. Synthèse des changements structurants et conséquences pour les utilisateurs de la V2

### 2.1. Séparation claire entre `system-overview.md`, `architecture-decisions.md` et `adr/README.md`
- **En V2 :** Le template `templates/technical-architecture.md` couvrait à la fois `system-overview.md` et `architecture-decisions.md`, et `docs/adr/README.md` n'avait pas de template dédié.
- **En V2.1 :**
  - `templates/technical-architecture.md` génère uniquement `docs/05-architecture/system-overview.md` (vue d'ensemble, contexte, frontières, composants, responsabilités, communications, dépendances, diagrammes et contraintes).
  - `templates/architecture-decisions.md` génère `docs/05-architecture/architecture-decisions.md` (synthèse structurée des décisions architecturales avec lien vers chaque ADR, sans duplication).
  - `templates/adr-readme.md` génère `docs/adr/README.md` (règles de gouvernance des ADR et registre des décisions).
- **Conséquence :** Vos projets en profil `Standard` et `Complet` disposent désormais d'un modèle exact pour chaque fichier de `05-architecture/` et `adr/`.

### 2.2. Passage des « 6 états obligatoires » à la « Grille des 6 états examinés et qualifiés »
- **En V2 :** Les 6 états (*Initial, Chargement, Vide, Erreur, Succès, Désactivé*) étaient présentés comme obligatoires sur chaque écran, ce qui pouvait conduire à inventer des états artificiels sur des écrans statiques.
- **En V2.1 :** Les 6 états demeurent la grille de contrôle systématique, mais chaque écran qualifie désormais chaque état en :
  - `Applicable` (spécifié en détail),
  - `Non applicable (N/A)` (avec une justification courte),
  - `À déterminer` (`[POINT EN ATTENTE]`).
- **Conséquence :** Plus aucun état artificiel sur les pages statiques ou de simple lecture, tout en gardant la même exigence de rigueur sur les formulaires et vues dynamiques.

### 2.3. Opérationnalisation des 3 profils documentaires (`Compact`, `Standard`, `Complet`)
- **En V2 :** `templates/docs-readme.md` listait les 26 fichiers comme s'ils étaient tous créés par défaut.
- **En V2.1 :** `docs/README.md` qualifie chaque document en `OBLIGATOIRE`, `CONDITIONNEL`, `FUSIONNÉ -> [fichier hôte]` ou `N/A`. Les règles de fusion pour un projet `Compact` (*Vision + Brief*, *Requirements + Scope*, *Direction visuelle + Design System*, *Architecture + Modèle de données*, *Roadmap + Handoff*) et la procédure d'évolution `Compact → Standard → Complet` sont formalisées.
- **Conséquence :** Un petit projet peut démarrer en profil `Compact` (6 à 9 fichiers) puis évoluer vers `Standard` ou `Complet` par extraction de sections sans casser ses liens Markdown relatifs ni renommer ses identifiants.

### 2.4. Traçabilité relationnelle souple et harmonisation des identifiants (`FR-001`, `AC-001`)
- **En V2 :** La matrice de traçabilité utilisait une chaîne linéaire `F → SCR → COMP → API → ENT → ADR → TEST` et les préfixes `F-001` et `CA-xxx`.
- **En V2.1 :**
  - Les identifiants sont harmonisés sur le standard international : `FR-001` (*Functional Requirement*, remplaçant `F-001`), `AC-001` (*Acceptance Criterion*, remplaçant `CA-xxx`) et `TEST-001` (remplaçant `TEST-UNIT-001`, etc., la catégorie étant portée par une colonne dédiée).
  - La matrice `templates/traceability.md` accepte des relations multiples, optionnelles ou `N/A` (avec colonne de justification des relations absentes).
- **Compatibilité avec vos projets V2 existants :** Si un projet en cours utilise déjà `F-001` et `CA-001`, conservez ses identifiants existants (règle de stabilité des IDs) ou appliquez le renommage `F-` → `FR-` et `CA-` → `AC-` de manière globale lors d'une révision contrôlée. Pour tout nouveau projet démarré en V2.1, `FR-001` et `AC-001` sont utilisés d'emblée.

### 2.5. Distinction explicite entre Spécification d'interface et Livrable visuel
- **En V2.1 :** Chaque fiche écran (`SCR-xxx`) et le `developer-handoff.md` précisent explicitement la nature du livrable fourni (spécification textuelle + wireframe ASCII vs maquette graphique ou prototype), en interdisant de confondre une description textuelle avec une maquette ou d'imposer un outil de design particulier.

## 3. Instructions pour passer de la V2 à la V2.1

1. **Dans un environnement compatible Agent Skills :**
   - Remplacez le dossier `project-architect/` existant par celui contenu dans `project-architect-v2.1.zip`.
2. **Dans Claude (Projects) :**
   - Remplacez le contenu des *Project Instructions* par le nouveau fichier `SKILL.md` (V2.1).
   - Dans la *Project Knowledge*, ajoutez les nouveaux templates `templates/adr-readme.md` et `templates/architecture-decisions.md`, et mettez à jour les fichiers `references/`, `workflows/` et `templates/` modifiés (listés dans `CHANGELOG.md`).
3. **Dans ChatGPT (Custom GPTs / Projects) :**
   - Remplacez le champ *Instructions* par le contenu du nouveau `SKILL.md` (V2.1).
   - Mettez à jour les fichiers de référence dans *Knowledge / Files* (ou l'archive `project-architect-v2.1.zip` si vous utilisez Code Interpreter).
