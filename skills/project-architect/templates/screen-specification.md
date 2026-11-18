# Spécification d'Écran : `SCR-001` — [Nom de l'Écran]

- **Projet :** [Nom du Projet]
- **Chemin :** `docs/04-ux-ui/screens/screen-001.md`
- **Identifiant Écran :** `SCR-001`
- **Type de livrable :** Spécification textuelle d'interface (distincte d'une maquette graphique ou d'un prototype interactif)
- **Route / Emplacement :** `[/route-exacte ou emplacement navigation]`
- **Statut :** `DRAFT` | `REVIEW` | `APPROVED` | `SUPERSEDED`
- **Version :** [0.1]
- **Date :** [YYYY-MM-DD]
- **Documents liés :** [Sitemap](../../03-product-design/sitemap.md) | [Design System](../design-system.md) | [Exigences](../../03-product-design/requirements.md) | [API](../../05-architecture/api-specification.md)

## 1. Objectif de l'écran
- **Finalité utilisateur :** [Ce que l'utilisateur comprend et accomplit sur cet écran.]
- **Action principale (Primary CTA) :** [L'action prioritaire mise en avant, ou `N/A` s'il s'agit d'un écran purement informatif.]

## 2. Utilisateurs concernés et Permissions
- **Acteurs & Personas autorisés :** `ACT-001` (`PER-001`)
- **Règles d'accès et de redirection :** [Comportement si non connecté ou si rôle insuffisant.]

## 3. Structure spatiale et découpage en zones (Layout)
```text
+-------------------------------------------------------------------+
| Zone A : En-tête d'écran (Titre h1, navigation, action primaire)  |
+-------------------------------------------------+-----------------+
| Zone B : Zone principale                        | Zone C : Panneau|
| (Contenu / Liste / Formulaire / Visualisation)  | secondaire      |
+-------------------------------------------------+-----------------+
```
- **Zone A — En-tête :** [Contenu et comportement au défilement.]
- **Zone B — Zone principale :** [Organisation, grille, largeur.]
- **Zone C — Zone secondaire / Filtres :** [Organisation ou `N/A` si écran à zone unique.]

## 4. Hiérarchie visuelle des éléments
1. **Niveau 1 (Point focal immédiat) :** [...]
2. **Niveau 2 (Contenu et contrôles primaires) :** [...]
3. **Niveau 3 (Métadonnées et actions secondaires) :** [...]

## 5. Composants du Design System mobilisés (`COMP-xxx`)
| Zone | Composant (`COMP-xxx`) | Variante & Taille | Rôle dans l'écran |
| :--- | :--- | :--- | :--- |
| Zone A | `COMP-001` (Button) | `primary`, `md` | Déclencher l'action principale |
| Zone B | `COMP-003` (Card) / `COMP-004` | `default` | Présenter les éléments métiers |

## 6. Contenus et données affichées / saisies
| Élément / Champ | Libellé exact affiché | Type & Format | Source (`ENT-xxx` / `API-xxx` / Statique) | Validation / Règle d'affichage |
| :--- | :--- | :--- | :--- | :--- |
| [Champ 1] | « [Libellé exact] » | [Texte / Montant / Date] | `ENT-001.field` via `API-001` (ou `Contenu statique`) | [Obligatoire, max 120 car., troncature...] |

## 7. Actions utilisateur et appels API
| Action utilisateur | Élément déclencheur | Précondition / Validation client | Endpoint appelé (`API-xxx` ou `N/A`) | Résultat attendu |
| :--- | :--- | :--- | :--- | :--- |
| [Action 1] | Clic `COMP-001` | [Champs requis valides] | `POST /api/...` (`API-001`) | [Confirmation + navigation vers `SCR-002`] |

## 8. Interactions et micro-interactions
- **Recherche / Filtrage / Tri / Navigation :** [Comportement, debounce, synchronisation URL, ou `N/A`.]
- **Transitions et feedback :** [Animations d'ouverture, retour visuel immédiat, respect de `prefers-reduced-motion`.]

## 9. Examen de la grille des 6 États de l'écran

> **Règle d'application :** Les 6 catégories ci-dessous constituent la grille de contrôle systématique. Pour chaque état, qualifier explicitement s'il est **Applicable** (et détailler alors sa présentation et son comportement), **Non applicable (`N/A`)** (en justifiant pourquoi, par ex. pour un écran statique sans chargement ni saisie) ou **À déterminer (`[POINT EN ATTENTE]`)** (en indiquant l'information manquante).

### 9.1. Grille de qualification des états de `SCR-001`
| Catégorie d'état | Qualification (`Applicable` / `N/A` / `À déterminer`) | Justification ou déclencheur |
| :--- | :--- | :--- |
| **1. Initial (Nominal)** | `Applicable` | État de référence à l'ouverture de l'écran |
| **2. Chargement (Loading)** | `Applicable` \| `N/A` \| `À déterminer` | [Ex. Requête asynchrone `API-001` / ou `N/A : contenu statique pré-rendu`] |
| **3. Vide (Empty State)** | `Applicable` \| `N/A` \| `À déterminer` | [Ex. Collection pouvant contenir 0 élément / ou `N/A : écran de formulaire ou page statique`] |
| **4. Erreur (Error State)** | `Applicable` \| `N/A` \| `À déterminer` | [Ex. Échec réseau ou erreur de validation de saisie / ou `N/A : aucune saisie ni appel distant`] |
| **5. Succès (Success State)** | `Applicable` \| `N/A` \| `À déterminer` | [Ex. Confirmation de création ou sauvegarde / ou `N/A : écran de simple consultation`] |
| **6. Désactivé / Lecture seule** | `Applicable` \| `N/A` \| `À déterminer` | [Ex. Contrôle désactivé ou profil lecteur seul / ou `N/A : écran public sans contrôle verrouillable`] |

### 9.2. Spécification détaillée des états applicables
*(Ne détailler ci-dessous que les états qualifiés `Applicable` dans la grille 9.1 ; conserver la mention `N/A — [Justification]` ou `[POINT EN ATTENTE]` pour les autres.)*

- **1. État Initial (Nominal) :**
  - [Données affichées, tri/filtre par défaut, position initiale du focus.]
- **2. État Chargement (Loading) :**
  - [`Applicable` : Squelettes (*skeletons*) respectant les dimensions finales (CLS = 0) ou bouton en état `loading` bloquant les doubles soumissions. / Ou `N/A — Justification`.]
- **3. État Vide (Empty State) :**
  - [`Applicable` : Distinguer si pertinent **a) Aucune donnée existante** (message accueillant + CTA primaire) et **b) Aucun résultat de filtre** (message + bouton « Réinitialiser les filtres »). / Ou `N/A — Justification`.]
- **4. État Erreur (Error State) :**
  - [`Applicable` : Distinguer si pertinent **a) Erreur réseau/serveur** (message clair + bouton « Réessayer ») et **b) Erreur de validation de saisie** (message sous le champ fautif relié via `aria-describedby`, focus sur le 1er champ en erreur et conservation intégrale des valeurs saisies). / Ou `N/A — Justification`.]
