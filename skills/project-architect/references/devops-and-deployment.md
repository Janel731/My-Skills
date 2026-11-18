# Infrastructure, Déploiement, Exploitation et Coûts

## 1. Environnements et isolation

Définis une topologie d'environnements adaptée à la taille du projet :
- **Développement local (`local`)** : Exécutable facilement par un développeur (base locale ou conteneurisée, variables `.env.example` documentées, données de seed reproductibles, mocks des services payants).
- **Pré-production / Validation (`staging` / `preview`)** : Environnement miroir permettant de valider les parcours UX/UI (`SCR-xxx`), les migrations de base de données et les intégrations (en mode sandbox/test) avant mise en production.
- **Production (`prod`)** : Strictement isolé (bases de données, clés d'API, secrets, buckets de stockage et accès distincts du staging).

## 2. Pipeline CI/CD et stratégie de déploiement

Spécifie dans `docs/05-architecture/system-overview.md` et `docs/07-delivery/developer-handoff.md` :
- **Contrôles automatisés avant fusion (CI)** : Vérification du typage/compilation, linter, tests unitaires et d'intégration, contrôle des secrets et des vulnérabilités critiques.
- **Déploiement continu ou contrôlé (CD)** :
  - Ordre d'exécution : Sauvegarde préalable -> Migrations de base de données rétrocompatibles -> Déploiement applicatif -> Vérification de santé (*Healthcheck* / *Smoke test*).
- **Stratégie de Rollback** : Comment revenir à la version précédente en moins de quelques minutes si une régression critique est détectée, et comment gérer les migrations de données non destructrices (*Expand and Contract pattern*).

## 3. Observabilité et Exploitation (Run)

Un produit n'est pas terminé au premier déploiement. Documente :
- **Surveillance (Monitoring & Alerting)** : Vérification de disponibilité (uptime), taux d'erreurs HTTP `5xx`, latence des endpoints critiques, échecs des jobs asynchrones, saturation disque/mémoire/quotas API.
- **Journalisation (Logging)** : Logs structurés JSON, niveau de verbosité, corrélation des requêtes, durée de rétention et respect de la vie privée.
- **Sauvegardes et Reprise après incident (DRP)** : Sauvegardes automatisées des bases de données et des fichiers utilisateurs, stockage sur une zone distincte et test périodique de restauration.
- **Responsabilités opérationnelles** : Qui déploie, qui reçoit les alertes critiques, qui applique les mises à jour de sécurité et qui assure le support de niveau 1/2.

## 4. Analyse des coûts d'infrastructure et de services tiers

Identifie tous les postes de coûts d'exploitation :
- Hébergement frontend, backend/compute et workers.
- Base de données, cache et stockage de fichiers/médias + bande passante sortante (egress).
- Services tiers (authentification, envoi d'e-mails/SMS, paiement — commissions par transaction, appels API IA/LLM par million de tokens, cartographie).
- Observabilité, noms de domaine, certificats et sauvegardes.

**Règle de rigueur financière** :
- Si les tarifs exacts sont vérifiés et datés via une source officielle, cite la source et la date.
- Si les tarifs ne peuvent pas être vérifiés en temps réel, détaille les **facteurs d'échelle (cost drivers)** (ex. coût par utilisateur actif, par Go stocké, par 1 000 requêtes IA) et marque les montants comme `[HYPOTHESE : grille tarifaire fournisseur à vérifier]` sans jamais inventer de prix fictifs.
