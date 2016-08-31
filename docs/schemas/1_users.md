```sql
DROP TABLE IF EXISTS Users CASCADE;
DROP TYPE IF EXISTS roles CASCADE;

-- ENUM
CREATE TYPE roles AS ENUM ('ADMIN', 'USER');

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
    language CHARACTER VARYING(255) NOT NULL DEFAULT 'en_US',

    -- Role
    role roles
);


-- EXAMPLE-DATA
INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'vst-admin', '123456789', 'sitcomlab245@gmail.com', 'VST', 'ADMIN', 'en_US', 'ADMIN');

INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'test-user', 'abcdef', 'test.user@uni-muenster.de', 'Test', 'User', 'en_US', 'USER');

INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'nicho90', 'abcdef', 'nicho90@example.org', 'Nicho', 'S.', 'de_DE', 'USER');

INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'heinrichloewen', 'abcdef', 'heinrichloewen@example.org', 'Heinrich', 'L.', 'de_DE', 'USER');

INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'rehans516', 'abcdef', 'rehans516@example.org', 'Rehan', 'C.', 'en_US', 'USER');

INSERT INTO Users (created, updated, username, password, email_address, first_name, last_name, language, role)
VALUES (now(), now(), 'Timmimim', 'abcdef', 'timmimim@example.org', 'Timm', 'K.', 'de_DE', 'USER');
```
