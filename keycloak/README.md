# Keycloak (dev)

Кастомный образ для локального `docker-compose.yml`: realm `myrealm` и пользователи запекаются при сборке (`kc.sh import`).

```bash
# вручную (тот же тег, что в compose)
./build.sh
# или из корня deploy
docker compose build keycloak
```

Prod (`docker-compose-prod.yml`) использует `quay.io/keycloak/keycloak` без этого образа.
