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
    date TIMESTAMP WITH TIME ZONE NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
VALUES (now(), now(), 1, 120, '2016-05-08T00:00:00.000Z');

INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
VALUES (now(), now(), 1, 125, '2016-05-09T00:00:00.000Z');

INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
VALUES (now(), now(), 1, 130, '2016-05-10T00:00:00.000Z');

INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
VALUES (now(), now(), 1, 135, '2016-05-11T00:00:00.000Z');

INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
VALUES (now(), now(), 1, 136, '2016-05-12T00:00:00.000Z');

INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
VALUES (now(), now(), 1, 138, '2016-05-13T00:00:00.000Z');

INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
VALUES (now(), now(), 1, 137, '2016-05-14T00:00:00.000Z');

INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
VALUES (now(), now(), 1, 130, '2016-05-15T00:00:00.000Z');

-- INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
-- VALUES (now(), now(), 1, 125, '2016-05-16T00:00:00.000Z');

-- INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
-- VALUES (now(), now(), 1, 120, '2016-05-17T00:00:00.000Z');

-- INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
-- VALUES (now(), now(), 1, 119, '2016-05-18T00:00:00.000Z');

-- INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
-- VALUES (now(), now(), 1, 118, '2016-05-19T00:00:00.000Z');

-- INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
-- VALUES (now(), now(), 1, 119, '2016-05-20T00:00:00.000Z');

-- INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
-- VALUES (now(), now(), 1, 120, '2016-05-21T00:00:00.000Z');

-- INSERT INTO Timeseries (created, updated, sensor_id, distance, date)
-- VALUES (now(), now(), 1, 121, '2016-05-22T00:00:00.000Z');
```
