# Sécurité, Confidentialité et Gestion des Risques

## 1. Philosophie Security-by-Design

La sécurité et la protection des données se conçoivent dès l'analyse des besoins et l'architecture (`docs/05-architecture/security.md`), de manière **proportionnée aux actifs réels et au profil de risque du projet**. Ne prétends jamais « certifier » un système sur la seule base d'un dossier d'architecture, mais garantis que chaque menace crédible dispose d'une mesure de réduction explicite.

## 2. Modèle de menaces simplifié (Threat Modeling)

Identifie systématiquement :
1. **Actifs critiques à protéger** : Données personnelles (PII), identifiants/sessions, flux financiers, propriété intellectuelle, clés d'API tierces, disponibilité du service.
2. **Frontières de confiance (Trust Boundaries)** : Navigateur/App mobile <-> API publique <-> Services internes <-> Base de données <-> Prestataires externes.
3. **Scénarios d'abus et d'attaque** : Usurpation d'identité, accès non autorisé aux données d'un autre client (IDOR / BOLA), injection (SQL, XSS, commande, prompt injection si IA), élévation de privilèges, déni de service / épuisement de quotas payants (SMS, LLM, stockage), fuite de secrets.

## 3. Contrôles de sécurité essentiels à spécifier

- **Authentification et cycle de vie des sessions** :
  - Standard éprouvé (OIDC/OAuth2, sessions HTTP-only `Secure` `SameSite`, JWT à durée de vie courte + rotation de refresh tokens, MFA si sensible).
  - Hachage robuste des mots de passe (`Argon2id` ou `bcrypt`), flux de réinitialisation sécurisé sans énumération de comptes.
- **Autorisation et moindre privilège** :
  - Matrice des permissions par rôle (`ACT-xxx`) et vérification systématique de l'appartenance de la ressource (Row-Level Security ou contrôle applicatif centralisé).
- **Validation des entrées et sécurité des fichiers** :
  - Validation de schéma stricte côté serveur sur toutes les entrées.
  - Pour les téléversements (uploads) : vérification du type MIME réel (magic bytes), limite de taille, renommage aléatoire, stockage hors de la racine exécutable, URLs signées temporaires pour les fichiers privés.
- **Protection des communications et des secrets** :
  - TLS (HTTPS) obligatoire partout, chiffrement au repos des données sensibles.
  - Aucun secret dans le code source ni dans le bundle client frontend ; injection par gestionnaire de secrets ou variables d'environnement serveur isolées par environnement.
- **Anti-abus, Rate Limiting et Sécurité IA (si applicable)** :
  - Quotas par utilisateur et par IP sur les routes sensibles (login, inscription, paiement, génération IA, envoi d'e-mails/SMS).
  - Pour les projets IA/LLM : séparation stricte instructions système / entrées utilisateur, validation des sorties, plafonnement budgétaire des tokens et interdiction d'exécuter du code ou des actions destructrices sans confirmation humaine.
- **Journalisation d'audit sécurisée** :
  - Tracer les événements sensibles (connexions, échecs d'auth, changements de droits, suppressions, transactions) **sans jamais journaliser de mots de passe, jetons, numéros de carte ou données sensibles en clair**.

## 4. Confidentialité et protection des données personnelles (RGPD / Privacy)

Documente :
- Les catégories de données personnelles collectées et leur finalité exacte (principe de minimisation : ne collecter que ce qui est indispensable au service).
- La durée de conservation et les règles de purge/anonymisation.
- La prise en charge dès l'UX/UI (`SCR-xxx`) et l'API des droits des utilisateurs : consultation, rectification, export et suppression de compte.
- Mentionne clairement les points nécessitant la validation d'un juriste ou DPO (`[POINT EN ATTENTE : validation juridique/DPO]`).

## 5. Registre des risques (`docs/06-quality/risk-register.md`)

Évalue chaque risque (`RISK-001`...) — qu'il soit technique, sécurité, produit, UX, dépendance tierce ou opérationnel — sur une échelle qualitative cohérente (**Faible / Moyen / Élevé / Critique**) :

| ID | Catégorie | Scénario de risque & Cause | Probabilité | Impact | Niveau initial | Mesure de prévention / mitigation | Responsable | Risque résiduel |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
