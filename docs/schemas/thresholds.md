## Schema

```sql
DROP TABLE IF EXISTS Thresholds CASCADE;
DROP TYPE IF EXISTS thresholds_types CASCADE;

-- ENUM
CREATE TYPE thresholds_types AS ENUM ('PEDESTRIAN', 'BIKE', 'WHEELCHAIR', 'SCOOTER', 'MOTORBIKE', 'CAR', 'TRUCK');

-- SCHEMA
CREATE TABLE Thresholds (
    -- General
    threshold_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    username CHARACTER VARYING(255) NOT NULL REFERENCES Users (username) ON UPDATE CASCADE ON DELETE CASCADE,
    description CHARACTER VARYING(255) NOT NULL,
    value DECIMAL NOT NULL CONSTRAINT positive_value CHECK (value > 0),

    -- Category
    category thresholds_types NOT NULL
);
```

## Example-Entries

```sql
-- EXAMPLE-DATA
INSERT INTO Thresholds (created, updated, username, category, description, value)
VALUES (now(), now(), 'nicho90', 'PEDESTRIAN', 'Myself', 50);

INSERT INTO Thresholds (created, updated, username, category, description, value)
VALUES (now(), now(), 'nicho90', 'CAR', 'VW Golf (2015)', 20);

INSERT INTO Thresholds (created, updated, username, category, description, value)
VALUES (now(), now(), 'nicho90', 'CAR', 'Yamaha MT-03 (2015)', 13);

INSERT INTO Thresholds (created, updated, username, category, description, value)
VALUES (now(), now(), 'vst-admin', 'CAR', 'Audi A1', 21);

INSERT INTO Thresholds (created, updated, username, category, description, value)
VALUES (now(), now(), 'vst-admin', 'CAR', 'Toyota Tundra (2016)', 35);
```
