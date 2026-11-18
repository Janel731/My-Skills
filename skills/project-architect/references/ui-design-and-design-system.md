# UI Design, Direction Artistique & Design System

## 1. Objectif

Ce document guide la **Phase 4 (UX/UI Design)** pour transformer l'architecture de l'information et l'analyse des références visuelles en une **direction artistique cohérente** et un **Design System complet, précis et directement implémentable** par un développeur frontend ou un UI Designer.

**Interdiction absolue** : Ne jamais produire de recommandations génériques et vides telles que *« utiliser une palette moderne, une police lisible et un design épuré »*. Chaque choix doit être spécifié avec des valeurs concrètes (tokens, codes couleurs, tailles en `px`/`rem`, règles de grille, états interactifs).

## 2. Direction Artistique (`docs/04-ux-ui/visual-direction.md`)

La direction artistique définit l'identité visuelle et sensorielle du produit :

1. **Positionnement esthétique et tonalité** :
   - 3 à 5 adjectifs directeurs justifiés par la cible et le domaine (ex. *Éditorial, Précis, Apaisant, Haute lisibilité* — et ce qu'ils excluent : *Pas clinquant, pas ludique/enfantin, pas surchargé*).
2. **Principes directeurs de l'interface** :
   - Densité d'information cible (ex. haute densité tabulaire pour un back-office comptable vs respiration généreuse pour une application de bien-être).
   - Traitement de la profondeur (aplat minimaliste avec bordures `1px`, élévation par ombres portées douces, surfaces translucides contrôlées).
3. **Synthèse des références visuelles appliquées** :
   - Rappel explicite des éléments retenus et adaptés depuis `docs/02-research/references-analysis.md`.

## 3. Architecture du Design System (`docs/04-ux-ui/design-system.md`)

Structure le Design System autour de **Design Tokens sémantiques** afin que les composants ne référencent jamais des valeurs brutes arbitraires.

### 3.1. Palette de couleurs et tokens chromatiques

Spécifie chaque couleur avec son rôle sémantique, son code hexadécimal (pour le thème clair et/ou sombre retenu) et son ratio de contraste WCAG :

- **Surfaces / Backgrounds** :
  - `bg-canvas` / `surface-primary` (fond principal de l'application).
  - `bg-elevated` / `surface-secondary` (cartes, panneaux latéraux, en-têtes).
  - `bg-overlay` / `surface-modal` (modales, menus déroulants, tooltips).
  - `bg-subtle` / `surface-muted` (zones désactivées, arrière-plans de tableaux zébrés ou blocs de code).
- **Textes et icônes** :
  - `text-primary` (titres et corps principal, contraste `>= 7:1` ou `>= 4.5:1`).
  - `text-secondary` (sous-titres, descriptions secondaires, contraste `>= 4.5:1`).
  - `text-muted` (placeholders, légendes non critiques, contraste `>= 4.5:1` si informatif).
  - `text-on-accent` (texte affiché sur un bouton d'action primaire).
- **Marque et Actions (Brand & Accent)** :
  - `accent-primary`, `accent-primary-hover`, `accent-primary-active`, `accent-primary-subtle`.
  - `accent-secondary` (si pertinent).
- **Bordures et séparateurs** :
  - `border-subtle` (séparations courantes), `border-strong` (champs actifs/encadrés), `border-focus` (anneau de focus clavier).
- **Couleurs sémantiques d'état** (chaque état comprend une variante `text`, `bg-subtle` et `border`) :
  - `status-success` (confirmation, validation).
  - `status-warning` (attention, action risquée non bloquante).
  - `status-danger` / `error` (erreur, action destructrice).
  - `status-info` (information neutre, aide contextuelle).

### 3.2. Typographie

Définis précisément :
- **Familles de polices** :
  - `--font-heading` (titres, si différente du corps).
  - `--font-sans` / `--font-body` (interface et lecture courante).
  - `--font-mono` (code, identifiants, montants tabulaires — ou activation de `font-variant-numeric: tabular-nums` pour les chiffres alignés en colonne).
- **Échelle typographique complète** :

| Token | Usage | Taille (`rem` / `px`) | Graisse (`font-weight`) | Hauteur de ligne (`line-height`) | Espacement (`letter-spacing`) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `display-lg` | Titre héro / Marketing | ex. `2.5rem` (`40px`) | `700` | `1.15` | `-0.02em` |
| `heading-1` | Titre d'écran (`h1`) | ex. `1.875rem` (`30px`) | `700` | `1.2` | `-0.015em` |
| `heading-2` | Titre de section (`h2`) | ex. `1.5rem` (`24px`) | `600` | `1.25` | `-0.01em` |
| `heading-3` | Titre de carte / sous-section (`h3`) | ex. `1.25rem` (`20px`) | `600` | `1.3` | `0` |
| `body-lg` | Introduction / texte mis en avant | ex. `1.125rem` (`18px`) | `400` | `1.6` | `0` |
| `body-md` | Texte courant et contrôles UI | ex. `1rem` (`16px`) | `400` | `1.5` | `0` |
| `body-sm` | Texte secondaire, cellules de tableau | ex. `0.875rem` (`14px`) | `400` / `500` | `1.45` | `0` |
| `caption` | Badges, métadonnées, légendes | ex. `0.75rem` (`12px`) | `500` | `1.35` | `+0.02em` |

### 3.3. Échelle d'espacement (Spacing Scale)

Utilise une base régulière (système `4px` / `8px`) pour garantir l'harmonie spatiale :
- `space-1` = `4px` (`0.25rem`) — espacement interne minimal (icône + label).
- `space-2` = `8px` (`0.5rem`) — espacement entre éléments proches.
- `space-3` = `12px` (`0.75rem`) — padding vertical de champs/boutons.
- `space-4` = `16px` (`1rem`) — padding interne standard de carte mobile, écart entre champs.
- `space-6` = `24px` (`1.5rem`) — padding interne de carte desktop, écart entre blocs.
- `space-8` = `32px` (`2rem`) — séparation entre sous-sections.
- `space-12` = `48px` (`3rem`) — séparation majeure entre sections d'écran.
- `space-16` = `64px` (`4rem`) — respiration macro sur grands écrans.

### 3.4. Grilles, Rayons, Ombres et Iconographie

- **Grilles et conteneurs** : largeur maximale (`max-width`, ex. `1280px` ou `1440px`), nombre de colonnes par breakpoint (ex. 12 desktop, 8 tablette, 4 mobile), taille des gouttières (`16px` mobile, `24px` desktop) et marges latérales de sécurité.
- **Rayons de bordure (`border-radius`)** : `radius-sm` (`4px`), `radius-md` (`8px`), `radius-lg` (`12px`), `radius-xl` (`16px`), `radius-full` (`9999px`).
- **Ombres et élévation (`box-shadow` & `z-index`)** : définir les niveaux d'élévation (`elevation-0` à `elevation-3`) et l'échelle de `z-index` (base, header collant, tiroir, modale, toast, tooltip) pour éviter tout conflit de superposition.
- **Iconographie** : bibliothèque ou style retenu (ex. icônes vectorielles filaires `stroke-width: 1.75px` type Lucide/Phosphor, tailles `16px`, `20px`, `24px`), alignement optique avec le texte, interdiction de mélanger des styles disparates ou d'utiliser des emojis à la place d'icônes fonctionnelles dans une interface professionnelle.

## 4. Composants (`COMP-xxx`), Variantes et États interactifs

Pour chaque composant réutilisable du Design System (`COMP-001` Bouton, `COMP-002` Champ de saisie, `COMP-003` Carte, `COMP-004` Tableau/Liste, `COMP-005` Modale/Tiroir, `COMP-006` Toast/Alerte, plus les composants métiers spécifiques au projet), documente :

1. **Identifiant, nom et rôle**.
2. **Anatomie** : sous-éléments constitutifs (conteneur, icône gauche, label, badge, action secondaire).
3. **Variantes** :
   - Hiérarchie : `primary`, `secondary`, `outline`, `ghost`, `destructive`.
   - Tailles : `sm`, `md`, `lg` (avec hauteurs exactes en `px`).
4. **Les 8 états interactifs d'un composant** :
   - `default` (repos).
   - `hover` (survol pointeur).
   - `focus-visible` (navigation clavier — anneau de focus net et contrasté).
   - `active` / `pressed` (clic ou pression tactile).
   - `disabled` (inactif — opacité ou teinte dédiée, curseur `not-allowed`, raison compréhensible).
   - `loading` (action en cours — spinner intégré ou skeleton, prévention du double-clic).
   - `error` / `invalid` (bordure `status-danger`, icône et message d'aide explicite sous le champ).
   - `selected` / `checked` (état coché ou onglet actif).

## 5. Responsive Design (`docs/04-ux-ui/responsive-guidelines.md`)

Spécifie la stratégie d'adaptation multi-écrans :
- **Breakpoints explicites** : ex. Mobile (`< 640px`), Tablette (`640px – 1023px`), Desktop (`1024px – 1279px`), Large Desktop (`>= 1280px`).
- **Transformations structurelles par breakpoint** :
  - Navigation (ex. sidebar latérale fixe sur Desktop -> drawer ou bottom tab bar sur Mobile).
  - Tableaux de données (ex. tableau complet sur Desktop -> colonnes prioritaires + détail dépliable ou vue cartes sur Mobile).
  - Modales et panneaux (ex. modale centrée sur Desktop -> bottom sheet plein écran sur Mobile).
  - Typographie et espacements (réduction maîtrisée des titres et paddings sur petit écran sans jamais descendre sous `14px` pour le texte de lecture ni sous `16px` pour les champs `<input>` sur mobile afin d'éviter le zoom automatique iOS).

## 6. Micro-interactions, Animations et Transitions

Documente des règles de mouvement utiles, sobres et performantes :
- **Durées et courbes d'accélération (Easing)** :
  - Micro-feedback (hover, focus, toggle) : `120ms – 180ms`, `ease-out`.
  - Ouverture de menu, popover, toast : `180ms – 240ms`, `cubic-bezier(0.16, 1, 0.3, 1)`.
  - Transition de panneau latéral ou modale : `250ms – 320ms`.
- **Propriétés animées** : Privilégier `transform` et `opacity` (accélérées matériellement) ; éviter d'animer `width`, `height` ou `top/left` qui provoquent des recalculs de layout (reflow).
- **Intégrité du scroll et accessibilité** :
  - Ne jamais détourner ou bloquer le défilement naturel de l'utilisateur (*scroll-jacking* interdit sauf demande explicite validée).
  - Toujours définir le comportement de repli `@media (prefers-reduced-motion: reduce)` : suppression des translations amples et remplacement par un fondu instantané ou très court (`< 50ms`).

## 7. Distinction entre Spécifications UX/UI et Livrables Visuels

Dans tous les travaux de la Phase 4, respecte strictement la différence entre :
- **La spécification d'interface** : documentation textuelle structurée (`visual-direction.md`, `design-system.md`, `responsive-guidelines.md`, `screens/screen-XXX.md`) décrivant tokens, règles, composants, états et comportements.
- **Le livrable visuel** : représentation graphique ou interactive (wireframe basse fidélité, maquette haute fidélité, diagramme de parcours, prototype interactif, illustration ou prompt détaillé pour un outil de design).

Applique en permanence ces 6 règles :
1. Ne prétends jamais qu'une maquette graphique existe lorsqu'elle n'a pas été réellement produite.
2. Ne confonds jamais une description textuelle avec un prototype interactif.
3. Identifie clairement la nature exacte du livrable fourni.
4. Si la plateforme ne permet pas de générer des visuels graphiques, fournis une spécification textuelle exhaustive et signale explicitement la limite.
5. N'impose aucun outil de design particulier (Figma, Penpot, Sketch, etc.).
6. Respecte scrupuleusement les références visuelles fournies par le porteur de projet.
