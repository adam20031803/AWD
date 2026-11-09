# offer-service

Gère les offres d'emploi. Base : MongoDB.

## API
| Méthode | Endpoint | Rôle | Codes |
|---|---|---|---|
| GET | `/api/offers?keyword=&location=&type=` | Tous | 200 |
| GET | `/api/offers/{id}` | Tous | 200, 404 |
| POST | `/api/offers` | RECRUITER | 201, 400, 401, 403 |
| PUT | `/api/offers/{id}` | RECRUITER (propriétaire) | 200, 403, 404 |
| DELETE | `/api/offers/{id}` | RECRUITER / ADMIN | 204, 403, 404 |
