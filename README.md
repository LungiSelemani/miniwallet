# MiniWallet

Portefeuille électronique de type mobile money : création de portefeuilles,
dépôts, retraits et transferts entre utilisateurs, avec frais et plafonds.

Projet d'apprentissage conçu pour suivre un processus de développement
industriel, de la conception à la mise en production.

## Statut du projet

| Phase | Contenu | Statut |
|-------|---------|--------|
| 0 | Sprint 0 : fondations du projet | En cours |
| 1 | Fondations : utilisateurs, portefeuilles, dépôts, retraits | À venir |
| 2 | Transferts fiables et authentification | À venir |
| 3 | Rigueur financière : grand livre, idempotence, frais, plafonds | À venir |
| 4 | Système distribué : événements, notifications, réconciliation | À venir |
| 5 | Production : observabilité, tests de charge, déploiement | À venir |

## Documentation

- [Vision du produit](docs/vision.md) : problème, périmètre, principes.
- [Glossaire et règles d'or](docs/glossaire.md) : vocabulaire métier et
  règles techniques non négociables.
- [Guide de contribution](CONTRIBUTING.md) : branches, commits, pull requests.

## Stack technique

Java 25 (LTS), Spring Boot 4, Maven, PostgreSQL, Flyway, JUnit 5,
Testcontainers, Docker Compose, GitHub Actions.

## Prérequis

- **Git**
- **Java 25** (JDK, par exemple Eclipse Temurin)
- **Docker Desktop** (pour PostgreSQL et les tests d'intégration)

Maven n'est pas à installer : le projet fournit le Maven Wrapper (`mvnw`).

## Démarrage rapide

> Ces commandes seront fonctionnelles à la fin du Sprint 0.

```bash
git clone https://github.com/LungiSelemani/miniwallet.git
cd miniwallet
cp .env.example .env        # puis renseigner les valeurs dans .env
docker compose up -d        # démarre PostgreSQL
./mvnw spring-boot:run      # démarre l'application (Windows : .\mvnw.cmd)
```

Une fois l'application démarrée :

- État de santé : http://localhost:8080/actuator/health
- Documentation de l'API : http://localhost:8080/swagger-ui.html

## Lancer les tests

```bash
./mvnw verify               # Windows : .\mvnw.cmd verify
```

## Structure du projet

```
miniwallet/
├── docs/               Documentation (vision, glossaire, décisions)
├── src/                Code source et tests (à partir de l'étape 3)
├── .gitattributes      Règles de fins de ligne
├── .gitignore          Fichiers exclus de Git
└── README.md           Ce fichier
```