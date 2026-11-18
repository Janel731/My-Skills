# Design System & Bibliothèque de Composants — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/04-ux-ui/design-system.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Direction Artistique](./visual-direction.md) | [Règles Responsive](./responsive-guidelines.md) | [Écrans](./screens/screen-001.md)

## 1. Tokens de Couleurs Sémantiques (Conformité WCAG 2.1 AA)
| Token sémantique | Rôle dans l'interface | Valeur (Thème Clair) | Valeur (Thème Sombre) | Contraste vérifié |
| :--- | :--- | :--- | :--- | :--- |
| `surface-canvas` | Fond global de l'écran | `#FAFAFC` | `#090A0F` | — |
| `surface-card` | Fond des cartes et panneaux | `#FFFFFF` | `#12141C` | — |
| `surface-subtle` | Fond secondaire / lignes paires / code | `#F1F3F9` | `#1A1D28` | — |
| `text-primary` | Titres et texte principal | `#11131A` | `#F5F7FA` | `>= 14:1` (AAA) |
| `text-secondary` | Descriptions, labels, sous-titres | `#4A5060` | `#A6B0C3` | `>= 6.5:1` (AA) |
| `text-muted` | Métadonnées secondaires, aides | `#636B7E` | `#848FA5` | `>= 4.6:1` (AA) |
| `accent-primary` | Action primaire (CTA), focus actif | `[#HEX]` | `[#HEX]` | `>= 4.5:1` avec `text-on-accent` |
| `accent-hover` | Survol action primaire | `[#HEX]` | `[#HEX]` | — |
| `border-subtle` | Bordures de cartes et séparateurs `1px` | `#E2E6F0` | `#232736` | — |
| `border-focus` | Anneau de focus clavier `:focus-visible` | `[#HEX]` | `[#HEX]` | `>= 3:1` |
| `status-success` | Confirmation (Texte / Fond subtil / Bordure) | `#157347` / `#E8F5EE` | `#4DD499` / `#0F291E` | `>= 4.5:1` |
| `status-warning` | Avertissement (Texte / Fond subtil / Bordure) | `#996500` / `#FFF8E6` | `#FFC145` / `#2B210B` | `>= 4.5:1` |
| `status-danger` | Erreur & Destruction (Texte / Fond / Bordure) | `#C92A2A` / `#FFF0F0` | `#FF6B6B` / `#2D1215` | `>= 4.5:1` |
| `status-info` | Information (Texte / Fond subtil / Bordure) | `#1864AB` / `#E7F5FF` | `#66B2FF` / `#102338` | `>= 4.5:1` |

## 2. Typographie
- **Police de titres (`--font-heading`) :** `[Nom de la police, fallback]`
- **Police de corps et d'interface (`--font-sans`) :** `[Nom de la police, fallback]`
- **Police monospace / données chiffrées (`--font-mono`) :** `[Nom de la police]` + `font-variant-numeric: tabular-nums` sur tous les montants, compteurs et colonnes numériques.

| Token | Élément HTML | Taille (`rem` / `px`) | Graisse | Interlignage (`line-height`) | Tracking | Usage |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `display-lg` | `h1.display` | `2.25rem` (`36px`) | `700` | `1.15` | `-0.02em` | Titre héro |
| `heading-1` | `h1` | `1.75rem` (`28px`) | `700` | `1.2` | `-0.015em` | Titre principal d'écran |
| `heading-2` | `h2` | `1.375rem` (`22px`) | `600` | `1.25` | `-0.01em` | Titre de section |
| `heading-3` | `h3` | `1.125rem` (`18px`) | `600` | `1.35` | `0` | Titre de carte / modale |
| `body-md` | `p`, `input`, `button` | `1rem` (`16px`) | `400` / `500` | `1.5` | `0` | Corps standard & champs |
| `body-sm` | `span`, `td` | `0.875rem` (`14px`) | `400` / `500` | `1.45` | `0` | Tableaux, listes denses |
| `caption` | `small` | `0.75rem` (`12px`) | `500` | `1.35` | `+0.02em` | Badges, horodatages |

