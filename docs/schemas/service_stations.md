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
    coordinates GEOMETRY NOT NULL,
    street CHARACTER VARYING(255) NOT NULL,
    house_number CHARACTER VARYING(255) NOT NULL,
    addition CHARACTER VARYING(255),
    zip_code CHARACTER VARYING(255) NOT NULL,
    city CHARACTER VARYING(255) NOT NULL,
    country CHARACTER VARYING(255) NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Service_Stations (created, updated, name, phone_number, coordinates, street, house_number, addition, zip_code, city, country)
VALUES (now(), now(), 'Autoservice Hermann Nientiedt', '+492512842937', ST_GeomFromText('POINT(51.979838 7.704319)', 4326), 'Gildenstraße', '2 Q', '', '48157', 'Münster', 'GERMANY');

INSERT INTO Service_Stations (created, updated, name, phone_number, coordinates, street, house_number, addition, zip_code, city, country) 
VALUES (now(), now(), 'Auto-Service Andres GmbH', '+49251324201', ST_GeomFromText('POINT(51.992260 7.664011)', 4326), 'Virnkamp', '20', '', '48157', 'Münster', 'GERMANY');
```
