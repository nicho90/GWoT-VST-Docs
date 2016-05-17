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
    coordinates GEOMETRY NOT NULL,
    street CHARACTER VARYING(255) NOT NULL,
    house_number CHARACTER VARYING(255) NOT NULL,
    addition CHARACTER VARYING(255),
    zip_code CHARACTER VARYING(255) NOT NULL,
    city CHARACTER VARYING(255) NOT NULL,
    country CHARACTER VARYING(255) NOT NULL
);


-- EXAMPLE-DATA
INSERT INTO Emergency_Stations (created, updated, name, phone_number, coordinates, street, house_number, addition, zip_code, city, country)
VALUES (now(), now(), 'Berufsfeuerwehr', '+4925120250', ST_GeomFromText('POINT(51.974492 7.611165)', 4326), 'York-Ring', '25', '', '48159', 'Münster', 'GERMANY');

INSERT INTO Emergency_Stations (created, updated, name, phone_number, coordinates, street, house_number, addition, zip_code, city, country)
VALUES (now(), now(), 'Freiwillige Feuerwehr Telgte', '+4925048806790', ST_GeomFromText('POINT(51.975639 7.788771)', 4326), 'Alverskirchener Straße', '27', '', '48291', 'Telgte', 'GERMANY');
```
