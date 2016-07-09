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
    avg_water_level DECIMAL NOT NULL CONSTRAINT positive_value_ CHECK (avg_water_level >= 0),
    sd_water_level DECIMAL NOT NULL CONSTRAINT positive_value_ CHECK (sd_water_level >= 0),
    num_measurements INTEGER NOT NULL CONSTRAINT positive_value_ CHECK (num_measurements >= 0),
    measurement_date DATE NOT NULL,
    valid_data BOOLEAN NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 51, 0, 1, '2016-05-08', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 50, 0, 1, '2016-05-09', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 52, 0, 1, '2016-05-10', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-11', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 53, 0, 1, '2016-05-12', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 55, 0, 1, '2016-05-13', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 52, 0, 1, '2016-05-14', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 51, 0, 1, '2016-05-15', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 52, 0, 1, '2016-05-16', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 50, 0, 1, '2016-05-17', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 51, 0, 1, '2016-05-18', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 52, 0, 1, '2016-05-19', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-20', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 59, 0, 1, '2016-05-21', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 58, 0, 1, '2016-05-22', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 56, 0, 1, '2016-05-23', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-24', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-24', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-25', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-26', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-27', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-24', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-28', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-29', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-05-30', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-01', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-02', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-03', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-04', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-05', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-06', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-07', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-08', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-09', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-10', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, avg_water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 1, 54, 0, 1, '2016-06-11', 'true');
```
