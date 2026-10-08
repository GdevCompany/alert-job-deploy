# alert-job-deploy

Docker и compose для dev/prod. **Запускать compose только отсюда.**

## Зависимости (соседние клоны)

| Путь | Зачем |
|------|--------|
| `../alert-job-base/config` | nginx, prometheus, init SQL, loki/promtail (prod) |
| `../alert-job-config-repo` | Spring Cloud Config Server (native) |
| Образы `rg.gdev.by/alert-job/*` | Собираются из Java/ front репо (`mvn install` + docker plugin) или CI |

## Dev

```bash
cp env_sample.properties .env
docker compose build keycloak
docker compose up
```

Keycloak dev-образ: `keycloak/` (`docker compose build keycloak`).

## Prod

```bash
docker compose -f docker-compose-prod.yml --env-file .env up -d
```

Keycloak: `quay.io/keycloak/keycloak` (не кастомный образ из `keycloak/`).

## Java → образ

Dockerfile-шаблоны: `docker/`. В каждом сервисе parent копирует нужный Dockerfile при `mvn package` (см. parent POM в `alert-job-base`).
