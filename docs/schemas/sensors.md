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
    sensor_height DECIMAL NOT NULL CONSTRAINT positive_value CHECK (sensor_height > 0),

    -- Coordinates
    coordinates GEOGRAPHY (POINT) NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Sensors (created, updated, created_by, device_id, description, private, sensor_height, coordinates)
VALUES (now(), now(), 'vst-admin', 'RPi-1', 'Raspberry Pi at Wersehause', 'false', 320, 'POINT(7.700130 51.973314)');

INSERT INTO Sensors (created, updated, created_by, device_id, description, private, sensor_height, coordinates)
VALUES (now(), now(), 'nicho90', 'RPi-2', '2nd Raspberry Pi at Wersehause', 'false', 300, 'POINT(7.699556 51.973544)');

INSERT INTO Sensors (created, updated, created_by, device_id, description, private, sensor_height, coordinates)
VALUES (now(), now(), 'nicho90', 'RPi-3', '3rd private Sensor', 'true', 300, 'POINT(7.698880 51.973934)');
```
