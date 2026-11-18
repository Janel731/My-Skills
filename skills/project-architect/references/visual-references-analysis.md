# Analyse des Références Visuelles (UX/UI & Direction Artistique)

## 1. Objectif et périmètre

Ce guide définit comment l'agent analyse, décompose et exploite les références visuelles fournies par l'utilisateur lors de la **Phase 2 (Research)** et de la **Phase 4 (UX/UI Design)**.

Le skill sait travailler à partir de six types de sources :

1. **Captures d'écran** (applications web, mobiles, desktop, dashboards).
2. **Sites web ou produits de référence** (URLs ou descriptions détaillées).
3. **Maquettes et wireframes** (exports Figma, Sketch, Penpot, croquis).
4. **Images d'inspiration et moodboards** (photographies, affiches, identités de marque, palettes).
5. **Interfaces existantes du projet** (legacy à refondre ou faire évoluer).
6. **Exemples d'interactions et d'animations** (descriptions de transitions, vidéos, extraits de mouvement).

## 2. Règles d'intégrité et d'honnêteté visuelle

- **Ne jamais inventer ce qui n'est pas visible** : Si une capture est tronquée, floue, statique ou ne montre qu'un seul écran, n'invente ni les animations, ni le comportement mobile, ni les états d'erreur absents de l'image. Marque-les comme `[HYPOTHESE]` ou `[POINT EN ATTENTE]`.
- **Signaler les limites d'accès aux URLs** : Si l'utilisateur fournit une URL de site web et que l'outil de lecture disponible n'extrait que le texte HTML sans rendu visuel CSS/JS, signale explicitement cette limite technique et demande une capture d'écran pour analyser la direction artistique réelle.
- **Ne jamais copier aveuglément** : Une référence visuelle a été conçue pour un contexte, une marque et des utilisateurs spécifiques. Tu dois extraire ses principes structurels et esthétiques pour les transposer au besoin réel du projet, sans cloner les marques, textes protégés ou défauts d'accessibilité de la source.

## 3. Grille d'analyse en 12 dimensions

Pour chaque référence pertinente (`REF-001`, `REF-002`...), analyse systématiquement les 12 dimensions suivantes :

### 3.1. Structure et composition
- Organisation macro de la page ou de l'écran (layout en F, en Z, split-screen, bento grid, sidebar + canvas, plein écran immersif).
- Rapport plein / vide (densité d'information vs respiration visuelle / whitespace).
- Équilibre des masses visuelles et points d'ancrage.

### 3.2. Hiérarchie visuelle
- Niveau 1 (ce que l'œil capte en moins d'une seconde : titre héro, indicateur clé, action primaire).
- Niveau 2 (blocs fonctionnels, cartes, navigation).
- Niveau 3 (métadonnées, labels secondaires, notes de bas de page).
- Procédés utilisés pour créer la hiérarchie : taille, graisse, contraste chromatique, encadrement, élévation.

### 3.3. Typographie
- Familles typographiques observées ou équivalentes (Sans-serif géométrique, néo-grotesque, humaniste, Serif éditoriale, Monospace technique).
- Contraste entre titres (Display / Headings) et corps de texte (Body / UI).
- Échelle de tailles, graisses, hauteur de ligne (line-height), espacement des lettres (tracking) et largeur de colonne (mesure de 55 à 75 caractères).

### 3.4. Couleurs
- Thème dominant : clair (Light), sombre (Dark), mixte ou adaptatif.
- Couleurs de fond (surfaces primaires, secondaires, cartes, modales).
- Couleurs de texte (primaire, secondaire, atténué/muted).
- Couleur(s) d'accentuation et d'action primaire (Brand / Primary CTA).
- Couleurs sémantiques observables (succès, avertissement, erreur, information) et qualité du contraste.

### 3.5. Espacements
- Rythme vertical et horizontal (compact / dense pour un outil métier expert vs aéré / éditorial pour une landing page).
- Marges internes (padding) des conteneurs et cartes.
- Écarts (gaps) entre éléments frères et entre grandes sections.

### 3.6. Grilles et proportions
- Nombre de colonnes observables (ex. grille 12 colonnes desktop, 4 colonnes mobile, ou layout modulaire asymétrique).
- Largeur maximale du conteneur principal (`max-width`) et gouttières.
- Proportions des cartes, ratios d'images (`16:9`, `4:3`, `1:1`, `4:5`).

### 3.7. Composants
- Inventaire des composants visibles : boutons, champs de saisie, cartes, tableaux, onglets, badges, modales, toasts, listes, graphiques.
- Style des bordures (épaisseur `1px`, couleur subtile), rayons de courbure (`border-radius` : anguleux `0px`, subtil `4-6px`, arrondi `8-12px`, pilule `9999px`) et ombres/élévation (flat, bordures fines, ombres diffuses, glassmorphism).

### 3.8. Navigation
- Modèle de navigation primaire (barre supérieure fixe, barre latérale repliable, barre d'onglets inférieure mobile, command palette `Cmd+K`, fil d'Ariane).
- Profondeur de navigation et repères d'état actif.

### 3.9. Interactions
- Affordance des éléments cliquables ou manipulables.
- Modes de saisie, filtres, recherche, tri, actions contextuelles (menus, survol, glisser-déposer).
- Charge cognitive demandée à l'utilisateur pour accomplir l'action principale.

### 3.10. Animations et micro-interactions
- Transitions d'entrée et de sortie (apparition progressive, translation douce, changement d'état de bouton).
- Feedback immédiat lors des actions utilisateur (hover, focus, active, loading spinner ou skeleton).
- Règle d'or : vérifier que les animations servent la compréhension (orientation spatiale, continuité) sans bloquer le défilement ni ralentir l'action.

