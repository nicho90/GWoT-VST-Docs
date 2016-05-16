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
    coordinates GEOMETRY NOT NULL,
    sensor_height DECIMAL NOT NULL CONSTRAINT positive_value CHECK (sensor_height > 0)
);


-- EXAMPLE-DATA
INSERT INTO Sensors (created, updated, created_by, device_id, description, private, coordinates, sensor_height)
VALUES (now(), now(), 'vst-admin', 'RPi-1', 'Raspberry Pi at Wersehause', 'false', ST_GeomFromText('POINT(51.973314 7.700130)', 4326), 320);

INSERT INTO Sensors (created, updated, created_by, device_id, description, private, coordinates, sensor_height)
VALUES (now(), now(), 'nicho90', 'RPi-2', '2nd Raspberry Pi at Wersehause', 'false', ST_GeomFromText('POINT(51.973544 7.699556)', 4326), 300);

INSERT INTO Sensors (created, updated, created_by, device_id, description, private, coordinates, sensor_height)
VALUES (now(), now(), 'nicho90', 'RPi-3', '3rd private Sensor', 'true', ST_GeomFromText('POINT(51.973934 7.698880)', 4326), 300);
```
