# 🇲🇱 Mali Connecte (`connect.malihub.digital`)

Fournisseur d'Identité et SSO (IdP OIDC / OAuth2) pour l'écosystème numérique Malihub et les services publics partenaires.

Propulsé par [Authentik](https://goauthentik.io) sous Docker avec reverse-proxy Traefik et certificats SSL Let's Encrypt automatiques.

---

## 1. Fonctionnalités & Sécurité

- **Authentification sans mot de passe (Passkeys / WebAuthn)** : Connexion biométrique via smartphone (Android / iOS) ou ordinateur (TouchID, Windows Hello, clés FIDO2).
- **Standard OpenID Connect (OIDC)** : Émission de jetons JWT sécurisés pour l'ensemble des services web et portails applicatifs.
- **Gestion des Rôles & Habilitations (RBAC)** :
  - `platform_admins` : Super-administrateurs de la plateforme d'identité.
  - `services:admin` : Administrateurs et gestionnaires de services métiers.
  - `content:editor` : Éditeurs de contenus des sites institutionnels.
  - `users` : Usagers et citoyens accédant aux téléservices.

---

## 2. Démarrage Rapide

1. Cloner le dépôt :
   ```bash
   git clone git@github.com:malibub-digital/connect.git
   cd connect
   ```
2. Préparer les variables d'environnement :
   ```bash
   cp .env.example .env
   # Renseigner les variables secrètes dans .env (ignoré par Git)
   ```
3. Lancer la pile Docker :
   ```bash
   docker compose up -d
   ```

---

## 3. Raccordement d'un Service (Application OIDC)

Pour connecter une nouvelle application (ex: Astro, Next.js) :
- **Issuer** : `https://connect.malihub.digital/application/o/<slug>/`
- **Authorize URL** : `https://connect.malihub.digital/application/o/authorize/`
- **Token URL** : `https://connect.malihub.digital/application/o/token/`
- **Userinfo URL** : `https://connect.malihub.digital/application/o/userinfo/`
- **Scopes supportés** : `openid`, `profile`, `email`
