# Conception d'Architecture Logicielle

## 1. Démarche d'architecture proportionnée

1. **Partir des exigences et de l'expérience utilisateur** : L'architecture technique sert les parcours (`UF-xxx`), les écrans (`SCR-xxx`), les règles métier (`BR-xxx`) et les exigences non fonctionnelles (`NFR-xxx`), jamais l'ego technologique.
2. **Privilégier la simplicité démontrable** : Choisis le style architectural le plus simple qui répond aux besoins actuels et à l'évolution plausible à 12-24 mois. Pas de microservices, de Kubernetes, de bus d'événements distribués, de CQRS/Event Sourcing ou de multi-cloud sans justification factuelle et chiffrée documentée dans un ADR (`docs/adr/ADR-NNN.md`).
3. **Définir le contexte et les frontières** : Identifie les acteurs humains, le système à construire et tous les systèmes externes (paiement, auth, e-mail, IA, stockage).
4. **Découper en modules cohérents (`MOD-xxx`)** : Chaque module ou composant possède une responsabilité unique claire, une interface explicite et des dépendances maîtrisées.
5. **Analyser les modes de défaillance** : Pour chaque dépendance externe ou flux critique, précise ce qui se passe en cas de lenteur, d'indisponibilité ou de réponse invalide (timeout, retry avec backoff, circuit breaker, dégradation gracieuse dans l'UI).

## 2. Sélection du style architectural

Compare les options crédibles en fonction de la taille de l'équipe, du domaine et des contraintes d'exploitation :

- **Monolithe modulaire** : Recommandation par défaut pour la majorité des nouveaux produits web, mobiles (backend) et SaaS. Déploiement unique, transactions ACID simples, frontières internes strictes entre modules métiers, évolutif vers des services séparés plus tard si un goulot d'étranglement réel apparaît.
- **Architecture en couches / Hexagonale (Ports & Adapters)** : Pertinente lorsque la logique métier est riche ou que les intégrations externes (fournisseurs de paiement, LLM, ERP) sont susceptibles de changer.
- **Architecture orientée événements / Asynchrone (Workers & Queues)** : Pertinente pour découpler les traitements lourds (génération de fichiers, pipelines IA/Data, envoi de notifications, webhooks) du cycle requête/réponse utilisateur.
- **Serverless / BaaS (Backend-as-a-Service)** : Pertinent pour accélérer un MVP ou absorber une charge très variable, à condition d'évaluer les coûts à l'échelle, les limites d'exécution (cold starts, timeouts) et la dépendance fournisseur (vendor lock-in).
- **Microservices / Systèmes distribués** : Uniquement lorsque plusieurs équipes autonomes, des contraintes réglementaires d'isolation forte ou des profils de mise à l'échelle radicalement divergents l'exigent.
- **Architecture embarquée / Edge / Local-First** : Lorsque la latence ultra-faible, la confidentialité locale ou le fonctionnement hors ligne (offline-first avec synchronisation) sont prioritaires.

## 3. Architecture Frontend / Client (Alignement avec `04-ux-ui/`)

Dans `docs/05-architecture/system-overview.md`, assure la jonction directe entre l'architecture technique et la conception UX/UI :

- **Rendu et routage** : Stratégie choisie (SSR, SSG, CSR/SPA, hybride, navigation native mobile) justifiée par le SEO, la performance perçue et l'interactivité des écrans (`SCR-xxx`).
- **Architecture des composants UI** : Organisation du code alignée sur `docs/04-ux-ui/design-system.md` (primitives/tokens -> composants du Design System `COMP-xxx` -> composants métiers -> vues/écrans `SCR-xxx`).
- **Gestion de l'état (State Management)** :
  - État serveur / cache distant (requêtes, invalidation, mises à jour optimistes).
  - État d'URL (filtres, pagination, onglet actif — pour permettre le partage de liens et le bouton Retour).
  - État local de formulaire et d'interface (modales, chargements, validations).
  - État global partagé (session utilisateur, thème clair/sombre, préférences).
- **Résilience côté client** : Gestion centralisée des erreurs API, interception des expirations de session, prévention des doubles soumissions et conservation des saisies en cas d'échec réseau.

## 4. Architecture Backend / Services

Documente avec précision :
- **Modules métiers (`MOD-001`...)** et leurs responsabilités exclusives.
- **Couche d'exposition** (API REST, GraphQL, gRPC, WebSockets/SSE, webhooks entrants/sortants).
- **Authentification, gestion de session et contrôle d'accès (RBAC / ABAC)** vérifiés côté serveur à chaque opération.
- **Validation des données et exécution des règles métier (`BR-xxx`)** : aucune règle métier critique ne doit reposer uniquement sur le frontend.
- **Traitements asynchrones et tâches planifiées (Cron / Jobs)** : idempotence, file d'attente, politique de retry et file de lettres mortes (Dead-Letter Queue).
- **Observabilité** : Journalisation structurée (avec identifiant de corrélation `request_id`), métriques techniques et métiers, traçage des erreurs.

## 5. Diagrammes d'architecture Mermaid

Inclure dans `docs/05-architecture/system-overview.md` des diagrammes Mermaid lisibles et **strictement fidèles au texte** (chaque boîte du diagramme doit être décrite dans le tableau des composants) :

1. **Diagramme de contexte système** (Acteurs <-> Système <-> Services externes).
2. **Diagramme des conteneurs / modules internes** (`MOD-xxx`, base de données, cache, workers).
3. **Diagrammes de séquence** pour les 1 à 3 flux les plus critiques ou risqués (ex. authentification, paiement, pipeline asynchrone).

## 6. Choix technologiques et ADR

N'impose jamais une stack par habitude. Évalue chaque brique technologique selon :
- Adéquation aux exigences fonctionnelles et non fonctionnelles.
- Compétences de l'équipe cible et maintenabilité à long terme.
- Maturité, stabilité, sécurité et santé de l'écosystème.
- Coût total de possession (développement + hébergement + licences + maintenance).
- Réversibilité et portabilité.

Chaque choix technologique majeur fait l'objet d'un ADR dédié dans `docs/adr/ADR-NNN.md` et est récapitulé dans `docs/05-architecture/architecture-decisions.md`.
