## Schema

```sql
DROP TABLE IF EXISTS Thresholds CASCADE;

-- SCHEMA
CREATE TABLE Thresholds (
    -- General
    threshold_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    name CHARACTER VARYING(255) UNIQUE NOT NULL,
    value DECIMAL NOT NULL
);
```

## Example-Entries

```sql
-- EXAMPLE-DATA
INSERT INTO Thresholds (created, updated, name, value)
VALUES (now(), now(), 'Audi A1', 120);

INSERT INTO Thresholds (created, updated, sensor_id, distance, measured)
VALUES (now(), now(), 1, 121, now());

INSERT INTO Thresholds (created, updated, sensor_id, distance, measured)
VALUES (now(), now(), 1, 119, now());
```
