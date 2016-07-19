```sql
DROP TABLE IF EXISTS Sensors CASCADE;
DROP TYPE IF EXISTS crossing_types CASCADE;

-- ENUM
CREATE TYPE crossing_types AS ENUM ('FLOODWAY', 'BRIDGE', 'OTHER');

-- SCHEMA
CREATE TABLE Sensors (

    -- General
    sensor_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    creator CHARACTER VARYING(255) NOT NULL REFERENCES Users (username) ON UPDATE CASCADE ON DELETE CASCADE,
    device_id CHARACTER VARYING(255) UNIQUE NOT NULL,
    description CHARACTER VARYING(255) NOT NULL,
    private BOOLEAN NOT NULL,
    water_body_id INTEGER REFERENCES Water_Bodies (water_body_id) ON UPDATE CASCADE ON DELETE CASCADE,
    sensor_height DECIMAL NOT NULL CONSTRAINT positive_value CHECK (sensor_height > 0), -- example: height of the sensor to the Gauge-Zero of the river
    crossing_height DECIMAL NOT NULL CONSTRAINT positive_value_ CHECK (crossing_height >= 0), -- example: height of a bridge / floodway to the Gauge-Zero of the river
    threshold_value DECIMAL NOT NULL CONSTRAINT positive_value__ CHECK (threshold_value > 0),
    default_frequency INTEGER NOT NULL CONSTRAINT valid_frequency CHECK (default_frequency >= 5000),  -- is on the sensor devided by 5, so that it actually is 1000
    danger_frequency INTEGER NOT NULL CONSTRAINT valid_frequency_ CHECK (danger_frequency >= 5000), -- see default_frequency
    increased_frequency BOOLEAN NOT NULL DEFAULT 'false',
    triggered_threshold BOOLEAN NOT NULL DEFAULT 'false',
    triggered_weather BOOLEAN NOT NULL DEFAULT 'false',
    online_status BOOLEAN NOT NULL DEFAULT 'false',
    seasonal BOOLEAN NOT NULL,
    wet_season_begin SMALLINT,
    wet_season_end SMALLINT,
    dry_season_begin SMALLINT,
    dry_season_end SMALLINT,

    -- Crossing type
    crossing_type crossing_types NOT NULL,

    -- Coordinates
    coordinates GEOGRAPHY(POINT) NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'nicho90', 'rpi-1', 'Raspberry Pi at Wersehause', 'false', 1,
    'OTHER',
    600, 400,
    200, 'false', 'true',
    60000, 5000, -- 60000 = 1min, 5000 = 5sec
    'false', NULL, NULL, NULL, NULL,
    'POINT(7.700130 51.973314)'
);


INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'test-user', 'sensor-104781701', 'Südmühlenstraße', 'false', 1,
    'BRIDGE',
    600, 400,
    200, 'false', 'false', 'false', 'false',
    60000, 5000, -- 60000 = 1min, 5000 = 5sec
    'false', NULL, NULL, NULL, NULL,
    'POINT(7.696494 51.989063)'
);


INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'test-user', 'sensor-104781702', 'Warendorfer Straße', 'false', 1,
    'BRIDGE',
    600, 400,
    200, 'false', 'false', 'false', 'false',
    60000, 5000, -- 60000 = 1min, 5000 = 5sec
    'false', NULL, NULL, NULL, NULL,
    'POINT(7.699013 51.974153)'
);


INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'test-user', 'sensor-104781703', 'Wersetimpen', 'true', 1,
    'BRIDGE',
    600, 400,
    200, 'false', 'false', 'false', 'false',
    60000, 5000, -- 60000 = 1min, 5000 = 5sec
    'false', NULL, NULL, NULL, NULL,
    'POINT(7.703576 51.970164)'
);


INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'test-user', 'sensor-104781704', 'Pleistermühlenweg 1', 'false', 1,
    'BRIDGE',
    300, 0,
    120, 'false', 'false', 'false', 'false',
    6000000, 300000, -- 6000000 = 1h, 300000 = 5min
    'false', NULL, NULL, NULL, NULL,
    'POINT(7.702965 51.962995)'
);


INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'test-user', 'sensor-104781705', 'Pleistermühlenweg 2', 'false', 1,
    'BRIDGE',
    300, 220,
    120, 'false', 'false', 'false', 'false',
    600000, 60000, -- 600000 = 10min, 60000 = 1min
    'false', NULL, NULL, NULL, NULL,
    'POINT(7.702048 51.963458)'
);


INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'test-user', 'sensor-104781706', 'Wolbecker Straße', 'false', 1,
    'BRIDGE',
    300, 0,
    120, 'false', 'false', 'false', 'false',
    6000000, 300000,
    'false', NULL, NULL, NULL, NULL,
    'POINT(7.687832 51.946644)'
);


INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'test-user', 'sensor-104781707', 'Angelmoder Weg', 'false', 1,
    'BRIDGE',
    300, 0,
    120, 'false', 'false', 'false', 'false',
    6000000, 300000,
    'false', NULL, NULL, NULL, NULL,
    'POINT(7.698433 51.924358)'
);


-- Australian example entries
INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'test-user', 'sensor-255910281', 'Reedbeds Rd', 'false', 7,
    'FLOODWAY',
    300, 0,
    10, 'false', 'false', 'false', 'false',
    6000000, 600000, -- 1h, 10 min
    'true', 11, 4, 5, 10, -- Wet season November - April, Dry season May - October
    'POINT(130.979248 -12.780740)'
);

INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'test-user', 'sensor-255910282', 'Old Bynoe Rd', 'false', 7,
    'FLOODWAY',
    300, 0,
    10, 'false', 'false', 'false', 'false',
    6000000, 600000, -- 1h, 10 min
    'true', 11, 4, 5, 10, -- Wet season November - April, Dry season May - October
    'POINT(130.983581 -12.770264)'
);

INSERT INTO Sensors (
    created, updated, creator, device_id, description, private, water_body_id,
    crossing_type,
    sensor_height, crossing_height,
    threshold_value, increased_frequency, triggered_threshold, triggered_weather, online_status,
    default_frequency, danger_frequency,
    seasonal, wet_season_begin, wet_season_end, dry_season_begin, dry_season_end,
    coordinates)
VALUES (
    now(), now(), 'test-user', 'sensor-255910283', 'Cox Peninsula Rd', 'false', 7,
    'BRIDGE',
    300, 0,
    10, 'false', 'false', 'false', 'false',
    6000000, 600000, -- 1h, 10 min
    'true', 11, 4, 5, 10, -- Wet season November - April, Dry season May - October
    'POINT(130.965638 -12.742289)'
);
```
