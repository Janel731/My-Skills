# Spécifications Détaillées des Écrans (`SCR-xxx`) et Livrables Visuels

## 1. Distinction fondamentale : Spécification d'interface vs Livrable visuel

Le skill différencie strictement deux natures de production UX/UI :

### 1.1. Spécification d'interface (Document textuel structuré)
Document Markdown (`docs/04-ux-ui/screens/screen-XXX.md`) détaillant avec précision la structure spatiale, les composants (`COMP-xxx`), les contenus, les interactions, la grille d'états, le comportement responsive, l'accessibilité et les règles métier (`BR-xxx`, `FR-xxx`) d'un écran. C'est le livrable systématique du blueprint.

### 1.2. Livrable visuel (Représentation graphique ou interactive)
Représentation visuelle ou interactive de cette interface. Selon les capacités réelles de la plateforme hôte, l'agent peut produire ou préparer :
- **Wireframes basse fidélité** (schémas structurels ASCII, SVG/HTML ou croquis fonctionnels).
- **Maquettes haute fidélité** (rendus graphiques ou composants stylisés si l'environnement dispose d'un moteur de rendu ou de génération d'images/interfaces).
- **Diagrammes de parcours** (flux Mermaid `flowchart` ou `stateDiagram`).
- **Prototypes interactifs** (si un environnement de prévisualisation code/canvas est disponible et demandé).
- **Illustrations et références visuelles annotées**.
- **Descriptions précises (prompts de design)** destinées à un outil de design externe ou à un designer humain.

### 1.3. Six règles obligatoires sur les livrables UX/UI
1. **Ne jamais prétendre qu'une maquette graphique existe** lorsqu'elle n'a pas été réellement produite dans l'environnement.
2. **Ne jamais confondre une description textuelle avec un prototype interactif** ou une maquette haute fidélité.
3. **Identifier explicitement en en-tête de chaque fiche le type de livrable fourni** (ex. *Spécification textuelle + wireframe ASCII*, *Diagramme de flux Mermaid*, *Brief pour outil de design* ou *Maquette générée*).
4. **Si les capacités de génération visuelle sont indisponibles**, produire une spécification textuelle complète et directement exploitable par un développeur ou un designer, et signaler honnêtement la limite de la plateforme.
5. **Ne jamais imposer un outil de design particulier** (Figma, Sketch, Penpot, Adobe XD, etc.) sauf si le porteur de projet l'a choisi.
6. **Respecter fidèlement les références visuelles fournies** par le porteur de projet (`docs/02-research/references-analysis.md`).

## 2. Niveau d'exigence d'une spécification d'écran (`SCR-xxx`)

Chaque écran ou vue clé du produit est documenté dans `docs/04-ux-ui/screens/screen-XXX.md` (ou regroupé de manière cohérente en profil `Compact`). Un développeur frontend ou un designer UI doit pouvoir implémenter ou maquetter l'écran **sans deviner les contenus, les états applicables, les validations ou les erreurs**.

**Formulations vagues interdites** :
- « Créer une page de connexion classique et intuitive. »
- « Afficher un tableau de bord moderne avec les statistiques de l'utilisateur. »

## 3. Anatomie d'une fiche écran (`SCR-xxx`)

Chaque spécification d'écran couvre les sections suivantes selon leur pertinence :

1. **Identifiant, Nom, Type de livrable et Route / Point d'entrée** (`SCR-001`...).
2. **Objectif de l'écran et Action principale (Primary CTA)**.
3. **Utilisateurs concernés (`PER-xxx`, `ACT-xxx`) et Permissions / Redirections**.
4. **Structure spatiale et découpage en zones (Layout)**.
5. **Hiérarchie visuelle des éléments (Niveaux 1, 2, 3)**.
6. **Composants du Design System mobilisés (`COMP-xxx`)**.
7. **Contenus et données nécessaires** (libellés exacts, formats, sources `ENT-xxx` / `API-xxx` ou statique, règles de troncature).
8. **Actions possibles et appels API (`API-xxx`)**.
9. **Interactions, micro-interactions et animations**.
10. **Examen systématique de la grille des 6 États de l'écran** (voir Section 4 ci-dessous).
11. **Comportement Responsive** (Desktop, Tablette, Mobile).
12. **Accessibilité (a11y)** (titres, focus clavier, annonces `aria-live`).
13. **Règles métier et Exigences associées (`BR-xxx`, `FR-xxx`)**.
14. **Références visuelles (`REF-xxx`) et livrables visuels liés**.
15. **Critères d'acceptation de l'écran (`AC-xxx` en `Given / When / Then`)**.

## 4. Règle de gestion de la grille des 6 États des écrans

Les six catégories d'états constituent la **grille de contrôle de référence** de tout écran :
1. **Initial (Nominal)**
2. **Chargement (Loading)**
3. **Vide (Empty State)**
4. **Erreur (Error State)**
5. **Succès (Success State)**
6. **Désactivé / Lecture seule (Disabled / Read-Only)**

### Principe de proportionnalité : Examen obligatoire, spécification selon pertinence
Ces 6 états **ne doivent pas être rendus artificiellement obligatoires sur tous les écrans**. Pour chaque écran, l'agent examine systématiquement les 6 catégories et attribue à chacune l'une des trois qualifications suivantes :

| Qualification | Quand l'utiliser | Ce que la fiche écran doit contenir |
| :--- | :--- | :--- |
| **`Applicable`** | L'état peut réellement se produire sur cet écran compte tenu de ses données, actions ou permissions. | Spécifier concrètement la présentation visuelle, les messages affichés et le comportement interactif (ex. squelette sans saut de layout, conservation des saisies en cas d'erreur, CTA sur état vide). |
| **`Non applicable (N/A)`** | L'état n'a aucun sens fonctionnel ou technique sur cet écran. | Indiquer `N/A` accompagné d'une **justification courte** (ex. *Écran statique de présentation : Chargement = N/A (contenu statique pré-rendu), Vide = N/A, Succès = N/A, Désactivé = N/A*). |
| **`À déterminer`** (`[POINT EN ATTENTE]`) | Une inconnue métier ou technique empêche encore de savoir si l'état existe ou comment il doit réagir. | Signaler explicitement l'information manquante à clarifier avec le porteur de projet. |

### Exemples d'application concrète
- **Écran statique de présentation / Landing page / Mentions légales** :
  - *Initial* : `Applicable`.
  - *Chargement, Vide, Erreur, Succès, Désactivé* : généralement `N/A` (avec justification : contenu statique embarqué sans requête dynamique ni formulaire).
- **Écran de formulaire de création ou d'édition** :
  - *Initial* : `Applicable` (valeurs par défaut, focus).
  - *Chargement* : `Applicable` (état de soumission du bouton, verrouillage contre le double envoi).
  - *Vide* : `N/A` (un formulaire vierge correspond à son état initial, pas à une collection vide) ou `Applicable` si une liste déroulante dépendante est vide.
  - *Erreur* : `Applicable` (erreurs de validation champ par champ + erreur serveur/réseau sans perte des données saisies).
  - *Succès* : `Applicable` (toast ou redirection après enregistrement).
  - *Désactivé* : `Applicable` (si certains contrôles dépendent d'une permission ou d'une précondition métier).
- **Écran de liste / Tableau de bord dynamique** :
  - *Initial, Chargement (skeletons), Vide (0 élément en base vs 0 résultat de filtre), Erreur (échec API avec bouton Réessayer)* : `Applicable`.
  - *Succès / Désactivé* : `Applicable` uniquement si des actions de modification ou des restrictions de rôle existent sur cette vue, sinon `N/A`.