## 3. Échelle d'Espacement, Grilles, Rayons et Ombres
- **Unité de base :** `4px` (`space-1: 4px`, `space-2: 8px`, `space-3: 12px`, `space-4: 16px`, `space-6: 24px`, `space-8: 32px`, `space-12: 48px`, `space-16: 64px`).
- **Rayons (`border-radius`) :** `radius-sm: 6px` (badges, petits contrôles), `radius-md: 8px` (boutons, champs), `radius-lg: 12px` (cartes, modales), `radius-full: 9999px` (pills, avatars).
- **Élévations (`box-shadow`) et `z-index` :**
  - `elevation-0` : Aucune ombre, bordure `1px solid var(--border-subtle)`.
  - `elevation-1` (Cartes survolées / Dropdowns) : `0 4px 12px rgba(0, 0, 0, 0.06)`.
  - `elevation-2` (Modales / Drawers / Toasts) : `0 16px 32px rgba(0, 0, 0, 0.14)`.
  - Échelle `z-index` : `base: 1`, `sticky-header: 20`, `dropdown: 30`, `drawer: 40`, `modal: 50`, `toast: 60`, `tooltip: 70`.

## 4. Catalogue des Composants (`COMP-xxx`) et États interactifs

### `COMP-001` — Bouton d'action (`Button`)
- **Variantes :** `primary`, `secondary`, `outline`, `ghost`, `destructive`.
- **Tailles :** `sm` (hauteur `32px`, padding `0 12px`), `md` (hauteur `40px`, padding `0 16px`), `lg` (hauteur `48px`, padding `0 24px`, tactile mobile).
- **États obligatoires :**
  - `default` : Couleur nominale de la variante.
  - `hover` : Transition `150ms ease-out` vers la teinte `*-hover`.
  - `focus-visible` : Outline `2px solid var(--border-focus)` avec `outline-offset: 2px`.
  - `active` : Légère translation `translateY(1px)` ou teinte active.
  - `disabled` : Opacité `0.45`, `cursor: not-allowed`, `aria-disabled="true"`.
  - `loading` : Largeur préservée, icône spinner `16px` + texte explicite (ex. « Enregistrement... »), clics supplémentaires bloqués.

### `COMP-002` — Champ de formulaire (`Input / Select / Textarea`)
- **Anatomie :** `<label>` explicite au-dessus (`margin-bottom: 6px`), conteneur champ (hauteur `40px` desktop / `44px` mobile, police `16px` min sur mobile), texte d'aide ou message d'erreur sous le champ (`min-height: 20px`).
- **États :** `default`, `hover`, `focus` (bordure `accent-primary` + anneau doux), `disabled` / `read-only`, `error` (bordure `status-danger`, icône d'alerte + message d'erreur relié par `aria-describedby`), `valid`.

### `COMP-003` — Carte / Conteneur métier (`Card`)
- [Spécifier anatomie, paddings, variantes interactive vs statique, état `skeleton` de chargement.]

### `COMP-004` — Tableau de données / Liste (`DataTable / List`)
- [Spécifier en-tête, alignement texte à gauche / nombres à droite en `tabular-nums`, tri, pagination, état vide, repli responsive mobile.]

### `COMP-005` — Modale, Tiroir et Notification (`Modal / Drawer / Toast`)
- [Spécifier focus trap clavier, fermeture `Escape`, confirmation d'action destructrice, durée d'affichage des toasts `aria-live="polite"`.]

## 5. Micro-interactions, Animations et Accessibilité du mouvement
- **Transitions standards :** `150ms ease-out` (contrôles UI), `240ms cubic-bezier(0.16, 1, 0.3, 1)` (panneaux et modales).
- **Respect de `prefers-reduced-motion: reduce` :** Désactivation de toutes les translations spatiales et remplacement par un changement d'opacité instantané (`< 50ms`).
