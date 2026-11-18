# Règles Responsive & Adaptation Multi-Supports — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/04-ux-ui/responsive-guidelines.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Design System](./design-system.md) | [Sitemap](../03-product-design/sitemap.md) | [Écrans](./screens/screen-001.md)

## 1. Grille et Breakpoints officiels
| Nom du Breakpoint | Plage de largeur (`px`) | Colonnes | Gouttière (`gap`) | Marges latérales | Largeur max du conteneur |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Mobile (`xs` / `sm`)** | `320px – 639px` | 4 colonnes | `12px` | `16px` | `100%` |
| **Tablette (`md`)** | `640px – 1023px` | 8 colonnes | `16px` | `24px` | `100%` |
| **Desktop (`lg`)** | `1024px – 1279px` | 12 colonnes | `24px` | `32px` | `1200px` |
| **Large Desktop (`xl`)** | `>= 1280px` | 12 colonnes | `24px` | `40px` | `1360px` |

## 2. Transformations des patrons d'interface par Breakpoint

### 2.1. Navigation globale et contextuelle
- **Desktop (`>= 1024px`) :** [Ex. Barre latérale fixe de `240px` à gauche + barre supérieure d'actions contextuelles.]
- **Tablette (`640px – 1023px`) :** [Ex. Barre latérale repliée en mode icônes (`64px`) ou tiroir ouvrable.]
- **Mobile (`< 640px`) :** [Ex. Barre de navigation inférieure fixe à 4 entrées principales (`height: 64px` + `env(safe-area-inset-bottom)`) ou menu tiroir accessible au pouce.]

### 2.2. Tableaux, listes et cartes de données
- **Desktop :** Tableau multi-colonnes complet avec actions rapides en fin de ligne.
- **Tablette :** Masquage des colonnes de priorité 3, conservation des colonnes de priorité 1 et 2.
- **Mobile :** Transformation de chaque ligne en carte verticale compacte regroupant : Identifiant/Titre + Statut en haut, Montant/Valeur clé à droite, et action au tap sur la carte (aucun scroll horizontal forcé sur l'écran global).

### 2.3. Formulaires, Modales et Panneaux de détail
- **Formulaires :** Passage des grilles 2 colonnes (Desktop) à 1 colonne unique pleine largeur sur Mobile ; boutons de soumission fixés en bas de vue ou pleine largeur (`100%`) sur Mobile.
- **Modales (`COMP-005`) :** Modale centrée (`max-width: 520px`) sur Desktop -> *Bottom Sheet* ancrée en bas d'écran sur Mobile.

## 3. Ergonomie tactile et contraintes matérielles
- **Cibles tactiles minimales :** `44x44px` minimum sur Mobile et Tablette avec un écart d'au moins `8px` entre deux actions voisines.
- **Saisie mobile sans zoom intempestif :** Police d'au moins `16px` (`1rem`) sur tous les champs `<input>`, `<select>` et `<textarea>` + attributs `inputmode` (`numeric`, `email`, `tel`, `search`) et `autocomplete` appropriés.
- **Images et médias :** Ratios préservés (`aspect-ratio`), chargement différé (`loading="lazy"`) hors de la ligne de flottaison.
