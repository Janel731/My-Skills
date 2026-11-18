# Workflow 06 — Critical Review, Qualité & Gestion des Risques

## 1. Objectif de la phase
Examiner l'ensemble du blueprint avec le regard d'un auditeur indépendant pour éliminer les incohérences entre Product Design, UX/UI et Architecture technique, identifier tous les risques (`RISK-xxx`), et formaliser la stratégie de tests (`TEST-xxx`) ainsi que les critères d'acceptation consolidés (`AC-xxx`).

## 2. Ressources internes du skill à mobiliser
- **Références** : `references/testing-strategy.md`, `references/security-guidelines.md`, `references/documentation-standards.md`
- **Templates** : `templates/test-strategy.md`, `templates/acceptance-criteria.md`, `templates/risk-register.md`

## 3. Entrées
- L'ensemble des documents produits lors des Phases 1 à 5 (`01-discovery/` à `05-architecture/` et `adr/`).

## 4. Déroulement opérationnel

1. **Audit de cohérence inter-couches (Checklist des 10 contrôles critiques)** :
   - *Alignement Problème <-> MVP* : Le MVP résout-il le problème central identifié en Phase 1 sans dérive ?
   - *Alignement Exigences <-> Écrans / Flux* : Chaque exigence `FR-xxx` et règle `BR-xxx` ayant un impact utilisateur est-elle prise en charge par les écrans `SCR-xxx` et flux `UF-xxx` pertinents (et les exigences purement backend ont-elles leur justification `SCR : N/A`) ?
   - *Alignement Écrans <-> Design System & Grille des 6 états* : Tous les composants utilisés dans `screens/screen-XXX.md` sont-ils définis dans `design-system.md` ? Les 6 catégories d'états ont-elles été systématiquement examinées sur chaque écran (`Applicable` avec détail / `N/A` avec justification / `À déterminer`) sans imposer d'états artificiels sur un écran statique ?
   - *Alignement Écrans <-> API & Données* : Chaque action dynamique et champ d'un écran `SCR-xxx` correspond-il à un endpoint `API-xxx` et à une entité/attribut `ENT-xxx` ?
   - *Chasse à la sur-ingénierie* : Existe-t-il un composant technique, une file d'attente ou une abstraction complexe qui peut être simplifié pour le MVP ?
   - *Points uniques de défaillance (SPOF) & Dépendances* : Que se passe-t-il si une API tierce tombe, si le réseau coupe ou si un quota est dépassé ?
   - *Sécurité & Permissions* : Existe-t-il une route ou un écran où le contrôle d'accès par rôle (`ACT-xxx`) est flou ?
   - *Accessibilité & Utilisabilité* : Les contrastes, la navigation clavier, le responsive mobile et la prévention des erreurs sont-ils garantis ?
   - *Coûts cachés & Exploitation* : Les coûts variables (tokens IA, SMS, stockage, bande passante, licences) et la charge de maintenance sont-ils maîtrisés ?
   - *Fidélité des diagrammes et honnêteté des livrables visuels* : Les diagrammes Mermaid correspondent-ils exactement aux textes descriptifs, et la distinction entre spécification textuelle et livrable visuel est-elle respectée ?
2. **Correction immédiate des écarts** :
   - Corrige directement les incohérences mineures dans les fichiers `docs/` concernés.
   - Si une contradiction majeure oblige à modifier le périmètre ou une décision déjà `APPROVED`, soumets l'arbitrage à l'utilisateur (`[DECISION PROPOSEE]`).
3. **Rédaction des livrables `docs/06-quality/`** :
   - Produis `docs/06-quality/test-strategy.md` (`TEST-001`... couvrant tests unitaires, UI/états applicables, intégration/API, E2E, accessibilité, sécurité, performance).
   - Produis `docs/06-quality/acceptance-criteria.md` (référentiel consolidé des critères `AC-001`...).
   - Produis `docs/06-quality/risk-register.md` (`RISK-001`... avec probabilité, impact, mitigation, responsable et risque résiduel).

## 5. Arbitrages d'autonomie
- **Tu décides seul** : l'élaboration des scénarios de test `TEST-xxx`, la correction des oublis de cohérence interne entre documents non encore figés et l'évaluation technique des risques.
- **Tu fais valider par l'utilisateur** : tout changement de périmètre ou d'architecture induit par la découverte d'un risque bloquant ou d'une infaisabilité.

## 6. Critères de sortie (Passage à la Phase 7)
- [ ] Aucune contradiction ne subsiste entre `03-product-design/`, `04-ux-ui/` et `05-architecture/`.
- [ ] Le registre des risques (`risk-register.md`) couvre les risques techniques, produit/UX, sécurité et dépendances.
- [ ] La stratégie de tests (`test-strategy.md`) et les critères d'acceptation (`acceptance-criteria.md`) sont complets et vérifiables.
