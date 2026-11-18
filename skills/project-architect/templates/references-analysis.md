# Analyse des Références Visuelles et Ergonomiques — [Nom du Projet]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/02-research/references-analysis.md`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Rapport de recherche](./research-report.md) | [Direction Artistique](../04-ux-ui/visual-direction.md) | [Design System](../04-ux-ui/design-system.md)

## 1. Inventaire des références analysées
| ID | Nom / Source de la référence | Type (Capture, Site, Maquette, Animation, Legacy) | Mode d'inspection (Image inspectée / URL / Description) | Rôle de cette référence |
| :--- | :--- | :--- | :--- | :--- |
| `REF-001` | [Nom ou fichier] | [Ex. Capture d'écran dashboard] | [Inspection visuelle directe] | [Inspiration structure & couleurs] |

## 2. Analyse détaillée par référence (Grille des 12 dimensions)

### `REF-001` — [Nom de la référence]
1. **Structure et composition :** [Layout macro, rapport plein/vide, équilibre des zones.]
2. **Hiérarchie visuelle :** [Focal point de niveau 1, blocs de niveau 2, métadonnées de niveau 3.]
3. **Typographie :** [Familles de polices observées, contraste titres/corps, tailles, graisses, lisibilité.]
4. **Couleurs :** [Thème clair/sombre, surfaces, texte, couleur d'accent, états sémantiques, qualité du contraste.]
5. **Espacements :** [Densité générale, paddings internes des cartes, écarts inter-sections.]
6. **Grilles et proportions :** [Colonnes, largeur max, ratios des cartes et médias.]
7. **Composants :** [Boutons, champs, cartes, tableaux, badges, rayons `border-radius`, bordures, ombres.]
8. **Navigation :** [Position, profondeur, repères d'état actif.]
9. **Interactions :** [Affordance, filtres, actions contextuelles, charge cognitive.]
10. **Animations et transitions :** [Micro-interactions observées ou `Non visible sur capture statique`.]
11. **Comportement responsive :** [Adaptation mobile/tablette observée ou `Non visible sur capture desktop unique`.]
12. **Ambiance et direction artistique :** [Registre émotionnel et adéquation avec notre cible.]

## 3. Matrice d'arbitrage UX/UI obligatoire (Synthèse croisée)

### 3.1. Éléments à reproduire (Adoptés directement)
| Élément / Principe | Référence source | Justification pour notre projet | Application cible (`design-system.md` / `SCR-xxx`) |
| :--- | :--- | :--- | :--- |
| [Ex. Hiérarchie tabulaire épurée et fond `#FAFAFC`] | `REF-001` | [Maximise la lisibilité lors d'un usage quotidien prolongé] | `design-system.md`, `SCR-002` |

### 3.2. Éléments à adapter (Transposés à notre contexte)
| Élément d'origine | Référence source | Adaptation décidée ou proposée | Raison de l'adaptation |
| :--- | :--- | :--- | :--- |
| [Ex. Navigation latérale à 14 entrées] | `REF-001` | [Réduction à 5 entrées principales + profil] | [Périmètre MVP plus ciblé] |

### 3.3. Éléments à éviter (Écartés volontairement)
| Élément écarté | Référence source | Risque ou défaut identifié (UX, accessibilité, technique) |
| :--- | :--- | :--- |
| [Ex. Texte gris clair `#A0A0A8` sur fond blanc] | `REF-001` | [Contraste `< 2.6:1` non conforme WCAG AA] |

### 3.4. Éléments nécessitant une clarification (`[POINT EN ATTENTE]`)
| ID | Question sur la référence | Options possibles | Impact sur le Design System ou les écrans |
| :--- | :--- | :--- | :--- |
| `Q-VIS-01` | [Question ciblée] | [Option A vs Option B] | [Impact] |
