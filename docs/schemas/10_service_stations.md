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

-- Australian example entries
INSERT INTO Service_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'Caltex Berry Springs', '+61889886010', 'Cox Peninsula Rd', '808', '', '0838', 'Berry Springs', 'NT', 'AUSTRALIA', 'POINT(131.014369 -12.700771)');

INSERT INTO Service_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'United Petroleum - Noonamah', '+61394131400', 'Stuart Hwy', '1805', '', '0837', 'Noonamah', 'NT', 'AUSTRALIA', 'POINT(131.074572 -12.633788)');

INSERT INTO Service_Stations (created, updated, name, phone_number, street, house_number, addition, zip_code, city, state, country, coordinates)
VALUES (now(), now(), 'United Petroleum - Acacia', '+61889883219', 'Stuart Hwy', '3760', '', '0822', 'Acacia Hills', 'NT', 'AUSTRALIA', 'POINT(131.122041 -12.799029)');
```
