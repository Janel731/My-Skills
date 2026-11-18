# Product Design & UX Design

## 1. Objectif

L'UX Design (conception de l'expérience utilisateur) garantit que le produit résout le bon problème, pour les bons utilisateurs, avec un parcours fluide, compréhensible, accessible et résilient aux erreurs. Il fait le pont entre la **Phase 1 (Discovery)**, la **Phase 3 (Product Design)** et la **Phase 4 (UX/UI Design)**.

## 2. Identification des utilisateurs et Personas (`PER-xxx`)

### Quand créer des personas ?
- **Toujours** identifier les profils d'utilisateurs et acteurs (`ACT-001`...).
- **Créer des fiches Personas (`PER-001`...)** lorsque les choix d'interface, de parcours, de vocabulaire ou de priorisation dépendent du contexte humain, du niveau de littératie numérique, de l'environnement physique ou de la fréquence d'utilisation.

### Règles de conception d'un persona utile (sans fiction superflue)
N'invente pas de détails biographiques inutiles (loisirs, animaux de compagnie, citations artificielles). Chaque persona doit documenter uniquement ce qui impacte la conception :

- **Identifiant et rôle** : ex. `PER-001 — Gérant de restaurant indépendant`.
- **Contexte d'utilisation** : appareil principal, environnement (bruyant, mobile, bureau, connectivité instable), fréquence et durée des sessions.
- **Objectifs principaux** : ce qu'il cherche à accomplir concrètement.
- **Frustrations et points de douleur actuels (Pain points)** : ce qui lui fait perdre du temps, de l'argent ou génère des erreurs aujourd'hui.
- **Niveau d'aisance numérique et contraintes** : besoins d'accessibilité, rapidité d'exécution, tolérance à la complexité.
- **Exigences et écrans clés liés** : références `FR-xxx` et `SCR-xxx`.

## 3. Besoins, problèmes utilisateurs et Jobs-to-be-Done

Formule les besoins sous l'angle du problème à résoudre avant la solution :

- **Situation / Déclencheur** : *Quand [contexte ou événement déclencheur]...*
- **Motivation / Action** : *Je veux [objectif utilisateur sans jargon technique]...*
- **Résultat attendu** : *Afin de [valeur mesurable ou état souhaité].*

Chaque fonctionnalité du produit (`FR-xxx`) doit répondre à au moins un besoin utilisateur identifié ou à une contrainte opérationnelle/réglementaire explicite.

## 4. User Journeys (`UJ-xxx`)

Un **User Journey** décrit l'expérience macroscopique d'un utilisateur de bout en bout (avant, pendant et après l'interaction avec le produit) :

1. **Étapes du parcours** : Découverte / Entrée -> Onboarding / Première action -> Utilisation courante -> Résolution d'un problème -> Fidélisation / Sortie.
2. **Pour chaque étape** :
   - Action de l'utilisateur.
   - Point de contact (écran, notification, e-mail, API, action hors ligne).
   - Pensées / Questions de l'utilisateur (ce qu'il doit comprendre immédiatement).
   - Point de friction potentiel (risque d'abandon ou d'erreur).
   - Opportunité de design / Réponse du produit.

## 5. User Flows (`UF-xxx`)

Un **User Flow** modélise la logique opérationnelle et les embranchements précis d'une tâche dans le produit (représentable en diagramme Mermaid `flowchart TD`) :

- **Déclencheur et préconditions** (ex. utilisateur connecté ou anonyme).
- **Parcours nominal (Happy Path)** : la séquence la plus directe entre l'intention et le résultat. Minimise le nombre de clics, d'écrans et de saisies obligatoires.
- **Parcours alternatifs** : variantes légitimes (ex. paiement par carte vs virement, connexion sociale vs e-mail, import fichier vs saisie manuelle).
- **Parcours d'erreur et de récupération (Edge & Error Flows)** :
  - Échec de validation d'un champ.
  - Perte de réseau ou délai d'attente dépassé (timeout).
  - Ressource introuvable, conflit d'édition ou permission refusée.
  - Action annulée ou retour arrière par l'utilisateur.

**Règle fondamentale** : Aucun User Flow ne doit contenir d'impasse (dead-end). Tout état d'erreur ou d'absence de données doit offrir une action claire pour continuer, réessayer ou revenir en sécurité.

## 6. Architecture de l'information, Sitemap et Navigation

