# Stratégie de Tests, Critères d'Acceptation (`AC-xxx`) et Qualité (`TEST-xxx`)

## 1. Objectif

Garantir que chaque exigence fonctionnelle (`FR-xxx`), règle métier (`BR-xxx`), écran (`SCR-xxx`) et exigence non fonctionnelle (`NFR-xxx`) dispose d'un **mécanisme de vérification concret, proportionné et traçable** dans `docs/06-quality/test-strategy.md` et `docs/06-quality/acceptance-criteria.md`.

**Règle d'intégrité** : Distingue toujours la *stratégie de test planifiée dans le blueprint* des *tests réellement exécutés*. Ne prétends jamais qu'un test a réussi si tu ne l'as pas exécuté dans un environnement d'exécution réel.

## 2. Pyramide et niveaux de tests à spécifier (`TEST-001`...)

Chaque scénario ou suite de test critique reçoit un identifiant stable `TEST-001`, `TEST-002`... et se rattache à l'un des niveaux suivants selon la criticité du projet :

1. **Tests unitaires (`Unit`)** :
   - Cible : Règles métier pures (`BR-xxx`), calculs, validations de schémas, machines à états, fonctions utilitaires et transformations de données.
   - Exigence : Rapides, déterministes, sans dépendance réseau ou base de données externe.
2. **Tests de composants et d'états UI (`UI`)** :
   - Cible : Composants critiques du Design System (`COMP-xxx`) et vérification des **états qualifiés `Applicable`** parmi la grille des 6 états des écrans (`SCR-xxx`). Ne jamais exiger de tests artificiels pour les états qualifiés `N/A` (ex. pas de test d'état de chargement dynamique sur une page purement statique).
3. **Tests d'intégration et de contrats d'API (`Integration`)** :
   - Cible : Endpoints (`API-xxx`), requêtes et contraintes de base de données (`ENT-xxx`), permissions par rôle (`401`/`403`), webhooks et files d'attente.
4. **Tests End-to-End (`E2E`)** :
   - Cible : Les parcours utilisateurs prioritaires (`UF-xxx`) du MVP (inscription/connexion, parcours cœur de valeur, paiement ou transaction critique, récupération sur erreur).
5. **Tests d'accessibilité (`A11Y`)** :
   - Cible : Audit automatisé (axe-core / Lighthouse) + parcours complet au clavier seul (`Tab`, `Shift+Tab`, `Enter`, `Escape`), vérification des contrastes et des annonces de formulaires/modales.
6. **Tests de sécurité (`Security`)** :
   - Cible : Contrôle d'accès croisé entre utilisateurs (tentative d'accès aux ressources d'autrui), entrées malveillantes, expiration de jetons, rate limiting, audit des dépendances.
7. **Tests de performance et de résilience (`Performance`)** :
   - Cible : Temps de réponse sous charge nominale/pic, comportement lors de la coupure d'une API tierce ou d'un réseau mobile lent.

## 3. Consolidation des critères d'acceptation (`AC-001`...)

Chaque critère d'acceptation dans `docs/06-quality/acceptance-criteria.md` porte un identifiant stable (`AC-001`, `AC-002`...), utilise la structure observable **Given / When / Then** et couvre :
- Le scénario nominal.
- Les cas de refus / validation / erreur.
- Les cas limites (valeurs nulles, listes vides lorsqu'elles sont applicables, doublons, limites de quotas).
- Les exigences d'interface et d'accessibilité associées à l'écran (`SCR-xxx`).

## 4. Critères de sortie (Definition of Done & Go/No-Go Release)

Définis clairement les conditions objectives pour déclarer un lot ou le MVP prêt à être livré :
- 100 % des exigences `Must (MVP)` (`FR-xxx`, `NFR-xxx`) implémentées et leurs critères d'acceptation (`AC-xxx`) vérifiés.
- Tous les états qualifiés `Applicable` des écrans prioritaires (`SCR-xxx`) implémentés et vérifiés sur Desktop et Mobile.
- Aucun défaut bloquant (Sévérité Critique ou Haute) ouvert.
- Contrôles de sécurité et d'autorisation vérifiés sur tous les endpoints exposés.
- Sauvegardes, variables d'environnement et procédure de rollback opérationnelles.
