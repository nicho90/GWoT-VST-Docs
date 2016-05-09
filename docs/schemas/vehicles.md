## Schema

```sql
DROP TABLE IF EXISTS Vehicles CASCADE;
DROP TYPE IF EXISTS types CASCADE;

-- ENUM
CREATE TYPE types AS ENUM ('BIKE', 'WHEELCHAIR', 'SCOOTER', 'MOTORBIKE', 'CAR');

-- SCHEMA
CREATE TABLE Vehicles (

    -- General
    vehicle_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    brand CHARACTER VARYING(255) NOT NULL,
    name CHARACTER VARYING(255) NOT NULL,
    year CHARACTER VARYING(255)

    -- Role
    type types
);
```

## Example-Entries

```sql
-- EXAMPLE-DATA
INSERT INTO Vehicles (created, updated, brand, name, year, type)
VALUES (now(), now(), 'VW', 'Golf', '2015', 'CAR');
INSERT INTO Vehicles (created, updated, brand, name, year, type)
VALUES (now(), now(), 'Audi', 'A1', '2014', 'CAR');
INSERT INTO Vehicles (created, updated, brand, name, year, type)
VALUES (now(), now(), 'Toyota', 'Tundra SR5', '2016', 'CAR');
```
