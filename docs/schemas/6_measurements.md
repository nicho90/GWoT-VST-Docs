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
    water_level DECIMAL NOT NULL CONSTRAINT positive_value_ CHECK (water_level >= 0), -- (water_level = sensor-height - distance)
    measurement_timestamp TIMESTAMP WITH TIME ZONE NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 2, 449, 151, '2016-07-21T12:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 2, 448, 152, '2016-07-21T13:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 2, 447, 153, '2016-07-21T14:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 2, 448, 152, '2016-07-21T15:00:00.000Z');


INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 3, 449, 151, '2016-07-21T12:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 3, 448, 152, '2016-07-21T13:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 3, 447, 153, '2016-07-21T14:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 3, 448, 152, '2016-07-21T15:00:00.000Z');


INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 4, 449, 151, '2016-07-21T12:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 4, 448, 152, '2016-07-21T13:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 4, 447, 153, '2016-07-21T14:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 4, 448, 152, '2016-07-21T15:00:00.000Z');


INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 5, 449, 151, '2016-07-21T12:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 5, 448, 152, '2016-07-21T13:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 5, 447, 153, '2016-07-21T14:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 5, 448, 152, '2016-07-21T15:00:00.000Z');


INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 6, 449, 151, '2016-07-21T12:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 6, 448, 152, '2016-07-21T13:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 6, 447, 153, '2016-07-21T14:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 6, 448, 152, '2016-07-21T15:00:00.000Z');


INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 7, 449, 151, '2016-07-21T12:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 7, 448, 152, '2016-07-21T13:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 7, 447, 153, '2016-07-21T14:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 7, 448, 152, '2016-07-21T15:00:00.000Z');



-- Australian example entries
INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 9, 285, 15, '2016-07-21T12:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 9, 285, 15, '2016-07-21T13:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 9, 285, 15, '2016-07-21T14:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 9, 285, 15, '2016-07-21T15:00:00.000Z');


INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 10, 295, 5, '2016-07-21T12:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 10, 295, 5, '2016-07-21T13:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 10, 295, 5, '2016-07-21T14:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 10, 295, 5, '2016-07-21T15:00:00.000Z');


INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 11, 299, 1, '2016-07-21T12:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 11, 299, 1, '2016-07-21T13:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 11, 299, 1, '2016-07-21T14:00:00.000Z');

INSERT INTO Measurements (created, updated, sensor_id, distance, water_level, measurement_timestamp)
VALUES (now(), now(), 11, 299, 1, '2016-07-21T15:00:00.000Z');
```
