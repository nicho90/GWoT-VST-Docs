```sql
DROP TABLE IF EXISTS Timeseries CASCADE;

-- SCHEMA
CREATE TABLE Timeseries (
    -- General
    timeserie_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    sensor_id INTEGER NOT NULL REFERENCES Sensors (sensor_id) ON UPDATE CASCADE ON DELETE CASCADE,
    water_level DECIMAL NOT NULL CONSTRAINT positive_value_ CHECK (water_level > 0),
    measurement_date DATE NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 51, '2016-05-08');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 50, '2016-05-09');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 52, '2016-05-10');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 54, '2016-05-11');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 53, '2016-05-12');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 55, '2016-05-13');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 52, '2016-05-14');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 51,'2016-05-15');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 52,'2016-05-16');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 50,'2016-05-17');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 51,'2016-05-18');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 52,'2016-05-19');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 54,'2016-05-20');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 59,'2016-05-21');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 58,'2016-05-22');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 56, '2016-05-23');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, measurement_date)
VALUES (now(), now(), 1, 54, '2016-05-24');
```
