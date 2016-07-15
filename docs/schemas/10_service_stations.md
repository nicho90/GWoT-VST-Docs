```sql
DROP TABLE IF EXISTS Service_Stations CASCADE;

-- SCHEMA
CREATE TABLE Service_Stations (

    -- General
    service_station_id SERIAL PRIMARY KEY,
    created TIMESTAMP WITH TIME ZONE NOT NULL,
    updated TIMESTAMP WITH TIME ZONE,

    -- Attributes
    name CHARACTER VARYING(255) NOT NULL,
    phone_number CHARACTER VARYING(255) NOT NULL,
    street CHARACTER VARYING(255) NOT NULL,
    house_number CHARACTER VARYING(255) NOT NULL,
    addition CHARACTER VARYING(255),
    zip_code CHARACTER VARYING(255) NOT NULL,
    city CHARACTER VARYING(255) NOT NULL,
    state CHARACTER VARYING(255) NOT NULL,
    country CHARACTER VARYING(255) NOT NULL,

    -- Coordinates
    coordinates GEOGRAPHY(POINT) NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Service_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Autoservice Hermann Nientiedt', '+492512842937', 'Gildenstraße', '2 Q', '', '48157', 'Münster', 'NRW', 'GERMANY', 'POINT(7.704319 51.979838)');

INSERT INTO Service_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Auto-Service Andres GmbH', '+49251324201', 'Virnkamp', '20', '', '48157', 'Münster', 'NRW', 'GERMANY', 'POINT(7.664011 51.992260)');

INSERT INTO Service_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Pit-Stop Auto Service GmbH', '+4925130231', 'Ostmarkstraße', '92', '', '48145', 'Münster', 'NRW', 'GERMANY', 'POINT(7.655081 51.967563)');

INSERT INTO Service_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Ralf Jaisfeld', '+4925134882', 'Beckhofstraße', '23', '', '48145', 'Münster', 'NRW', 'GERMANY', 'POINT(7.650274 51.969012)');

INSERT INTO Service_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Autohaus Steinbrede', '+492512302850', 'Dieckstraße', '63', '', '48145', 'Münster', 'NRW', 'GERMANY', 'POINT(7.652783 51.973841)');
```
