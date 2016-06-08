```sql
DROP TABLE IF EXISTS Water_Bodies CASCADE;
DROP TYPE IF EXISTS water_body_types CASCADE;

-- ENUM
CREATE TYPE water_body_types AS ENUM ('STREAM', 'RIVER', 'CHANNEL', 'LAKE', 'POND', 'POOL');

-- SCHEMA
CREATE TABLE Water_Bodies (

    -- General
    water_body_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    name CHARACTER VARYING(255) NOT NULL,

    -- Category
    category water_body_types NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Water_Bodies (created, updated, name, category)
VALUES (now(), now(), 'Werse', 'RIVER');

INSERT INTO Water_Bodies (created, updated, name, category)
VALUES (now(), now(), 'Ems', 'RIVER');

INSERT INTO Water_Bodies (created, updated, name, category)
VALUES (now(), now(), 'Dortmund-Ems Kanal', 'CHANNEL');

INSERT INTO Water_Bodies (created, updated, name, category)
VALUES (now(), now(), 'Schleusebecken (Schiffahrter Damm)', 'POOL');

INSERT INTO Water_Bodies (created, updated, name, category)
VALUES (now(), now(), 'Aa', 'STREAM');

INSERT INTO Water_Bodies (created, updated, name, category)
VALUES (now(), now(), 'Aasee', 'LAKE');
```
