# Sécurité des systèmes distribués - Oauth2, OIDC, Keycloak
### Auteur : Hafssa Miftah Idrissi
### Master : SDIA2
### Module : Systèmes distribués
### Année universitaire : 2026/2027

---
## Sécuriser une architecture micro-service Spring Angular avec Keycloak
---

#### Création du Micro Service Inventory Service

- Création du package entites : Avec l'entité Product annotée @Entity
- Création de package repository : Avec l'interface ProductRepository
- Création du package web avec le RestControlleur ProductRestController avec une méthode qui retourne la liste des produits et une autre qui retourne un produit par son id
- Test Avec CommandLineRunner et création des 3 produits
- Accès interdit sans passage via keycloak d'ou la nécessité à configurer la sécurité
    

---

