# Workflow 02 — Research & Analyse des Références

## 1. Objectif de la phase
Étudier le domaine métier, les solutions concurrentes ou open source, les briques technologiques candidates (dépôts GitHub, licences, maturité) ET analyser de manière méthodique toutes les références visuelles ou ergonomiques fournies par l'utilisateur.

## 2. Ressources internes du skill à mobiliser
- **Références** : `references/research-methodology.md`, `references/visual-references-analysis.md`
- **Templates** : `templates/research-report.md`, `templates/references-analysis.md`

## 3. Entrées
- `docs/01-discovery/project-brief.md` (au moins au statut `REVIEW` ou `APPROVED`).
- Références visuelles fournies par l'utilisateur (captures d'écran, URLs de sites/produits, maquettes, moodboards, exemples d'animations) ou contexte permettant d'explorer des références du secteur.

## 4. Déroulement opérationnel

1. **Étude du domaine et des solutions existantes** :
   - Identifie les produits commerciaux comparables et les alternatives open source.
   - Analyse leurs forces, leurs limites fonctionnelles et les irritants utilisateurs connus.
2. **Audit technique et open source (si outils de recherche disponibles)** :
   - Vérifie les dépôts GitHub pertinents : URL canonique, licence exacte, activité récente, releases, dépendances, documentation et adéquation au besoin.
   - Si aucun outil de recherche web n'est disponible, déclare la limite explicitement, marque les éléments évolutifs comme `[POINT EN ATTENTE : vérification externe requise]` et fournis les requêtes de vérification.
3. **Analyse des références visuelles (`REF-001`...)** :
   - Passe chaque référence visuelle au crible des **12 dimensions** de `references/visual-references-analysis.md` (structure/composition, hiérarchie, typographie, couleurs, espacements, grilles/proportions, composants, navigation, interactions, animations, responsive, ambiance/DA).
   - Remplis la matrice de décision obligatoire en 4 catégories :
     1. **Éléments à reproduire**
     2. **Éléments à adapter**
     3. **Éléments à éviter**
     4. **Éléments nécessitant une clarification**
   - N'invente jamais un détail non visible sur une capture.
4. **Rédaction des livrables `docs/02-research/`** :
   - Produis `docs/02-research/research-report.md` et `docs/02-research/references-analysis.md` (ou fusionne-les si Profil Compact).
   - Mets à jour `docs/README.md`.

## 5. Arbitrages d'autonomie
- **Tu décides seul** : les critères de comparaison technique, l'extraction analytique des 12 dimensions visuelles et l'identification des risques de licence ou de maintenance.
- **Tu fais valider par l'utilisateur** : les arbitrages *Build vs Buy vs Reuse* structurants et les points classés dans « 4. Éléments nécessitant une clarification » sur les références visuelles.

## 6. Critères de sortie (Passage à la Phase 3)
- [ ] Les solutions existantes et options techniques ont été comparées avec sources et licences vérifiées (ou marquées non vérifiées).
- [ ] Les références visuelles ont été décomposées selon les 12 dimensions et classées en *À reproduire / À adapter / À éviter / À clarifier*.
- [ ] Les opportunités de différenciation produit et UX sont synthétisées.
