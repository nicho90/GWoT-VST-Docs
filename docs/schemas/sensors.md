## Schema

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
    sensor_height DECIMAL NOT NULL
);
```

## Example-Entries

```sql
-- EXAMPLE-DATA
INSERT INTO Sensors (created, updated, created_by, device_id, description, private, coordinates, sensor_height)
VALUES (now(), now(), 'vst-admin', 'RPi-1', 'Raspberry Pi at Wersehause', 'false', ST_GeomFromText('POINT(51.973314 7.700130)', 4326), 320);

INSERT INTO Sensors (created, updated, created_by, device_id, description, private, coordinates, sensor_height)
VALUES (now(), now(), 'vst-admin', 'RPi-2', '2nd Raspberry Pi at Wersehause', 'true', ST_GeomFromText('POINT(51.973544 7.699556)', 4326), 300);
```
