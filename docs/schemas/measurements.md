## Schema

```sql
DROP TABLE IF EXISTS Measurements CASCADE;

-- SCHEMA
CREATE TABLE Measurements (
    -- General
    measurement_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    sensor_id CHARACTER VARYING(255) UNIQUE NOT NULL,
    distance DECIMAL NOT NULL,
    measured TIMESTAMP WITH TIME ZONE NOT NULL
);
```

## Example-Entries

```sql
-- EXAMPLE-DATA
INSERT INTO Vehicles (created, updated, sensor_id, distance, measured)
VALUES (now(), now(), 1, 120, now());

INSERT INTO Vehicles (created, updated, sensor_id, distance, measured)
VALUES (now(), now(), 1, 121, now());

INSERT INTO Vehicles (created, updated, sensor_id, distance, measured)
VALUES (now(), now(), 1, 119, now());
```
