# PostgresSQL Cheatsheet

1. Backup and restore with CLI
    ```bash
    sudo apt-get install postgresql-client

    # backup
    PGPASSWORD=$PASSWORD pg_dump -U $USERNAME -h $URL -p $PORT -n $SCHEMA $DATABASE > dump-file.sql

    # restore
    PGPASSWORD=$PASSWORD psql -U $USERNAME -h $URL -p $PORT $DATABASE < dump-file.sql
    ```

1. Access the database via CLI
    ```bash
    PGPASSWORD=$PASSWORD psql -U $USERNAME -h $URL -p $PORT $DATABASE
    ```

1. foreign keys are not indexed per se -- they are only indexed on the external table as primary keys. So don't forget to index them manually

1. Best timestamp format: `timestamptz NOT NULL DEFAULT CURRENT_TIMESTAMP`

1. Postgres has enums:
    ```postgres
    CREATE TYPE partyws.some_enum AS ENUM ('FOO', 'BAR');
    ```

1. Debug query performance with `EXPLAIN ANALYZE ...`

1. Mock DB for tests:
    ```bash
    npm i -D @shelfio/jest-postgres
    ```

1. For a big dynamic list of lookup values, prefix the query with a `WITH ... VALUES` table and join against it instead of building huge `IN (...)`/`OR` chains. This will make it much faster. Always confirm with `EXPLAIN ANALYZE`.
    ```sql
    WITH wanted(id) AS (
      VALUES (101), (205), (309)
    )
    SELECT p.*
    FROM posts p
    JOIN wanted w ON w.id = p.id;
    ```
