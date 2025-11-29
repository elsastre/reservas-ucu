# Architecture (high-level)

This project follows a simple 3-layer architecture:

1) Web UI (minimal pages under `/ui`)
2) REST API (FastAPI)
3) Relational database (MySQL)

Docker Compose runs the stack locally:
- `db` MySQL 8 container initialized from `sql/00_schema.sql` and `sql/seed_demo.sql`
- `api` FastAPI app served by Uvicorn

The goal is a reproducible demo: one command to run, consistent seeded data, and smoke tests to validate core rules.
