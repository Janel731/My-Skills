# Project Discovery & Cadrage Initial

## 1. Objectif

Passer d'une idée initiale (parfois floue, incomplète ou formulée directement comme une solution technique) à une **compréhension partagée, vérifiée et structurée du problème, des utilisateurs, de la proposition de valeur et du périmètre**.

## 2. Les 10 axes d'exploration du cadrage

Explore ces dimensions avec discernement (sans transformer l'échange en interrogatoire mécanique) :

1. **Problème réel** : Quelle difficulté concrète cherche-t-on à résoudre ? Pour qui ? Dans quelle situation ? Comment les utilisateurs contournent-ils ce problème aujourd'hui et pourquoi est-ce insatisfaisant ?
2. **Utilisateurs et parties prenantes** : Utilisateurs finaux (bénéficiaires), acheteurs/décideurs, administrateurs, modérateurs, opérateurs terrain, partenaires et systèmes externes.
3. **Proposition de valeur et Vision** : Quel résultat concret améliore-t-on (gain de temps, réduction d'erreur, nouveau service, expérience simplifiée) et quelle est l'ambition à moyen terme ?
4. **Contexte d'usage et expérience** : Fréquence d'utilisation, durée d'une session, appareils (mobile en mobilité, desktop double écran, tablette partagée, terminal embarqué), connectivité (hors ligne requis ou non), langues, accessibilité et attentes esthétiques/références visuelles.
5. **Périmètre (Scope)** : Ce qui est indispensable au MVP, ce qui est reporté aux versions ultérieures (V1.1, V2) et ce qui est explicitement hors périmètre.
6. **Contraintes non négociables** : Budget (développement et exploitation mensuelle), calendrier/échéances, taille et compétences de l'équipe de développement, technologies imposées ou interdites, réglementation (RGPD, santé, finance, accessibilité légale), souveraineté ou mode d'hébergement.
7. **Données** : Données collectées ou produites, origine, propriétaire, sensibilité (données personnelles, secrets d'affaires, paiement), volume initial et projeté, durée de conservation.
8. **Intégrations externes** : Authentification (SSO, OAuth), paiement (Stripe, Mobile Money, etc.), messagerie (e-mail, SMS, push, WhatsApp), cartographie, ERP/CRM, fournisseurs d'IA, API tierces.
9. **Exploitation et gouvernance** : Qui déploie, administre, supporte les utilisateurs, modère les contenus, surveille les alertes et maintient le système après la mise en ligne ?
10. **Critères de succès (`OBJ-xxx`)** : Indicateurs mesurables (KPI produit, UX et techniques), valeur cible et méthode de mesure.

## 3. Art de questionner et de challenger l'idée

- **Sélectionne les 3 à 6 questions les plus structurantes** : Ne pose jamais 20 questions d'un coup. Priorise celles dont la réponse modifie radicalement le périmètre, l'expérience utilisateur ou l'architecture.
- **Challenge avec bienveillance et lucidité** :
  - Si l'utilisateur demande d'emblée une fonctionnalité complexe (ex. *« je veux un chat temps réel, une IA générative, une marketplace et une application mobile native dès le lancement »*), aide-le à identifier le **cœur de valeur (Core Loop)** qui valide l'intérêt du produit au moindre coût.
  - Signale les contradictions dès la Phase 1 (ex. *« vouloir un fonctionnement 100 % hors ligne tout en reposant uniquement sur une API LLM cloud temps réel sans modèle local »*).
- **Propose des options concrètes** : Lorsqu'un point est ouvert, accompagne ta question de 2 ou 3 options claires avec leurs implications pour aider l'utilisateur à trancher rapidement.

## 4. Classification de l'origine des besoins et de la certitude

Croise systématiquement deux axes :

### A. Origine du besoin
- `EXPLICIT` : Demandé explicitement par le porteur de projet.
- `INFERRED` : Déduit logiquement du domaine ou du contexte, à faire confirmer.
- `RECOMMENDED` : Proposé par l'architecte / product designer pour sécuriser l'UX, la qualité ou la technique.
- `OUT_OF_SCOPE` : Exclu explicitement de la version cible.

### B. Statut décisionnel
- `[FAIT VERIFIE]` | `[HYPOTHESE]` | `[RECOMMANDATION]` | `[DECISION PROPOSEE]` | `[DECISION VALIDEE]` | `[POINT EN ATTENTE]`

## 5. Livrables de la Phase 1 dans `docs/01-discovery/`

Selon le profil documentaire choisi (`references/documentation-standards.md`) :
- `docs/README.md` : Initialisé avec le profil du projet et la liste des documents prévus.
- `docs/01-discovery/project-brief.md` : Synthèse exécutive, problème, acteurs, objectifs, contraintes, hypothèses et questions ouvertes.
- `docs/01-discovery/product-vision.md` : Vision long terme, proposition de valeur, positionnement, principes directeurs UX/Produit (fusionnable dans `project-brief.md` en Profil Compact).
- `docs/01-discovery/scope.md` : Frontières exactes du MVP, jalons fonctionnels, exclusions explicites et dépendances externes (fusionnable dans `project-brief.md` en Profil Compact).
