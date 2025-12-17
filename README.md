# zero2prod

Minimal Actix Web project used for learning/testing.

## Local test DB

This project uses a local Postgres instance for integration tests.
The repository includes a `configuration.yaml` used by tests. By default the test run in CI/local expects a Postgres instance with the credentials in that file.

To run a test Postgres container locally (recommended):

```bash
# start Postgres on host port 5433 (if 5432 is in use)
docker run --name zero2prod-postgres -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=password -e POSTGRES_DB=postgres -p 5433:5432 -d postgres:14

# run the tests
cargo test
```

If you prefer to use a different Postgres instance, update `configuration.yaml` with your `host`, `port`, `username`, and `password`.

## Notes

- `configuration.yaml` is currently ignored by `.gitignore` to make local overrides easier — add a project-specific configuration if desired.
- CI should start a test database or use a matrix that provides Postgres.

## Cleaning up

Stop and remove the test container when finished:

```bash
docker stop zero2prod-postgres && docker rm zero2prod-postgres
```
