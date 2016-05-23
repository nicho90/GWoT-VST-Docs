```sql
DROP TABLE IF EXISTS Measurements CASCADE;

-- SCHEMA
CREATE TABLE Measurements (

    -- General
    measurement_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    sensor_id INTEGER NOT NULL REFERENCES Sensors (sensor_id) ON UPDATE CASCADE ON DELETE CASCADE,
    distance DECIMAL NOT NULL CONSTRAINT positive_value CHECK (distance > 0), -- measured distance
    water_level DECIMAL NOT NULL CONSTRAINT positive_value_ CHECK (water_level > 0), -- (water_level = sensor-height - distance)
    measured TIMESTAMP WITH TIME ZONE NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measured)
VALUES (now(), now(), 1, 120, 130, '2016-05-08T09:43:01.010Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measured)
VALUES (now(), now(), 1, 121, 129'2016-05-08T10:44:01.123Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measured)
VALUES (now(), now(), 1, 119, 131, '2016-05-08T11:45:01.005Z');
```
