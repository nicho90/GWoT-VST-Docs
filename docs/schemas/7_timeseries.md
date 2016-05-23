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
    distance DECIMAL NOT NULL CONSTRAINT positive_value CHECK (distance > 0),
    measurement_date DATE
);


-- EXAMPLE-DATA
INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 120, '2016-05-08');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 125, '2016-05-09');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 130, '2016-05-10');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 135, '2016-05-11');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 136, '2016-05-12');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 138, '2016-05-13');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 137, '2016-05-14');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 130, '2016-05-15');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 125, '2016-05-16');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 120, '2016-05-17');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 119, '2016-05-18');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 118, '2016-05-19');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 119, '2016-05-20');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 120, '2016-05-21');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 121, '2016-05-22');

INSERT INTO Timeseries (created, updated, sensor_id, distance, measurement_date)
VALUES (now(), now(), 1, 122, '2016-05-23');
```
