# application-service

Gère les candidatures. Base : PostgreSQL. Publie des événements RabbitMQ.

## API
| Méthode | Endpoint | Rôle | Codes |
|---|---|---|---|
| POST | `/api/applications` | CANDIDATE | 201, 400, 404 (offre), 409 (déjà postulé) |
| GET | `/api/applications/me` | CANDIDATE | 200 |
| GET | `/api/applications/offer/{offerId}` | RECRUITER | 200, 403 |
| PATCH | `/api/applications/{id}/status` | RECRUITER | 200, 403, 404 |

## Événements (RabbitMQ)
- `application.submitted` : `{applicationId, offerId, candidateId, recruiterId, date}`
- `application.status.changed` : `{applicationId, candidateId, newStatus}`
