# device-registry-service

device-registry-service — domain: devices

- **Port:** 8900
- **Language:** Python 3.11 + Flask
- **Database:** `devices` (Postgres, table `device_registry`)
- **Event bus:** Kafka

## API

| Method    | Path                       |
|-----------|----------------------------|
| GET       | `/api/device_registry/`          |
| POST      | `/api/device_registry/`          |
| GET       | `/api/device_registry/<id>`      |
| PUT/PATCH | `/api/device_registry/<id>`      |
| DELETE    | `/api/device_registry/<id>`      |
| GET       | `/health`                  |
| GET       | `/ready`                   |

## Events

**Publishes:** (none)
**Subscribes:** (none)

## HTTP peer dependencies

- `patients-service`
- `audit-log-service`

## Local dev

```bash
pip install -e ../../libs/py-healthcare-common
pip install -r requirements.txt
cp .env.example .env
(cd ../../infra && docker compose up -d postgres kafka kafka-init)
python -m app.main
```

## Tests

```bash
pytest
```
