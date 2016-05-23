```sql
DROP TABLE IF EXISTS Sensors CASCADE;

-- SCHEMA
CREATE TABLE Sensors (

    -- General
    sensor_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    created_by CHARACTER VARYING(255) NOT NULL REFERENCES Users (username) ON UPDATE CASCADE ON DELETE CASCADE,
    device_id CHARACTER VARYING(255) UNIQUE NOT NULL,
    description CHARACTER VARYING(255) NOT NULL,
    private BOOLEAN NOT NULL,
    water_body_id INTEGER REFERENCES Water_Bodies (water_body_id) ON UPDATE CASCADE ON DELETE CASCADE,
    sensor_height DECIMAL NOT NULL CONSTRAINT positive_value CHECK (sensor_height > 0), -- example: height of the sensor to the Gauge-Zero of the river
    crossing_height DECIMAL NOT NULL CONSTRAINT positive_value_ CHECK (crossing_height >= 0), -- example: height of a bridge / floodway to the Gauge-Zero of the river
    threshold_value DECIMAL NOT NULL CONSTRAINT positive_value__ CHECK (threshold_value > 0),
    default_frequency INTEGER NOT NULL CONSTRAINT valid_frequency CHECK (default_frequency >= 1000),
    threshold_frequency INTEGER NOT NULL CONSTRAINT valid_frequency_ CHECK (threshold_frequency >= 1000),
    frequency_increased BOOLEAN NOT NULL,

    -- Coordinates
    coordinates GEOGRAPHY (POINT) NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Sensors (
    created, updated, created_by, device_id, description, private, water_body_id,
    sensor_height, crossing_height,
    threshold_value, frequency_increased,
    default_frequency, threshold_frequency,
    coordinates)
VALUES (
    now(), now(), 'vst-admin', 'RPi-1', 'Raspberry Pi at Wersehause', 'false', 1,
    320, 200,
    120, 'false',
    60000, 5000, -- 60000 = 1min, 5000 = 5sec
    'POINT(7.700130 51.973314)');

INSERT INTO Sensors (
    created, updated, created_by, device_id, description, private, water_body_id,
    sensor_height, crossing_height,
    threshold_value, frequency_increased,
    default_frequency, threshold_frequency,
    coordinates)
VALUES (
    now(), now(), 'nicho90', 'RPi-2', '2nd Raspberry Pi at Wersehause', 'true', 1,
    300, 220,
    120, 'false',
    600000, 60000, -- 600000 = 10min, 60000 = 1min
    'POINT(7.699556 51.973544)');

INSERT INTO Sensors (
    created, updated, created_by, device_id, description, private, water_body_id,
    sensor_height, crossing_height,
    threshold_value, frequency_increased,
    default_frequency, threshold_frequency,
    coordinates)
VALUES (
    now(), now(), 'nicho90', 'RPi-3', '3rd private Sensor', 'false', 1,
    300, 0,
    120, 'false',
    6000000, 300000, -- 6000000 = 1h, 300000 = 5min
    'POINT(7.698880 51.973934)');
```