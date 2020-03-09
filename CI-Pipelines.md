## Overall

* Only use docker-compose volumes in dev

## Backend

### Dockerfile

* Keep builds fast by pulling in the package lock and npm installing, then bringing in app files
* Put `node_modules` in `.dockerignore`
* Use `npm ci --only=production` to speed up builds
  * Won't have your test dependencies though

### Database Connections

* Development, test, and ci can all use the same default connection string
  * `postgres://postgres:password@db:5432`
  * `POSTGRES_PASSWORD=password` needs to be in all environments

## Frontend

* You have to use actual ports for the front-end and backend (but not the database)

## Tests

* All use internal network

### CI

* One-shot tests, use production builds

### E2E Tests

* Continuous tests
* Use volumes
