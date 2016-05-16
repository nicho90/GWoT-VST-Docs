```sql
DROP TABLE IF EXISTS Vehicles CASCADE;
DROP TYPE IF EXISTS vehicle_types CASCADE;

-- ENUM
CREATE TYPE vehicle_types AS ENUM ('BIKE', 'WHEELCHAIR', 'SCOOTER', 'MOTORBIKE', 'CAR', 'TRUCK');

-- SCHEMA
CREATE TABLE Vehicles (

    -- General
    vehicle_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    brand CHARACTER VARYING(255) NOT NULL,
    name CHARACTER VARYING(255) NOT NULL,
    year CHARACTER VARYING(255),

    -- Category
    category vehicle_types
);


-- EXAMPLE-DATA
INSERT INTO Vehicles (created, updated, brand, name, year, category)
VALUES (now(), now(), 'Yamaha', 'Aerox R', '2015', 'SCOOTER');

INSERT INTO Vehicles (created, updated, brand, name, year, category)
VALUES (now(), now(), 'Yamaha', 'MT-03', '2015', 'MOTORBIKE');

INSERT INTO Vehicles (created, updated, brand, name, year, category)
VALUES (now(), now(), 'VW', 'Golf', '2015', 'CAR');

INSERT INTO Vehicles (created, updated, brand, name, year, category)
VALUES (now(), now(), 'Audi', 'A1', '2014', 'CAR');

INSERT INTO Vehicles (created, updated, brand, name, year, category)
VALUES (now(), now(), 'Toyota', 'Tundra SR5', '2016', 'CAR');
```
