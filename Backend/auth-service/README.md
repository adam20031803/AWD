# auth-service

**Microservice commun.** Gère les comptes, les rôles (`CANDIDATE`, `RECRUITER`, `ADMIN`) et l'émission des JWT. Base : PostgreSQL.

## API
| Méthode | Endpoint | Description | Codes |
|---|---|---|---|
| POST | `/api/auth/register` | Créer un compte | 201, 400, 409 |
| POST | `/api/auth/login` | Connexion, retourne un JWT | 200, 401 |
| GET | `/api/users/me` | Profil de l'utilisateur connecté | 200, 401 |
| GET | `/api/users/{id}` | Infos d'un utilisateur | 200, 401, 404 |
| DELETE | `/api/users/{id}` | Supprimer un compte (ADMIN) | 204, 403, 404 |
