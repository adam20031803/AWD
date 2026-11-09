# JobBoard — Plateforme de recherche d'emploi (Projet AWD)

Application web distribuée basée sur une **architecture microservices** : les recruteurs publient des offres, les candidats postulent, les événements sont échangés de façon asynchrone.

> Étudiant : Adam — Travail individuel — Validation intermédiaire (séance 4)

## Structure du dépôt

```
AWD/
├── Backend/
│   ├── api-gateway/          # Point d'entrée unique, validation JWT, routage
│   ├── discovery-server/     # Eureka (registre de services)
│   ├── auth-service/         # Microservice commun : utilisateurs, rôles, JWT
│   ├── offer-service/        # Offres d'emploi
│   └── application-service/  # Candidatures + publication d'événements
├── Frontend/                 # Application cliente (Angular)
├── Documentation/
│   ├── Presentation/         # Plan de la présentation (séance 4)
│   ├── Diagrams/             # Architecture, classes, séquences (Mermaid)
│   └── dossier-technique.md  # Dossier technique
└── README.md
```

## Technologies (prévues)

| Couche | Choix |
|---|---|
| Backend | Spring Boot 3, Spring Cloud Gateway, Eureka |
| Sécurité | Spring Security + JWT |
| Bases de données | PostgreSQL (auth, applications), MongoDB (offres) |
| Messagerie | RabbitMQ |
| Frontend | Angular |
| Conteneurs | Docker / Docker Compose |
| Gestion de projet | GitHub Projects (Kanban) + Issues |

## Documentation

- [Dossier technique](Documentation/dossier-technique.md)
- [Diagrammes](Documentation/Diagrams/)
- [Plan de présentation](Documentation/Presentation/plan-presentation.md)

## Workflow Git

- `main` : version stable
- `develop` : intégration
- `feature/<service>-<fonction>` : une branche par fonctionnalité
- Commits au format : `feat(offer): add search endpoint`

## Statut

Conception validée (séance 4). Développement en cours.
