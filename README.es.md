# Sistema de Reserva de Salas (UCU) — Proyecto académico (BD1)

Sistema liviano de reservas de salas para un obligatorio académico. La idea es que sea **fácil de correr y evaluar**:
Docker Compose, datos seed de demostración, reglas de negocio y endpoints de reportes para análisis de uso.

## Qué demuestra
- Enfoque BI: endpoints de reportes (horas pico, salas más usadas, uso por rol, no-shows, etc.)
- Fundamentos de datos/backend: esquema SQL, seed demo, diseño de API REST
- Reproducibilidad: setup con Docker Compose + smoke tests

## Ejecución rápida (Docker)
Requisitos: Docker Desktop

```bash
docker compose up -d --build
```

- UI: `http://127.0.0.1:8000/ui`
- Documentación API (OpenAPI): `http://127.0.0.1:8000/docs`
- Health: `http://127.0.0.1:8000/health`

### Resetear base demo (seed desde cero)
Borra el volumen de MySQL y reaplica el seed demo:

```bash
bash scripts/reset_demo.sh
```

## Variables de entorno
Copiá el `.env`:

```bash
cp .env.example .env
```

## Endpoints principales
- Auth: `/auth/login`, `/auth/me`
- Reservas: `/reservas`, `/reservas/{id}/asistencia`, `/disponibilidad`
- Datos base: `/edificios`, `/salas`, `/turnos`, `/participantes`, `/sanciones`

### Reportes
Ver listado completo en `README.md` (sección Reporting).

## Estructura
- `src/` API FastAPI + UI mínima
- `sql/` schema + seed demo (solo `00_schema.sql` y `seed_demo.sql`)
- `docs/` ERD y archivo de SQL legacy en `docs/archive/`
