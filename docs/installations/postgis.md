## What is PostGIS?

>PostGIS is a spatial database extender for PostgreSQL object-relational database. It adds support for geographic objects allowing location queries to be run in SQL.
>(Source: [http://postgis.net](http://postgis.net), 2016-04-23)

### Installation

##### Linux

* Install PostGIS with Ubuntus package-manager:

```bash
sudo apt-get install -y postgis postgresql-9.3-postgis-2.1
```

* Add the PostGIS-Extension to the database (`vst`):

```
sudo -u postgres psql -c "CREATE EXTENSION postgis; CREATE EXTENSION postgis_topology;" vst
```
