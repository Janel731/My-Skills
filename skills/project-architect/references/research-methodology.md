# Méthodologie de Recherche Technique et d'Étude de l'Existant

## 1. Objectif

Identifier, vérifier et comparer les solutions existantes (produits concurrents, projets open source, bibliothèques, services managés, standards) afin d'éclairer les choix de Product Design et d'Architecture sans réinventer la roue ni introduire de dépendances toxiques.

## 2. Règles absolues de fiabilité et d'intégrité

1. **Aucune hallucination documentaire ou technique** :
   - N'invente jamais un résultat de recherche, une URL, un dépôt GitHub, un numéro de version, une statistique d'adoption ou un benchmark.
   - Ne prétends jamais avoir inspecté le code source d'un dépôt si tu n'y as pas réellement eu accès.
   - N'invente jamais la licence d'un projet : si elle n'est pas vérifiée, écris `Non vérifié — à contrôler avant intégration`.
   - Ne présente jamais une technologie, un SDK ou un tarif cloud comme actuel sans préciser la date de vérification (ou sans signaler l'absence d'accès web en temps réel si l'environnement est hors ligne).
2. **Transparence sur les limites de l'environnement** :
   - Si la recherche web est disponible, exécute-la sur des sources primaires et cite les URLs exactes avec la date de consultation.
   - Si la recherche web est indisponible ou restreinte, déclare-le explicitement en tête de section, distingue ce qui relève de tes connaissances générales établies (`[HYPOTHESE : à vérifier sur la documentation officielle actuelle]`) et fournis à l'utilisateur les requêtes de vérification exactes.

## 3. Hiérarchie des sources

Consulte et pondère les sources dans cet ordre de priorité :

1. **Sources primaires officielles** : Documentation officielle de la technologie, spécifications (W3C, IETF, RFC, OpenAPI), notes de version (changelogs/releases) et publications de l'équipe mainteneuse.
2. **Dépôts de code originaux (GitHub, GitLab, Codeberg)** : Fichiers `README`, `LICENSE`, `package.json` / `Cargo.toml` / `pyproject.toml`, historique des commits, releases, issues ouvertes/fermées et politique de sécurité (`SECURITY.md`).
3. **Retours d'expérience techniques argumentés** : Études de cas d'ingénierie, post-mortems, analyses d'architecture détaillant des compromis réels en production.
4. **Signaux communautaires** : Discussions d'utilisateurs et forums techniques — à utiliser uniquement pour repérer des irritants réels (bugs récurrents, mauvaise DX, breaking changes), jamais comme preuve unique de qualité.

## 4. Protocole d'audit d'un dépôt GitHub / Open Source

Avant de recommander la réutilisation, le fork ou l'intégration d'un dépôt open source, vérifie autant que possible les 10 points suivants :

1. **Identité et URL canonique** : S'agit-il du dépôt officiel ou d'un miroir/fork abandonné ?
2. **Objectif et périmètre réel** : Résout-il exactement le besoin du projet ou seulement 20 % au prix d'une lourde complexité ?
3. **Licence exacte et compatibilité** :
   - Permissive (`MIT`, `Apache-2.0`, `BSD-2/3`, `ISC`).
   - Copyleft faible ou fort (`MPL-2.0`, `LGPL`, `GPLv3`, `AGPLv3` — attention à l'obligation de redistribution du code sur les services réseau avec `AGPLv3`).
   - Licence propriétaire, *Source-Available* ou non commerciale (`BSL`, `SSPL`, `Commons Clause`, absence de licence = tous droits réservés par défaut).
4. **Activité et maintenance** : Date du dernier commit, cadence des releases, réactivité sur les issues critiques et les correctifs de sécurité, nombre de mainteneurs actifs (risque de *bus factor = 1*).
5. **Stack et empreinte technique** : Langage, runtime requis, poids des dépendances transitives, compatibilité avec l'environnement cible.
6. **Qualité de la documentation** : Guide de démarrage, documentation d'API, guide de déploiement et de mise à jour.
7. **Architecture et extensibilité** : Modularité, présence de tests automatisés, facilité de personnalisation sans modifier le cœur.
8. **Sécurité observable** : Présence d'alertes connues, gestion de l'authentification, validation des entrées.
9. **Coût d'adoption et de sortie (Lock-in)** : Effort d'intégration initial et coût de migration s'il faut remplacer l'outil dans 18 mois.
10. **Distinction popularité vs adéquation** : Un dépôt à 40 000 étoiles peut être obsolète, sur-dimensionné ou mal adapté ; un projet spécialisé à 800 étoiles maintenu par une organisation reconnue peut être bien plus pertinent.

## 5. Grille de comparaison multicritère (Build vs Buy vs Open Source)

Compare toujours les options crédibles selon des critères explicites dans `docs/02-research/research-report.md` :

| Solution / Option | Type (SaaS / OSS / Sur-mesure) | Couverture fonctionnelle | Stack & Intégration | Licence | Maturité & Activité | Coût (Initial & Run) | Limites & Risques | Source & Date de vérification |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |

## 6. Synthèse décisionnelle attendue en fin de recherche

Toute étude de l'existant se conclut par :
- **Enseignements produit & UX** : Ce que les solutions existantes font bien et les irritants que notre produit doit éviter.
- **Arbitrage Build vs Reuse** : Ce qui doit être réutilisé (bibliothèques, services), ce qui doit être configuré et ce qui constitue le cœur différenciant à développer sur mesure.
- **Recommandation argumentée** (`[RECOMMANDATION]` / `[DECISION PROPOSEE]`) reliée aux futurs ADR (`docs/adr/ADR-NNN.md`).
