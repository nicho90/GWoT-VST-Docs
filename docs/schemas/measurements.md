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
    distance DECIMAL NOT NULL CONSTRAINT positive_value CHECK (distance > 0),
    measured TIMESTAMP WITH TIME ZONE NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Measurements (created, updated, sensor_id, distance, measured)
VALUES (now(), now(), 1, 120, '2016-05-08T11:43:01.010Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, measured)
VALUES (now(), now(), 1, 121, '2016-05-08T11:44:01.123Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, measured)
VALUES (now(), now(), 1, 119, '2016-05-08T11:45:01.005Z');
```
