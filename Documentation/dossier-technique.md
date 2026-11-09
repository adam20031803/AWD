# Dossier technique — JobBoard

## 1. Description du sujet
Les offres d'emploi et les candidatures sont souvent dispersées sur plusieurs canaux. JobBoard centralise la publication d'offres par les recruteurs et le dépôt de candidatures par les candidats, via une architecture microservices évolutive.

## 2. Acteurs et fonctionnalités
| Acteur | Fonctionnalités |
|---|---|
| Candidat | Inscription, connexion, recherche d'offres, candidature, suivi du statut |
| Recruteur | Publication/modification/suppression d'offres, consultation et traitement des candidatures |
| Administrateur | Gestion des utilisateurs, modération des offres |

Voir [cas d'utilisation](Diagrams/use-cases.md).

## 3. Découpage en microservices
| Service | Responsabilité | Base de données | Justification |
|---|---|---|---|
| api-gateway | Point d'entrée, validation JWT, routage | - | Sécurité centralisée |
| discovery-server | Registre Eureka | - | Découverte dynamique |
| auth-service (commun) | Comptes, rôles, JWT | PostgreSQL | Données relationnelles, intégrité |
| offer-service | Offres d'emploi | MongoDB | Schéma flexible, recherche textuelle |
| application-service | Candidatures, statuts | PostgreSQL | Transactions et contraintes d'unicité |

## 4. Données gérées par service
Voir [diagrammes de classes](Diagrams/class-diagrams.md). Chaque service possède sa propre base (database per service) ; aucune jointure inter-services : les références se font par identifiant (`recruiterId`, `offerId`, `candidateId`).

## 5. Interactions entre services
- **Synchrone (REST)** : application-service → offer-service pour vérifier l'existence de l'offre avant d'enregistrer une candidature.
- **Asynchrone (RabbitMQ)** : application-service publie `application.submitted` et `application.status.changed`. Un notification-service pourra les consommer (extension).

Voir [diagrammes de séquence](Diagrams/sequence-diagrams.md).

## 6. Architecture globale et sécurité
Voir [architecture](Diagrams/architecture.md). Le client n'appelle que l'API Gateway, qui valide le JWT (signé par auth-service) et transmet l'identité et le rôle aux services. Les mots de passe sont hachés (BCrypt).

## 7. Contrats d'API
Détaillés dans le README de chaque service (`Backend/<service>/README.md`).

## 8. Technologies
Spring Boot 3, Spring Cloud Gateway, Eureka, Spring Security/JWT, PostgreSQL, MongoDB, RabbitMQ, Angular, Docker Compose.

## 9. Organisation du travail
Travail individuel. Outil : GitHub Projects (Kanban : To do / In progress / Done). Branches `main`, `develop`, `feature/*`.

## 10. Planning prévisionnel
| Semaine | Objectif |
|---|---|
| 4 | Conception, dépôt Git, présentation |
| 5 | Discovery, Gateway, auth-service |
| 6 | offer-service |
| 7 | application-service + RabbitMQ |
| 8 | Frontend Angular |
| 9 | Docker Compose, tests, finalisation |

## 11. Risques
| Risque | Mitigation |
|---|---|
| Charge de travail (projet seul) | Périmètre réduit à 3 services, notification-service optionnel |
| Complexité de la sécurité JWT | Validation uniquement au Gateway au début |
| Intégration RabbitMQ | Prototype tôt (semaine 7) |
| Retard sur le frontend | Interface minimale, priorité à l'API |