- **5. État Succès (Success State) :**
  - [`Applicable` : Retour visuel confirmant l'action (toast `status-success`, mise à jour de la vue ou redirection). / Ou `N/A — Justification`.]
- **6. État Désactivé / Lecture seule (Disabled / Read-Only) :**
  - [`Applicable` : Contrôles inactifs ou mode consultation selon les permissions `ACT-xxx` ou préconditions `BR-xxx`, avec explication claire. / Ou `N/A — Justification`.]

## 10. Comportement Responsive spécifique
- **Desktop (`>= 1024px`) :** [Disposition multi-colonnes.]
- **Tablette (`640px – 1023px`) :** [Adaptation intermédiaire.]
- **Mobile (`< 640px`) :** [Empilement vertical, cibles tactiles `>= 44x44px`, absence de défilement horizontal.]

## 11. Accessibilité (a11y)
- **Structure sémantique :** `<main>`, `<h1>` unique (« [Titre exact] »), landmarks et labels de formulaires explicites.
- **Navigation clavier :** Ordre de tabulation logique, `:focus-visible` distinct, gestion du focus sur modales/erreurs.
- **Lecteurs d'écran :** Annonces dynamiques via `aria-live="polite"` ou `role="alert"` lorsque des états dynamiques sont applicables.

## 12. Règles métier et Exigences associées (`BR-xxx`, `FR-xxx`)
- `FR-001`, `BR-001` : [Application concrète sur cet écran, ou `N/A`.]

## 13. Références visuelles et Livrables visuels liés (`REF-xxx`)
- **Références d'inspiration (`REF-xxx`) :** [Éléments repris ou adaptés de `../../02-research/references-analysis.md`.]
- **Livrables visuels associés :** [Indiquer honnêtement : *Aucun livrable graphique produit (spécification textuelle + wireframe ASCII ci-dessus)*, ou pointer vers la maquette/wireframe réellement fourni ou généré.]

## 14. Critères d'acceptation de l'écran (`AC-xxx` — `Given / When / Then`)
1. **`AC-001` (Comportement nominal) :** *Given* [contexte], *When* l'utilisateur accède à `SCR-001`, *Then* [résultat observable].
2. **`AC-002` (États applicables & Responsive) :** *Given* [condition d'état applicable ou écran mobile `375px`], *When* [action], *Then* [résultat observable sans perte de données ni débordement].
