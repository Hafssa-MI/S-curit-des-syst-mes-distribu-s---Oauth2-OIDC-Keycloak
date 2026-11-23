# Sécurité des systèmes distribués - Oauth2, OIDC, Keycloak
### Auteur : Hafssa Miftah Idrissi
### Master : SDIA2
### Module : Systèmes distribués
### Année universitaire : 2026/2027

---
## Sécuriser une architecture micro-service Spring Angular avec Keycloak
---

#### Installation et configuration de Keycloak avec Docker

Pour éviter d'installer Keycloak en local, nous utilisons son image Docker officielle (Keycloak 19). Le conteneur est lancé en mode développement, avec la création du compte administrateur au démarrage et un volume pour conserver la configuration :

```bash
docker run -d --name keycloak -p 8080:8080 \
  -e KEYCLOAK_ADMIN=admin \
  -e KEYCLOAK_ADMIN_PASSWORD=admin \
  -v keycloak_data:/opt/keycloak/data \
  quay.io/keycloak/keycloak:19.0.3 start-dev
```

La console d'administration est ensuite accessible sur `http://localhost:8080`. La configuration se fait directement depuis cette console :

- Création d'un **Realm** dédié à l'application, qui isole les utilisateurs, les clients et les rôles
- Création d'un **client** à sécuriser, avec l'authentification activée (Client authentication), les flux Standard flow et Direct access grants, ainsi que les Service accounts roles
- Création des **rôles** (USER, ADMIN) dans le realm
- Création des **utilisateurs**, avec un mot de passe non temporaire, puis affectation des rôles à chacun
- Test de l'authentification avec `curl` : grant de type password, refresh token et client credentials, puis analyse du contenu des JWT (Access Token et Refresh Token)

---

#### Création du Micro Service Inventory Service

- Création du package entites : Avec l'entité Product annotée @Entity
- Création de package repository : Avec l'interface ProductRepository
- Création du package web avec le RestControlleur ProductRestController avec une méthode qui retourne la liste des produits et une autre qui retourne un produit par son id
- Test Avec CommandLineRunner et création des 3 produits
- Accès interdit sans passage via keycloak d'ou la nécessité à configurer la sécurité
    ![img_1.png](img_1.png)

---