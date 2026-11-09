# api-gateway

Spring Cloud Gateway. Valide le JWT, route vers les services via Eureka.

| Route | Service |
|---|---|
| `/api/auth/**` | auth-service (public : register, login) |
| `/api/offers/**` | offer-service |
| `/api/applications/**` | application-service |
