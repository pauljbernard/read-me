# PostgreSQL Database

## Purpose
A PostgreSQL Database for '[Project Name]' intended to back a '[Framework Name]' microservice with RBAC, audit logging, partitioning, and advanced extensions.
 - Replace `[Project Name]` with the name of your application throughout this file. 
 - Replace `[DB Migration Tool]` with the name of your db migration tool throughout this file.
 - Replace `[Framework Name]` with the name of your framework throughout this file.
 - Every input after // (double forward slash) will be ignored by AI agent as they are considered to be a comment
 - Adjust sections as your project grows.

## Getting Started
1. Install PostgreSQL and `psql` CLI.
2. Create a root user and a database for a `[Project Name]`.
3. Enable the following extensions
    - pg_stat_statements	//Tracks execution statistics of all SQL statements. Crucial for performance tuning.
    - auto_explain	        //Automatically logs slow or costly queries with their execution plans.   
    - uuid-ossp	            //Functions to generate UUIDs (uuid_generate_v4() is widely used).
    - tablefunc	            //Crosstab (pivot) queries, great for reporting.
    - hstore	            //Key-value pairs in a single column, useful for semi-structured data.
    - intarray	            //Fast array operations for integer arrays.
    - btree_gin	            //Enables B-tree style indexing for GIN, improving composite indexing.
    - pg_trgm	            //Trigram similarity indexing, useful for fuzzy search.
    - citext                //text, but with case-insensitive
4. Database has a mandatory log table for storing error logs and other logs of interest
5. Database has a mandatory partition master table for storing table partition logic
6. Database has A role-based access control system
6. Place initialisation scripts in `ddl/` and run them via '[DB Migration Tool]'.

## Schema Design
- Normalised table design following the third normal form (3NF)
- Consistent naming conventions using `snake_case` lower case
- Place business logic into the public schema, the archive schema will be used for archiving
- Every table, column, relationship, view, function, and stored procedure must be commented
- Use of CHECK constraints to enforce business rules (e.g., `status IN ('A', 'I')`).
- Every foreign key column has an index on it
- Foreign key constraints with `ON DELETE`/`ON UPDATE` rules

### Naming conventions
- The table name is always plural
- View has vw_ prefix
- Function has fn_ prefix
- Stored procedure has spc_ prefix
- Trigger has trg_ prefix
- Index has idx_ prefix, and format is 'prefix + table name (singular)' + column name
- Foreign key column name format is 'parent table name (singular)' + uuid

### Table Design
- Standard columns in each table:
  - `uuid` (Primary key) with `gen_random_uuid()`
  - `partition_uuid` (FK)
  - `created_at`, `updated_at` (timestamps)
  - `status` (e.g., 'A' = Active, 'I' = Inactive)
  - `metadata` (jsonb, extensible for unstructured info)
- For text columns like name, address line, prefer to use case-insensitive types

## Documentation
Document key tables, relationships, and naming conventions here as your design evolves.
```
database/
├── ddl/        # `[DB Migration Tool]`
├── seed/       # Optional seed data
├── report/     # html report
└── README.md
```

## Functionality
- // Here, you can provide a description of the database's function. AI will use it to generate objects. If left empty, only mandatory tables will be created.
- // E.g. This database holds records about students and the classes they attend. Students are not limited to one school only; schools are usually part of a district.

## Non-Functional Requirements
- SQL scripts should be linted (e.g., with `sqlfluff`).
- Ensure migration scripts run in CI before merging.

## Global Standards

### Security Standards
- Store database credentials in environment variables, not source control.
- Apply the least-privilege principle for database roles.
- Use SSL connections for all client connections.

### Logging Specifications
- Enable slow query logging for performance diagnostics.
- Centralise logs for analysis (e.g., use `pgAudit`).
- Enable `log_min_duration_statement = 1000ms` to catch slow queries.

### Error Handling
- Use transactional migrations so failures roll back safely.
- Document common error codes and how the '[Framework Name]' service should respond.

### Customisation Notes
- Adapt the directory layout if your project requires additional scripts.
- Extend the features list with domain-specific guidelines.
- Add '[Framework Name]' specific guidelines.
