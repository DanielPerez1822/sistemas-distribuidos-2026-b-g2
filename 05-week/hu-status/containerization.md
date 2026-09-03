# MVP 1 Containerization Specification

## Objective

Package the Di Lucca MVP so the same artifact can run in development, QA and production. The design follows the environment and configuration practices described in [`local-setup.md`](../../../dlc-docs/10-devops/local-setup.md) and the architecture boundaries in [`hexagonal-architecture.md`](../../../dlc-docs/05-architecture/hexagonal-architecture.md).

## Image rules

- Use a multi-stage build: compile with the build image and ship only the runtime artifact.
- Pin the runtime major version and expose only the application port.
- Exclude `.env`, `.git`, test output and local dependencies through `.dockerignore`.
- Never copy credentials into an image layer.
- Configure database URLs, broker addresses and secrets through environment variables.

## Compose topology

```text
app network
  api-gateway  -> auth-service
               -> appointments-service
               -> clinical-service
               -> billing-service
  auth/appointments/billing -> PostgreSQL owned schemas
  clinical-service           -> MongoDB
```

Services communicate by Compose service name, never by hard-coded IP. Database data uses named volumes so restarting a container does not erase state.

## Required configuration

| Variable | Source | Secret? |
|---|---|---|
| `POSTGRES_URL` | environment | No |
| `POSTGRES_USER` | environment | No |
| `POSTGRES_PASSWORD` | secret manager/local ignored file | Yes |
| `MONGODB_URL` | environment | No |
| `JWT_SECRET` | secret manager/local ignored file | Yes |
| `*_SERVICE_URL` | environment | No |

## Acceptance checks

1. `docker compose config` resolves without committed secrets.
2. `docker compose up` starts the service containers and both database types.
3. `GET /health` reports `ok` only when required dependencies are ready.
4. The appointment walking skeleton persists data after an application restart.
5. The image contains no `.env`, `.git` or build toolchain.
6. The same tagged image is promoted through `develop`, `qa` and `main`.

The implementation and runtime output are pending because Dockerfiles and service source repositories are not included in this workspace.
