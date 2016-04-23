## What is Redis?

>Redis is an open source (BSD licensed), in-memory data structure store, used as database, cache and message broker. It supports data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs and geospatial indexes with radius queries. Redis has built-in replication, Lua scripting, LRU eviction, transactions and different levels of on-disk persistence, and provides high availability via Redis Sentinel and automatic partitioning with Redis Cluster.
>(Source: [http://redis.io/](http://redis.io/), 2016-04-23)

### Installation

##### Linux

```bash
cd /home/n_schi16
wget http://download.redis.io/releases/redis-3.0.7.tar.gz
tar xzf redis-3.0.7.tar.gz
cd redis-3.0.7
make
```

##### macOS

You can use **Homebrew** (the package-manager for macOS) to install it. Run the following command:

```bash
brew install redis
```

For manually installation, please check out this [tutorial](http://jasdeep.ca/2012/05/installing-redis-on-mac-os-x/).

##### Windows

At the moment Redis is not officially support on Windows. There seems to be a solution from the Microsoft Open Tech group.

### Configuration


### Running

On Linux you can start Redis with the following command:

```bash
/home/n_schi16/redis-3.0.7/src/redis-server
```

With **Homebrew** on macOS you can start Redis with:

```
redis-server
```
