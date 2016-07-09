## What is PostgreSQL?

>PostgreSQL is a powerful, open source object-relational database system. It has more than 15 years of active development and a proven architecture that has earned it a strong reputation for reliability, data integrity, and correctness.
>(Source: [http://www.postgresql.org/about/](http://www.postgresql.org/about/), 2016-04-23)

### Installation

##### Linux

* Install PostgreSQL with Ubuntus package-manager:

```bash
sudo apt-get update
sudo apt-get install -y postgresql postgresql-contrib
```

* Create a new user (`vst`) with the following command:

```bash
sudo -u postgres createuser -P vst
```

* Create a new database (`vst`) and give the user (`vst`) grant-access to it with the following command:

```bash
sudo -u postgres createdb -O vst vst
```

* Test connecting with the following command:

```bash
psql -h localhost -U vst vst
```

* Close the PSQL-interface with the command

```sql
\q
```

(Source: [http://www.saintsjd.com/2014/08/13/howto-install-postgis-on-ubuntu-trusty.html](http://www.saintsjd.com/2014/08/13/howto-install-postgis-on-ubuntu-trusty.html))

##### macOS

You can use **Homebrew** (the package-manager for macOS) to install it. Run the following command:

```bash
brew install postgres
```

For manually installation, please check out this [tutorial](http://jasdeep.ca/2012/05/installing-redis-on-mac-os-x/).

##### Windows

TO-DO

### Running

##### macOS

* Start:
```bash
brew services start postgres
```

* Stop:
```bash
brew services stop postgres
```

* Restart
```bash
brew services restart postgres
```

##### Linux

TO-DO
