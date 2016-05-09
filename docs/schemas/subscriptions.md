## Schema

```sql
DROP TABLE IF EXISTS Subscriptions CASCADE;

-- SCHEMA
CREATE TABLE Subscriptions (
    -- General
    subscription_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    username CHARACTER VARYING(255) NOT NULL REFERENCES Users (username) ON UPDATE CASCADE ON DELETE CASCADE,
    sensor_id CHARACTER VARYING(255) NOT NULL REFERENCES Sensors (sensor_id) ON UPDATE CASCADE ON DELETE CASCADE,
    threshold_id CHARACTER VARYING(255) NOT NULL REFERENCES Thresholds (threshold_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

## Example-Entries

```sql
-- EXAMPLE-DATA
INSERT INTO Subscriptions (created, updated, username, sensor_id, threshold_id)
VALUES (now(), now(), 'nicho90', 1, 1);

INSERT INTO Subscriptions (created, updated, username, sensor_id, threshold_id)
VALUES (now(), now(), 'nicho90', 1, 2);

INSERT INTO Subscriptions (created, updated, username, sensor_id, threshold_id)
VALUES (now(), now(), 'nicho90', 1, 3);
```
