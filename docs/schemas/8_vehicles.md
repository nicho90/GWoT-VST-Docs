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
    warning_height DECIMAL NOT NULL CONSTRAINT positive_value CHECK (warning_height > 0), -- example: wheel height
    danger_height DECIMAL NOT NULL CONSTRAINT positive_value_ CHECK (danger_height > 0 AND danger_height > warning_height), -- example: door height

    -- Category
    category vehicle_types
);


-- EXAMPLE-DATA
INSERT INTO Vehicles (created, updated, brand, name, year, category, warning_height, danger_height)
VALUES (now(), now(), 'Yamaha', 'Aerox R', '2015', 'SCOOTER', 5, 10);

INSERT INTO Vehicles (created, updated, brand, name, year, category, warning_height, danger_height)
VALUES (now(), now(), 'Yamaha', 'MT-03', '2015', 'MOTORBIKE', 5, 10);

INSERT INTO Vehicles (created, updated, brand, name, year, category, warning_height, danger_height)
VALUES (now(), now(), 'VW', 'Golf', '2015', 'CAR', 10, 20);

INSERT INTO Vehicles (created, updated, brand, name, year, category, warning_height, danger_height)
VALUES (now(), now(), 'Audi', 'A1', '2014', 'CAR', 10, 15);

INSERT INTO Vehicles (created, updated, brand, name, year, category, warning_height, danger_height)
VALUES (now(), now(), 'Toyota', 'Tundra SR5', '2016', 'CAR', 20, 30);
```
