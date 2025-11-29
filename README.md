# Study Rooms Reservation System (UCU) — Academic Project (BD1)

A lightweight room reservation system built for an academic assignment at Universidad Católica del Uruguay.
It’s designed to be **easy to run and easy to evaluate**: Dockerized services, seeded demo data, business rules,
and reporting endpoints for usage insights.

## What this demonstrates
- BI-minded analytics: reporting endpoints (peak times, most used rooms, usage by role, no-shows, etc.)
- Data + backend fundamentals: SQL schema, seeded demo dataset, REST API design
- Reproducibility: one-command Docker Compose setup + smoke tests

## Quickstart (Docker)
Prereqs: Docker Desktop

```bash
docker compose up -d --build
```

- UI: `http://127.0.0.1:8000/ui`
- API docs (OpenAPI): `http://127.0.0.1:8000/docs`
- Health check: `http://127.0.0.1:8000/health`

### Reset demo database (fresh seed)
This removes the MySQL volume and re-applies the demo seed.

```bash
bash scripts/reset_demo.sh
```

## Environment
Copy the example env file:

```bash
cp .env.example .env
```

Compose supports:
- `DB_PORT` (default 3306)
- `API_PORT` (default 8000)

## Key endpoints
- Auth: `/auth/login`, `/auth/me`
- Reservations: `/reservas`, `/reservas/{id}/asistencia`, `/disponibilidad`
- Master data: `/edificios`, `/salas`, `/turnos`, `/participantes`, `/sanciones`

### Reporting (BI-style)
- `/reportes/salas-mas-usadas`
- `/reportes/turnos-mas-demandados`
- `/reportes/uso-por-rol`
- `/reportes/reservas-y-asistencias-por-rol`
- `/reportes/ocupacion-por-edificio`
- `/reportes/sanciones-por-rol`
- `/reportes/top-participantes`
- `/reportes/efectividad-reservas`
- `/reportes/salas-no-show`
- `/reportes/promedio-participantes-por-sala`
- `/reportes/reservas-por-carrera-facultad`
- `/reportes/distribucion-semana-turno`

## Tests
Pytest suite lives in `tests/`. Smoke scripts are available under `scripts/`.

```bash
powershell -ExecutionPolicy Bypass -File scripts/smoke_full.ps1
```

## Repository layout
- `src/` FastAPI app + minimal UI (`/ui`)
- `sql/` database schema + demo seed used by Docker (only `00_schema.sql` and `seed_demo.sql`)
- `docs/` includes ERD (`docs/bd1_salas_erd.drawio`) and archived legacy SQL under `docs/archive/`

---

Spanish README: see `README.es.md`.
