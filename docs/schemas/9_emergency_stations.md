```sql
DROP TABLE IF EXISTS Emergency_Stations CASCADE;

-- SCHEMA
CREATE TABLE Emergency_Stations (

    -- General
    emergency_station_id SERIAL PRIMARY KEY,
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
INSERT INTO Emergency_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Berufsfeuerwehr', '+4925120250', 'York-Ring', '25', '', '48159', 'NRW', 'Münster', 'GERMANY', 'POINT(7.611165 51.974492)');

INSERT INTO Emergency_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Freiwillige Feuerwehr Telgte', '+4925048806790', 'Alverskirchener Straße', '27', '', '48291', 'Telgte', 'NRW', 'GERMANY', 'POINT(7.788771 51.975639)');

INSERT INTO Emergency_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Stadt Münster Freiwillige Feuerwehr', '', 'Rudolf-Diesel-Straße', '51', '', '48157', 'Münster', 'NRW', 'GERMANY', 'POINT(7.666192 51.989147)');

INSERT INTO Emergency_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Feuerwache II', '', 'Theodor-Scheiwe-Straße', '1', '', '48155', 'Münster', 'NRW', 'GERMANY', 'POINT(7.645146 51.946133)');

INSERT INTO Emergency_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Wasserschutzpolizeiinspektion', '', 'Wilhelmshavenufer', '20', '', '48155', 'Münster', 'NRW', 'GERMANY', 'POINT(7.664706 51.970424)');


-- Australian example entries
INSERT INTO Emergency_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Palmerston Fire Station', '', 'Emery Ave', '46', '', '0830', 'Palmerston City', 'NT', 'AUSTRALIA', 'POINT(130.980956 -12.495806)');

INSERT INTO Emergency_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Katherine Police/Fire Station', '+61889738000', 'Stuart Hwy', '', '', '0850', 'Katherine East', 'NT', 'AUSTRALIA', 'POINT(132.284959 -14.471554)');
```
