# Ingénierie des Exigences et Spécification Fonctionnelle (`FR-xxx`, `NFR-xxx`, `BR-xxx`, `AC-xxx`)

## 1. Principes d'une exigence exploitable

Chaque exigence formulée dans `docs/03-product-design/requirements.md` doit respecter 5 critères :

1. **Atomique** : Une seule capacité ou contrainte par identifiant (pas de « Le système doit permettre de payer, facturer, exporter en comptabilité et relancer les impayés » dans un seul `FR-001`).
2. **Non ambiguë** : Formulée dans un langage métier précis, sans adjectifs vagues non mesurables (« rapide », « intuitif », « moderne », « fluide », « sécurisé »).
3. **Testable** : Accompagnée de critères d'acceptation observables (`AC-001`...) permettant de trancher sans débat si l'exigence est remplie ou non.
4. **Traçable avec souplesse** : Reliée en amont à un objectif/besoin (`OBJ-xxx`, `PER-xxx`) et en aval aux artefacts pertinents (`BR-xxx`, `UF-xxx`, `SCR-xxx`, `COMP-xxx`, `ENT-xxx`, `API-xxx`, `ADR-xxx`, `AC-xxx`, `TEST-xxx`). Les relations non pertinentes pour une exigence donnée sont marquées `N/A` avec justification (ex. traitement interne sans écran `SCR-xxx`).
5. **Qualifiée** : Dotée d'une origine (`EXPLICIT`, `INFERRED`, `RECOMMENDED`, `OUT_OF_SCOPE`), d'une priorité et d'un statut décisionnel (`[DECISION VALIDEE]`, `[DECISION PROPOSEE]`, `[HYPOTHESE]`).

## 2. Typologie et identifiants stables

- `ACT-001`... : **Acteur ou rôle système** (utilisateur humain, administrateur, tâche planifiée, webhook externe).
- `FR-001`... : **Exigence fonctionnelle (*Functional Requirement*)** (comportement ou service offert par le produit).
- `BR-001`... : **Règle métier (*Business Rule*)** (invariant, formule de calcul, condition d'éligibilité, transition d'état autorisée/interdite).
- `NFR-001`... : **Exigence non fonctionnelle (*Non-Functional Requirement*)** (performance, disponibilité, accessibilité, sécurité, conformité, compatibilité, maintenabilité).
- `AC-001`... : **Critère d'acceptation (*Acceptance Criterion*)** vérifiable en Given / When / Then.

## 3. Structure complète d'une fiche exigence fonctionnelle (`FR-xxx`)

Pour chaque exigence fonctionnelle majeure, documente :

- **ID et Titre** : `FR-001 — [Verbe d'action + Objet métier]`
- **Origine et Statut** : `EXPLICIT` | `INFERRED` | `RECOMMENDED` — `[DECISION VALIDEE]` | `[DECISION PROPOSEE]`
- **Priorité et Cible** : `Must (MVP)` | `Should (MVP si simple / V1.1)` | `Could (Post-MVP)` | `Won't now (Hors périmètre)`
- **Acteur(s) et Personas** : `ACT-xxx`, `PER-xxx` (ou `N/A`)
- **Objectif / Valeur** : Pourquoi cette fonctionnalité existe.
- **Écrans et User Flows liés** : `SCR-xxx`, `UF-xxx` (ou `N/A — justification`)
- **Préconditions** : État requis avant déclenchement.
- **Scénario nominal** : Déroulement normal étape par étape.
- **Scénarios alternatifs** : Variantes valides.
- **Cas d'erreur et cas limites** : Que fait le système en cas de donnée invalide, conflit, hors-ligne ou erreur externe ?
- **Règles métier appliquées** : `BR-xxx` (ou `N/A`)
- **Données et permissions** : Entités lues/écrites (`ENT-xxx`), contrats (`API-xxx`) et contrôles d'accès par rôle.
- **Critères d'acceptation (`AC-xxx` — `Given / When / Then`)** :
  - *Given* (Étant donné le contexte initial...)
  - *When* (Lorsque l'acteur effectue l'action...)
  - *Then* (Alors le résultat observable exact est...)

## 4. Priorisation et cadrage du MVP

Utilise une priorisation rigoureuse croisant **MoSCoW** et le ratio **Valeur / Effort / Risque** :

- **MVP (Minimum Viable Product)** : Uniquement les fonctionnalités indispensables pour délivrer la proposition de valeur centrale de bout en bout à un premier utilisateur réel, en toute sécurité.
- **Après MVP (V1.1 / V2)** : Fonctionnalités d'optimisation, d'automatisation secondaire, de reporting avancé ou d'intégrations supplémentaires.
- **Hors périmètre (Out of Scope)** : Fonctionnalités explicitement écartées pour éviter toute dérive (*scope creep*).

## 5. Exigences Non Fonctionnelles (`NFR-xxx`)

Spécifie des seuils vérifiables adaptés au projet (et si un seuil dépend d'une mesure future, marque-le `[POINT EN ATTENTE : cible à confirmer]` en proposant une valeur par défaut raisonnable) :

- **Performance** : Temps de réponse API (`p95`), temps de chargement initial des écrans (`LCP`, `INP`), fluidité des animations (`60 fps`).
- **Accessibilité** : Conformité WCAG 2.1 AA, navigation clavier complète, support lecteur d'écran, contrastes `>= 4.5:1`.
- **Disponibilité et Résilience** : Tolérance aux pannes de services tiers, comportement hors ligne ou réseau dégradé, RPO et RTO.
- **Sécurité et Confidentialité** : Authentification, autorisation par ressource, chiffrement, journalisation d'audit, rétention RGPD.
- **Compatibilité** : Navigateurs supportés, versions iOS/Android, résolutions d'écran (`320px` à `2560px+`).
- **Maintenabilité et Observabilité** : Couverture des flux critiques par les tests (`TEST-xxx`), logs structurés, alertes d'erreur.
