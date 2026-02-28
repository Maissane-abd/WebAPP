# Projet Linux : Application Web Multi-Services

**Auteur :** ABDALLAH Maïssane\
**Classe :** 3IWJ\
**Établissement :** ESGI

------------------------------------------------------------------------

## Contexte du projet

Dans le cadre de ma formation à l'ESGI, j'ai travaillé sur une
application web multi-services capable de gérer et d'afficher des
articles en temps réel.

⚠️ **Important : le code source (API Flask, serveur WebSocket,
front-end) était fourni.**\
L'objectif du projet n'était pas de développer la logique métier, mais
de :

-   Comprendre l'architecture fournie\
-   Configurer correctement les services sous Linux\
-   Mettre en place l'interconnexion des composants\
-   Assurer le déploiement propre et automatisé

Ce projet met en œuvre une architecture complète combinant :

-   Une API REST en Flask\
-   Un serveur WebSocket en Go\
-   Un reverse proxy Nginx\
-   Une interface front-end en HTML / JavaScript\
-   Une base de données SQLite\
-   Des services systemd pour l'automatisation

------------------------------------------------------------------------

# Objectifs fonctionnels

L'application permet :

-   ✅ L'affichage d'une liste d'articles\
-   ✅ L'ajout d'articles via API\
-   ✅ La mise à jour en temps réel grâce aux WebSockets\
-   ✅ L'envoi de notifications côté serveur et côté client\
-   ✅ Le routage centralisé des requêtes via Nginx

------------------------------------------------------------------------

# Architecture du projet

    Client (Navigateur)
            │
            ▼
         Nginx (Reverse Proxy)
            │
     ┌──────┴────────┐
     ▼               ▼
    Flask API      WebSocket (Go)
            │
            ▼
         SQLite

------------------------------------------------------------------------

# ⚙️ Technologies utilisées

## 1️⃣ Flask (Python) --- API REST

Flask est utilisé pour :

-   Gérer les routes HTTP (GET, POST)
-   Structurer l'API REST
-   Interagir avec SQLite via Flask-SQLAlchemy
-   Permettre la consultation et l'ajout d'articles

### Lancement :

``` bash
python app.py
```

Endpoint principal :

    http://myproject.local:5000/api/articles

------------------------------------------------------------------------

## 2️⃣ SQLite --- Base de données

-   Base relationnelle embarquée\
-   Stockage persistant des articles\
-   Fichier généré : `app.db`

------------------------------------------------------------------------

## 3️⃣ WebSocket en Go --- Notifications temps réel

Permet :

-   La gestion des connexions clients\
-   La réception des notifications envoyées par Flask\
-   La diffusion en temps réel aux clients connectés

Lancement :

``` bash
go run websocket.go
```

------------------------------------------------------------------------

## 4️⃣ Nginx --- Reverse Proxy

Permet de :

-   Rediriger les requêtes HTTP vers Flask\
-   Gérer les connexions WebSocket vers le serveur Go\
-   Exposer l'application via le port 80

Fichier de configuration :

    /etc/nginx/sites-available/myproject

------------------------------------------------------------------------

## 🌐 Domaine local personnalisé

Modification du fichier :

    /etc/hosts

Ajout :

    127.0.0.1 myproject.local

Accès à l'application :

    http://myproject.local

------------------------------------------------------------------------

## 5️⃣ Systemd --- Gestion des services

Emplacement des fichiers :

    /etc/systemd/system/

Commandes utilisées :

``` bash
sudo systemctl daemon-reload
sudo systemctl enable nomduservice
sudo systemctl start nomduservice
```

Objectif :

-   Démarrage automatique au boot\
-   Supervision des services\
-   Déploiement propre

------------------------------------------------------------------------

## 6️⃣ Tests avec Curl

``` bash
curl -X POST http://myproject.local/api/articles -H "Content-Type: application/json" -d '{"title":"Nouvel article"}'
```

------------------------------------------------------------------------

# 🧠 Compétences mises en œuvre

-   Configuration d'un environnement Linux\
-   Compréhension d'une architecture multi-services\
-   Configuration d'un reverse proxy\
-   Mise en place de services systemd\
-   Configuration réseau locale\
-   Tests via ligne de commande\
-   Gestion d'une base de données embarquée

------------------------------------------------------------------------

# 📌 Conclusion

Ce projet m'a permis de comprendre concrètement le fonctionnement d'une
architecture web complète sous Linux, même si le code applicatif était
fourni.

L'intérêt principal résidait dans :

-   L'intégration des différents services\
-   Leur configuration\
-   Leur orchestration\
-   Leur mise en production locale propre et automatisée

------------------------------------------------------------------------

👨‍💻 ABDALLAH Maïssane\
3IWJ -- ESGI
