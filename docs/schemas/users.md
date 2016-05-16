```sql
DROP TABLE IF EXISTS Users CASCADE;
DROP TYPE IF EXISTS roles CASCADE;

-- ENUM
CREATE TYPE roles AS ENUM ('admin', 'user');

-- SCHEMA
CREATE TABLE Users (
    -- General
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    username CHARACTER VARYING(255) UNIQUE NOT NULL PRIMARY KEY,
    password CHARACTER VARYING(255) NOT NULL,
    email_address CHARACTER VARYING(255) NOT NULL,
    first_name CHARACTER VARYING(255) NOT NULL,
    last_name CHARACTER VARYING(255) NOT NULL,
    language CHARACTER VARYING(255) NOT NULL DEFAULT 'en_US'

    -- Role
    role roles
);


-- EXAMPLE-DATA
INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'vst-admin', '123456789', 'sitcomlab245@gmail.com', 'VST', 'ADMIN', 'en_US', 'admin');

INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'nicho90', 'abc', 'n.schiestel@uni-muenster.de', 'Nicho', 'S.', 'de_DE', 'user');

INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'heinrichloewen', 'def', 'loewen.heinrich@uni-muenster.de', 'Heinrich', 'L.', 'de_DE', 'user');

INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'rehans516', 'ghi', 'r_chau02@uni-muenster.de', 'Rehan', 'C.', 'en_US', 'user');

INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'Timmimim', 'jkl', 't_kueh06@uni-muenster.de', 'Timm', 'K.', 'de_DE', 'user');
```
