# Workflow 01 — Discovery & Cadrage Initial

## 1. Objectif de la phase
Comprendre en profondeur l'idée, le problème réel, les utilisateurs cibles, le contexte d'usage, la proposition de valeur, les objectifs mesurables (`OBJ-xxx`), le périmètre initial et les contraintes non négociables, puis choisir le profil documentaire adapté (*Compact*, *Standard* ou *Complet*).

## 2. Ressources internes du skill à mobiliser
- **Références** : `references/project-discovery.md`, `references/documentation-standards.md`
- **Templates** : `templates/docs-readme.md`, `templates/project-brief.md`, `templates/product-vision.md`, `templates/scope.md`

## 3. Entrées
- Une idée initiale, un besoin métier, un cahier des charges brut ou une demande de refonte soumise par l'utilisateur.

## 4. Déroulement opérationnel

1. **Reformulation et challenge bienveillant** :
   - Reformule l'idée en une proposition claire de 2 à 4 lignes sans la déformer.
   - Distingue immédiatement le problème à résoudre de la solution envisagée.
2. **Analyse des 10 axes de Discovery** :
   - Identifie ce qui est déjà connu (`[FAIT VERIFIE]`, origine `EXPLICIT`), ce qui peut être déduit provisoirement (`[HYPOTHESE]`, origine `INFERRED`) et ce que tu suggères (`[RECOMMANDATION]`, origine `RECOMMENDED`).
3. **Sélection du profil documentaire `docs/`** :
   - Détermine si le projet relève du **Profil Compact** (petit projet/site vitrine), **Profil Standard** (app web/mobile, SaaS, API) ou **Profil Complet** (plateforme complexe/système critique) et propose ce choix à l'utilisateur.
4. **Questions ciblées sur les inconnues structurantes** :
   - Pose un premier groupe de 3 à 6 questions prioritaires portant uniquement sur les points qui modifient le périmètre, l'expérience utilisateur ou l'architecture.
   - Demande également si l'utilisateur dispose de **références visuelles** (captures, sites, maquettes, inspirations) à analyser dès la Phase 2.
5. **Production des premiers livrables `docs/`** :
   - Initialise `docs/README.md`.
   - Rédige `docs/01-discovery/project-brief.md` (et `product-vision.md` + `scope.md` en Profil Standard/Complet) au statut `DRAFT` ou `REVIEW`.

## 5. Arbitrages d'autonomie
- **Tu décides seul** : la structure interne des tableaux, les identifiants `OBJ-001`..., le choix initial du profil documentaire recommandé et les hypothèses de travail non bloquantes.
- **Tu fais valider par l'utilisateur** : le problème cible, les utilisateurs prioritaires, la proposition de valeur, le périmètre macro (inclus / exclus) et les contraintes majeures (budget, délai, plateformes, réglementation).

## 6. Critères de sortie (Passage à la Phase 2)
- [ ] Le problème central et les utilisateurs cibles sont clairement identifiés.
- [ ] Les objectifs et critères de succès (`OBJ-xxx`) sont formulés.
- [ ] Le profil documentaire `docs/` est établi et `docs/README.md` + `docs/01-discovery/project-brief.md` sont rédigés.
- [ ] Les questions bloquantes empêchant la recherche ou la conception produit sont levées ou encadrées par des hypothèses explicites.
