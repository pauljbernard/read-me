# PostgreSQL Schema

## Purpose
A PostgreSQL schema for [Project Name] intended to back a FastAPI microservice.
Replace `[Project Name]` with the name of your application throughout this file. Adjust sections as your project grows.

## Features
- Normalized table design following third normal form (3NF)
- Consistent naming conventions using `snake_case`
- `uuid` primary keys with `gen_random_uuid()`
- Timestamp fields `created_at` and `updated_at` managed by triggers
- Foreign key constraints with `ON DELETE`/`ON UPDATE` rules
- Indexing strategy for high-traffic columns
- Use of `CHECK` constraints for business rules
- Partitioning or sharding guidelines for large datasets
- Role-based access control setup
- Migration scripts managed by Alembic

## Getting Started
1. Install PostgreSQL and `psql` CLI.
2. Create a database user and a database for `[Project Name]`.
3. Place initialization scripts in `migrations/` and run them via Alembic.
4. Configure the connection string in your FastAPI service's `.env` file.
5. Use connection pooling (`asyncpg` or `psycopg`) in the FastAPI service.

## Schema Design Tips
Document key tables, relationships, and naming conventions here as your design evolves.

```
database/
├── migrations/      # Alembic or SQL migrations
├── seed/            # Optional seed data
└── README.md
```

## Non-Functional Requirements
- SQL scripts should be linted (e.g., with `sqlfluff`).
- Provide integration tests that validate the schema using `pytest`.
- Ensure migration scripts run in CI before merging.

## Global Standards

### Security Standards
- Store database credentials in environment variables, not source control.
- Apply least-privilege principle for database roles.
- Use SSL connections for all client connections.

### Logging Specifications
- Enable slow query logging for performance diagnostics.
- Centralize logs for analysis (e.g., use `pgAudit`).

### Error Handling
- Use transactional migrations so failures roll back safely.
- Document common error codes and how the FastAPI service should respond.

## Customization Notes
- Adapt the directory layout if your project requires additional scripts.
- Extend the features list with domain-specific guidelines.
