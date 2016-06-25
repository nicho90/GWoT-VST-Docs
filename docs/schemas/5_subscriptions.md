```sql
DROP TABLE IF EXISTS Subscriptions CASCADE;

-- SCHEMA
CREATE TABLE Subscriptions (

    -- General
    subscription_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    creator CHARACTER VARYING(255) NOT NULL REFERENCES Users (username) ON UPDATE CASCADE ON DELETE CASCADE,
    sensor_id INTEGER NOT NULL REFERENCES Sensors (sensor_id) ON UPDATE CASCADE ON DELETE CASCADE,
    threshold_id INTEGER NOT NULL REFERENCES Thresholds (threshold_id) ON UPDATE CASCADE ON DELETE CASCADE,
    active BOOLEAN NOT NULL DEFAULT 'true',
    notified BOOLEAN NOT NULL DEFAULT 'false'
);


-- EXAMPLE-DATA
INSERT INTO Subscriptions (created, updated, creator, sensor_id, threshold_id, active, notified)
VALUES (now(), now(), 'nicho90', 1, 1, 'true', 'false');

INSERT INTO Subscriptions (created, updated, creator, sensor_id, threshold_id, active, notified)
VALUES (now(), now(), 'nicho90', 1, 2, 'true', 'false');

INSERT INTO Subscriptions (created, updated, creator, sensor_id, threshold_id, active, notified)
VALUES (now(), now(), 'nicho90', 1, 3, 'true', 'false');
```
