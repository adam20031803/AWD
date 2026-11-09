# Plan de présentation (10–15 min)

Étant donné le travail individuel, je présente toutes les parties.

| # | Diapositive | Durée |
|---|---|---|
| 1 | Titre + idée générale et problématique | 1 min |
| 2 | Acteurs et cas d'utilisation | 1 min |
| 3 | Fonctionnalités principales | 1 min |
| 4 | Architecture globale (gateway, sécurité, données, communications) | 2 min |
| 5 | Microservices, responsabilités et choix de bases de données | 1,5 min |
| 6 | Technologies choisies | 1 min |
| 7 | auth-service (commun) : classes + API | 1 min |
| 8 | offer-service : classes + API | 1 min |
| 9 | application-service : classes + API + événements | 1,5 min |
| 10 | Exemples de communication synchrone / asynchrone | 1 min |
| 11 | Organisation Git + GitHub Projects | 0,5 min |
| 12 | Planning prévisionnel et risques | 1 min |

## Speech de 1 minute par microservice (modèle)
« Le service X gère ... Il expose les endpoints ... Il stocke ses données dans ... Il communique avec ... de façon synchrone (REST) pour ... et publie l'événement ... de façon asynchrone. »
