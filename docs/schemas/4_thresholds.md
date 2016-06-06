```sql
DROP TABLE IF EXISTS Subscriptions CASCADE;
DROP TABLE IF EXISTS Thresholds CASCADE;
DROP TYPE IF EXISTS thresholds_types CASCADE;

-- ENUM
CREATE TYPE thresholds_types AS ENUM ('PEDESTRIAN', 'BIKE', 'WHEELCHAIR', 'SCOOTER', 'MOTORBIKE', 'CAR', 'BUS', 'TRUCK', 'OTHER');

-- SCHEMA
CREATE TABLE Thresholds (
    -- General
    threshold_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    creator CHARACTER VARYING(255) NOT NULL REFERENCES Users (username) ON UPDATE CASCADE ON DELETE CASCADE,
    description CHARACTER VARYING(255) NOT NULL,
    warning_threshold DECIMAL NOT NULL CONSTRAINT positive_value CHECK (warning_threshold > 0),
    critical_threshold DECIMAL NOT NULL CONSTRAINT positive_value_ CHECK (warning_threshold > 0 AND critical_threshold > warning_threshold),

    -- Category
    category thresholds_types NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Thresholds (created, updated, creator, category, description, warning_threshold, critical_threshold)
VALUES (now(), now(), 'nicho90', 'PEDESTRIAN', 'Myself', 5, 50);

INSERT INTO Thresholds (created, updated, creator, category, description, warning_threshold, critical_threshold)
VALUES (now(), now(), 'nicho90', 'CAR', 'VW Golf (2015)', 10, 20);

INSERT INTO Thresholds (created, updated, creator, category, description, warning_threshold, critical_threshold)
VALUES (now(), now(), 'nicho90', 'MOTORBIKE', 'Yamaha MT-03 (2015)', 5, 10);

INSERT INTO Thresholds (created, updated, creator, category, description, warning_threshold, critical_threshold)
VALUES (now(), now(), 'vst-admin', 'CAR', 'Audi A1', 10, 15);

INSERT INTO Thresholds (created, updated, creator, category, description, warning_threshold, critical_threshold)
VALUES (now(), now(), 'vst-admin', 'CAR', 'Toyota Tundra (2016)', 20, 30);
```