### Architecture de l'information (IA)
- Regroupe les concepts et contenus selon le **modèle mental de l'utilisateur**, jamais selon la structure interne des tables de base de données ou des microservices.
- Utilise un vocabulaire métier constant d'un bout à l'autre du produit (ne pas alterner entre « Facture », « Reçu », « Quittance » et « Document » pour le même objet).
- Hiérarchise les informations par fréquence d'usage et criticité : ce qui sert 80 % du temps est accessible au premier niveau ; les réglages rares sont placés au second niveau.

### Sitemap et modèles de navigation
Documente dans `docs/03-product-design/sitemap.md` :
- L'arborescence complète des vues/écrans (`SCR-001`, `SCR-002`...) avec un diagramme Mermaid.
- Les règles d'accès par rôle (Public, Authentifié, Administrateur, etc.).
- Les mécanismes de navigation :
  - **Navigation globale** (présente partout : barre principale, menu, recherche globale).
  - **Navigation locale / contextuelle** (onglets internes, sous-menus, filtres, fil d'Ariane).
  - **Navigation transactionnelle** (étapes d'un assistant/wizard, modales, tiroirs/drawers avec règles de fermeture et conservation du brouillon).

## 7. Gestion des erreurs, cas limites (Edge Cases) et états vides

Anticipe systématiquement dans la conception UX :

1. **Le premier lancement (First-Time User Experience / Empty State)** : Que voit l'utilisateur quand sa liste de projets, de commandes ou de messages est vide ? Fournis toujours une explication courte et un bouton d'action directe pour créer le premier élément.
2. **Les volumes extrêmes** : 0 élément, 1 élément, 10 000 éléments (pagination, virtualisation, recherche/filtre), textes très longs (troncature `ellipsis` avec tooltip ou retour à la ligne maîtrisé), noms composés ou caractères internationaux.
3. **Les actions destructrices** : Suppression, révocation, annulation irréversible -> exiger soit une possibilité d'annulation immédiate (*Undo* temporisé), soit une modale de confirmation explicite précisant la conséquence exacte.
4. **La prévention des erreurs** : Désactiver ou guider avant la faute plutôt que d'afficher un message d'erreur après coup (ex. formatage automatique des dates/téléphones, indication claire des critères de mot de passe en temps réel, sauvegarde automatique des formulaires longs).

## 8. Accessibilité (a11y) et Utilisabilité dès la conception

L'accessibilité n'est pas une couche cosmétique ajoutée en fin de projet ; elle se conçoit en Phase 3 et Phase 4 :

- **Navigation complète au clavier** : Ordre de tabulation logique (`tabindex`), état `:focus-visible` hautement distinct sur tout élément interactif, fermeture des modales/menus via `Escape`, piège de focus (*focus trap*) dans les modales ouvertes.
- **Contrastes visuels (WCAG 2.1 AA minimum)** :
  - Texte normal : ratio `>= 4.5:1`.
  - Grand texte (`>= 18pt` ou `>= 14pt` gras) et composants UI / icônes porteuses de sens : ratio `>= 3:1`.
- **Indépendance de la couleur seule** : Ne jamais transmettre une information (erreur, statut, série graphique) uniquement par la couleur ; associer toujours une icône, un libellé textuel ou un motif.
- **Sémantique et lecteurs d'écran** : Structure de titres hiérarchique (`h1` -> `h2` -> `h3` sans saut), labels explicites associés à chaque champ de formulaire (`<label>`), textes alternatifs pertinents, annonces `aria-live` pour les retours asynchrones (toasts, erreurs de formulaire, chargements).
- **Ergonomie motrice et cognitive** : Zones cliquables/tactiles d'au moins `44x44px` sur mobile (`36x36px` minimum sur desktop dense), respect de `prefers-reduced-motion` pour désactiver les mouvements brusques, langage clair et messages d'erreur orientés solution (« Le format de l'adresse e-mail est incomplet, ex. nom@domaine.fr » plutôt que « Entrée invalide : code 422 »).

## 9. Adaptation aux projets sans interface graphique (API, CLI, SDK, IoT)

Lorsque le projet est une API pure, un outil CLI, une bibliothèque ou un système embarqué :
- L'UX devient la **Developer Experience (DX)** ou l'**Operator Experience**.
- Les Personas représentent les développeurs intégrateurs, les administrateurs système ou les opérateurs terrain.
- Les User Flows décrivent le parcours d'intégration (authentification, premier appel réussi en moins de 5 minutes, débogage d'une erreur, mise à jour de version).
- Les « écrans » sont remplacés par les **spécifications de commandes CLI** (arguments, flags, sortie standard, sortie d'erreur explicite, codes de retour POSIX) ou les **contrats d'API et webhooks**.
