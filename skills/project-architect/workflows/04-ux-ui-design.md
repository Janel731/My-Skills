# Workflow 04 — UX/UI Design (Direction Artistique, Design System, Écrans & Livrables Visuels)

## 1. Objectif de la phase
Concevoir dans le détail ce que l'utilisateur voit, comprend et manipule : fixer la direction artistique, bâtir le Design System (tokens, couleurs, typographie, espacements, grilles, composants, états, micro-interactions), définir les règles responsive et spécifier chaque écran (`SCR-xxx`) en examinant la grille des 6 états et en distinguant rigoureusement les spécifications textuelles des livrables visuels.

## 2. Ressources internes du skill à mobiliser
- **Références** : `references/ui-design-and-design-system.md`, `references/screen-specifications.md`, `references/visual-references-analysis.md`
- **Templates** : `templates/visual-direction.md`, `templates/design-system.md`, `templates/responsive-guidelines.md`, `templates/screen-specification.md`

## 3. Entrées
- Analyse des références visuelles (`docs/02-research/references-analysis.md`).
- Sitemap, User Flows et Exigences (`docs/03-product-design/`).

## 4. Déroulement opérationnel

1. **Identification transparente de la nature des livrables UX/UI** :
   - Distingue explicitement la **spécification d'interface** (document textuel structuré dans `docs/04-ux-ui/`) du **livrable visuel** (wireframe basse fidélité, maquette haute fidélité, diagramme de parcours, prototype interactif ou brief/prompt pour un outil de design).
   - Ne prétends jamais qu'une maquette graphique ou un prototype existe s'il n'a pas été réellement généré. Si les capacités graphiques ne sont pas disponibles, produis une spécification textuelle exhaustive accompagnée de schémas structurels ASCII/Mermaid et signale la limite. N'impose aucun outil de design particulier.
2. **Définition et validation de la Direction Artistique (`docs/04-ux-ui/visual-direction.md`)** :
   - Si des références visuelles ont été analysées, transpose les éléments *À reproduire* et *À adapter* en principes esthétiques concrets.
   - Si aucune référence n'a été fournie, propose une direction artistique argumentée (ambiance, thème clair/sombre, palette, duo typographique, style de surface) et fais valider ce choix structurant.
   - En profil `Compact`, la direction artistique et les règles responsive peuvent être fusionnées directement dans `docs/04-ux-ui/design-system.md`.
3. **Construction du Design System (`docs/04-ux-ui/design-system.md`)** :
   - Définit les tokens chromatiques sémantiques (surfaces, textes, accents, bordures, états succès/alerte/erreur/info) avec vérification du contraste WCAG 2.1 AA (`>= 4.5:1`).
   - Définit l'échelle typographique complète, l'échelle d'espacement (`4px`/`8px`), les grilles, les rayons (`border-radius`), les ombres/élévations et le style d'iconographie.
   - Spécifie les composants réutilisables (`COMP-001`...) avec leurs variantes et leurs états interactifs pertinents.
   - Définit les micro-interactions, durées, courbes d'animation et le comportement `@media (prefers-reduced-motion: reduce)`.
4. **Définition des règles Responsive (`docs/04-ux-ui/responsive-guidelines.md`)** :
   - Fixe les breakpoints et les règles de transformation de la navigation, des grilles, des tableaux, des modales et des zones tactiles (`>= 44x44px`).
5. **Spécification granulaire de chaque écran (`docs/04-ux-ui/screens/screen-XXX.md`)** :
   - Pour chaque écran `SCR-001`... du Sitemap, applique le standard de `references/screen-specifications.md`.
   - Examine systématiquement la **grille de contrôle des 6 états** (`1. Initial`, `2. Chargement`, `3. Vide`, `4. Erreur`, `5. Succès`, `6. Désactivé`) et qualifie chacun d'eux en :
     - **`Applicable`** : spécifie en détail la présentation et le comportement.
     - **`Non applicable (N/A)`** : indique `N/A` avec une justification courte (ex. écran statique de présentation sans chargement dynamique ni formulaire).
     - **`À déterminer`** (`[POINT EN ATTENTE]`) : signale l'information manquante à clarifier.
   - Relie chaque écran à ses exigences (`FR-xxx`), règles métier (`BR-xxx`), références (`REF-xxx`) et critères d'acceptation (`AC-xxx` en Given/When/Then).

## 5. Arbitrages d'autonomie
- **Tu décides seul** : l'échelle mathématique des espacements et tailles typographiques, les valeurs de courbes d'animation, la qualification technique des états `Applicable` vs `N/A` évidents et l'organisation fine des composants.
- **Tu fais valider par l'utilisateur** : la direction artistique (thème, palette principale, tonalité visuelle), l'agencement des écrans majeurs et les états marqués `À déterminer`.

## 6. Critères de sortie (Passage à la Phase 5)
- [ ] La direction artistique est documentée et validée.
- [ ] Le Design System définit des tokens concrets (aucune description vague) et des composants `COMP-xxx` complets.
- [ ] Chaque écran du MVP (`SCR-001`...) possède sa fiche de spécification complète avec la grille des 6 états qualifiés (`Applicable` / `N/A` justifié / `À déterminer`) et ses critères `AC-xxx`.
- [ ] Le type de livrable (spécification textuelle vs livrable visuel) est clairement identifié sans ambiguïté.
