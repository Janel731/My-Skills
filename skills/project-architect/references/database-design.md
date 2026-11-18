# Modélisation des Données (`docs/05-architecture/data-model.md`)

## 1. Démarche de modélisation

1. **Partir du domaine métier et des écrans** : Chaque entité (`ENT-001`...) et chaque attribut doivent correspondre aux concepts manipulés dans les exigences (`FR-xxx`), les règles métier (`BR-xxx`) et les contenus affichés/saisis sur les écrans (`SCR-xxx`).
2. **Choisir le moteur de stockage adapté** :
   - **Relationnel (PostgreSQL, MySQL, SQLite)** : Choix par défaut pour les données structurées, l'intégrité référentielle et les transactions ACID.
   - **Document / Clé-Valeur / Recherche / Vecteurs / Objet** : Uniquement lorsque la nature des données (fichiers binaires/médias sur stockage objet S3-compatible, cache éphémère Redis, recherche plein texte ou embeddings vectoriels pgvector/moteur dédié) le justifie. Ne jamais choisir une base NoSQL par simple effet de mode.
   - Consigner le choix du stockage dans un ADR (`docs/adr/ADR-NNN.md`).
3. **Garantir l'intégrité au niveau des données** : Clés primaires, clés étrangères, contraintes `NOT NULL`, `UNIQUE`, `CHECK` et comportements de suppression (`RESTRICT`, `CASCADE`, `SET NULL` ou suppression logique *soft delete*).

## 2. Spécification de chaque entité (`ENT-xxx`)

Pour chaque entité du modèle, documente :

- **Identifiant et Nom métier / technique** : ex. `ENT-001 — Order (orders)`.
- **Description et propriétaire métier**.
- **Tableau des attributs (Dictionnaire de données)** :
  - Nom du champ.
  - Type logique (ex. `UUID`, `VARCHAR(255)`, `INTEGER`, `DECIMAL(12,2)`, `TIMESTAMPTZ`, `JSONB`, `ENUM`).
  - Obligatoire (`Oui` / `Non`).
  - Valeur par défaut.
  - Contraintes et validations (plage, format, unicité).
  - Sensibilité (Public, Interne, Donnée personnelle PII, Secret/Sensible).
- **Relations et cardinalités** : `1:1`, `1:N`, `N:M` (avec table de jointure explicite).
- **Cycle de vie et machine à états** : Si l'entité possède un statut (ex. `DRAFT -> SUBMITTED -> PAID -> CANCELLED`), documenter les transitions valides et qui peut les déclencher.

## 3. Indexation et performance des requêtes

Ne crée pas d'index au hasard. Identifie les **requêtes réelles anticipées** (alimentant les listes, filtres et recherches des écrans `SCR-xxx`) et définis :
- Les index sur clés étrangères.
- Les index composites correspondant aux filtres et tris fréquents (ex. `(organization_id, status, created_at DESC)`).
- Les index d'unicité partiels si une suppression logique (`deleted_at IS NULL`) est utilisée.

## 4. Cycle de vie, rétention, sauvegardes et migrations

- **Rétention et conformité (RGPD)** : Durée de conservation des données actives, politique d'anonymisation ou de purge des données personnelles, mécanisme d'export/droit à l'oubli.
- **Auditabilité** : Horodatages systématiques (`created_at`, `updated_at` en UTC) et journalisation des modifications critiques si requis par le métier.
- **Migrations de schéma** : Stratégie d'évolution du schéma versionnée et reproductible (migrations montantes/descendantes, compatibilité ascendante lors des déploiements).
- **Sauvegardes et restauration** : Fréquence des sauvegardes automatiques, rétention, chiffrement et procédure de test de restauration alignée sur les objectifs RPO/RTO.

## 5. Diagramme Entité-Relation (ERD Mermaid)

Fournis systématiquement un diagramme `erDiagram` Mermaid dans `docs/05-architecture/data-model.md` reflétant exactement les entités et relations décrites.
