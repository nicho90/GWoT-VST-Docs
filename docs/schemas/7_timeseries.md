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
    water_level DECIMAL NOT NULL CONSTRAINT positive_value_ CHECK (water_level >= 0),
    sd_water_level DECIMAL NOT NULL CONSTRAINT positive_value_sd CHECK (sd_water_level >= 0),
    num_measurements INTEGER NOT NULL CONSTRAINT positive_value_num CHECK (num_measurements >= 0),
    measurement_date DATE NOT NULL,
    valid_data BOOLEAN NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 151, 0, 1, '2016-05-08', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 150, 0, 1, '2016-05-09', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-05-10', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 154, 0, 1, '2016-05-11', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 153, 0, 1, '2016-05-12', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 155, 0, 1, '2016-05-13', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-05-14', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 151, 0, 1, '2016-05-15', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-05-16', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 150, 0, 1, '2016-05-17', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 151, 0, 1, '2016-05-18', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-05-19', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 154, 0, 1, '2016-05-20', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 159, 0, 1, '2016-05-21', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 158, 0, 1, '2016-05-22', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 156, 0, 1, '2016-05-23', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 154, 0, 1, '2016-05-24', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 154, 0, 1, '2016-05-24', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 154, 0, 1, '2016-05-25', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 154, 0, 1, '2016-05-26', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 154, 0, 1, '2016-05-27', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 154, 0, 1, '2016-05-24', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 153, 0, 1, '2016-05-28', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 153, 0, 1, '2016-05-29', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-05-30', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-01', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 151, 0, 1, '2016-06-02', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-03', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-04', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-05', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 151, 0, 1, '2016-06-06', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-07', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-08', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 153, 0, 1, '2016-06-09', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-10', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-11', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-12', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-13', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-14', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-15', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-16', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-17', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-18', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-19', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-20', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-21', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-22', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-23', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-24', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-25', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-26', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-27', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-28', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-29', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-06-30', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-01', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-02', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-03', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-04', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-05', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-06', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-07', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-08', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-09', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-10', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-11', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-12', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-13', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-14', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-15', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-16', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-17', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-18', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-19', 'true');

INSERT INTO Timeseries (created, updated, sensor_id, water_level, sd_water_level, num_measurements, measurement_date, valid_data)
VALUES (now(), now(), 3, 152, 0, 1, '2016-07-20', 'true');
```