### 3.11. Comportement responsive
- Adaptation observée ou déduite entre grand écran, ordinateur portable, tablette et smartphone.
- Repli des colonnes, transformation de la navigation, taille des cibles tactiles (`>= 44x44px`).

### 3.12. Ambiance et direction artistique
- Registre émotionnel et professionnel : minimaliste technique, éditorial premium, chaleureux et grand public, industriel sobre, ludique, institutionnel.
- Cohérence entre le ton visuel et la proposition de valeur du produit cible.

## 4. Matrice de décision obligatoire en 4 catégories

Toute analyse de références visuelles doit aboutir à un arbitrage structuré en 4 catégories explicites dans `docs/02-research/references-analysis.md` :

| Catégorie | Définition | Exemple concret |
| :--- | :--- | :--- |
| **1. Éléments à reproduire** | Principes, structures ou choix visuels de la référence directement alignés avec les besoins et objectifs du projet. | « Conserver la disposition en 3 colonnes du tableau de bord et le contraste élevé des cartes sur fond `#FAFAFC`. » |
| **2. Éléments à adapter** | Bonnes idées de la référence qui doivent être modifiées pour correspondre au contenu, à la cible ou aux contraintes techniques du projet. | « Adapter la barre latérale de 12 entrées de la référence en une navigation simplifiée à 4 entrées pour notre MVP. » |
| **3. Éléments à éviter** | Défauts d'ergonomie, surcharges visuelles, problèmes d'accessibilité ou fonctionnalités hors périmètre présents dans la référence. | « Éviter le texte gris clair sur fond blanc (contraste insuffisant < 3:1) et le carrousel bloquant le scroll vertical. » |
| **4. Éléments à clarifier** | Aspects ambigus de la référence ou arbitrages de goût qui nécessitent une validation explicite de l'utilisateur. | « Clarifier si vous souhaitez retenir de cette capture uniquement la palette sombre ou également la densité de données type terminal financier. » |

## 5. Procédure en l'absence de référence visuelle

Si l'utilisateur ne fournit aucune référence visuelle :

1. **Ne laisse jamais un vide artistique** : Analyse le domaine métier, les personas, le contexte d'usage (ex. usage mobile en extérieur vs usage desktop prolongé en bureau sombre) et le positionnement du produit.
2. **Propose 2 directions artistiques contrastées et argumentées** (ou une direction principale recommandée + une alternative crédible), chacune précisant :
   - Le positionnement et l'ambiance.
   - Le thème chromatique (clair, sombre ou adaptatif) avec codes hexadécimaux concrets.
   - Le duo typographique proposé.
   - Le style des composants (densité, rayons, bordures, ombres).
3. **Soumets ce choix comme `[DECISION PROPOSEE]`** et fais valider la direction retenue avant de rédiger l'intégralité des spécifications d'écrans.
