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
    warning_notified BOOLEAN NOT NULL DEFAULT 'false',
    danger_notified BOOLEAN NOT NULL DEFAULT 'false'
);


-- EXAMPLE-DATA
INSERT INTO Subscriptions (created, updated, creator, sensor_id, threshold_id, warning_notified, danger_notified)
VALUES (now(), now(), 'nicho90', 1, 1, 'false', 'false');

INSERT INTO Subscriptions (created, updated, creator, sensor_id, threshold_id, warning_notified, danger_notified)
VALUES (now(), now(), 'nicho90', 1, 2, 'false', 'false');

INSERT INTO Subscriptions (created, updated, creator, sensor_id, threshold_id, warning_notified, danger_notified)
VALUES (now(), now(), 'nicho90', 1, 3, 'false', 'false');
```
