#

## Latency Numbers
* 1MB sequential memory read: 250$$\mu s$$
* 1MB sequential SSD read: 1$$ms$$
* Disk seek: 10$$ms$$
* 1MB sequential disk read: 20$$ms$$
* Latency of a single request: 100$$ms$$ is decent
* Latency of page load: ~< 1000 $$ms$$ is decent; 2000 $$ms$$ is the up-limit.

## Key Decisons
* When low latency is the primary need, choose availability over consistency.
* When latency exists, cope with it and try to eliminate it.
* All lookups should happen in under 1 $$ms$$.
* Use SSD whereever possible.
* ...

---


## Scoping
Understanding...
* What is it?
* Who use it?
* How to use it?
* When to use it?
* Where to use it?

* use cases / specs / requirement?


## Services
## Storage
## Scalability


---

## Instant-messaging system

## URL shortening

## Key-value data store

## New Feeds
* [https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-xtf1/t39.2365-6/12431841_989782604402081_1065922300_n.pdf](https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-xtf1/t39.2365-6/12431841_989782604402081_1065922300_n.pdf)
* [http://stackoverflow.com/questions/7072924/what-is-the-design-architecture-behind-facebooks-status-update-mechanism](http://stackoverflow.com/questions/7072924/what-is-the-design-architecture-behind-facebooks-status-update-mechanism)
Keys
1. Aggregator: querying, aggregating, ranking, filtering
2. Leaf: distributed in-memory data storage


## Event Reminder
### Scoping

What defines an event?
* event name
* when
* where
* whos
* when to remind



* Vertical scaling: more RAM, more cores, more powerful CPUs
But there is a ceiling, by the budget, state of the art.
* Horizontal scaling: many cheap low-end machines
instead of a single high-end machine.


# Build a System

## Requirement
* Use cases
    * who do **what** for **what**
    * data: entities, attributes, associations
    * functionalities (maybe in terms of **C**reate**R**ead**U**pdate**D**elete?)

* Specs
    * performance
        * throughput in qps
        * latency in ms
        * space in bytes
    * scalability (for sure!)
    * consistency? (choose consistency over availability)
    * availability? (choose availability over consistency)

## Architecture
* service-oriented decomposition (SOA / SOD)
    * based on use cases
    * based on read / write
* resources per service:
    * # machines
    * # cores (per machine)
    * # RAM (per machine)
    * # hard drives (per machines)

## Data and Storage
* data store (DBMS)
    * RDBMS
        * slow read / write
        * strong consistency
        * harder to scala horizontally
    * NoSQL
        * fast read / write
        * weak (or eventual) consistency
        * automatic horizontal scaling
        * e.g. key-value type
        * e.g. document type
        * e.g. column family type
* data modeling
    * data schema
        * one table per entity
            * columns / attributes
            * primary key
            * column index ??
    * denormalization
    * ...
* data partitioning / sharding
    * vertical sharding
        * should be done in data modeling?
    * horizontal sharding
        * choose partition key (depend on use cases!)
        * choose hash function
        * choose hash scheme
            * inconsistent hashing (X)
            * consistent hashing (O)


* optimization
    * fault tolerance
        * to avoid single point of failure
            * replication
            * redundency
                * failover
                * failback
    * cache (decrease read latency)
    * proxy (collect many *similar requests* into a single uber request)
    * load balancing (distribute traffic across machines, track the heath of each node)
    * queue (for async write)

## Scaling

There are a few key design considerations as follows.
* Storage space in bytes
* Throughput in qps
* Latency in ms
* Simultaneous connection count
* ...
* Consistency vs availability


### Scaling App Server
* Cakes

### Scaling Data Store
* [http://www.clustrix.com/resources/white-papers/why-traditional-sql-databases-fail-to-scale-writes-reads-effectively/](http://www.clustrix.com/resources/white-papers/why-traditional-sql-databases-fail-to-scale-writes-reads-effectively/)

* Tranditional **R**DBMS
    * follows the relational data model
    * provides the [**ACID**](https://en.wikipedia.org/wiki/ACID) guarantees
    * supports complex queries
        * e.g. join on multiple tables
        * e.g. query on arbitrary (non-indexed) columns
        * e.g. group-by aggregation

* **ACID** gvies us too much. **ACID** is NOT required for most web applications.
* When a web application is at small scale, **ACID** is a nice-to-have feature.
* With the **ACID** guarantees, scaling a data store becomes a challenge.

* There are other key considerations such as **consistency** and **availability**
  for designing large-scale web applications.
* **NoSQL** movement is to trade **ACID** for the other key characteristics such
  as **availability**.
* Most **NoSQL** systems only support key lookup queries (no complex queries like join or groupby).
  The fact pushs application/business logic to application layer.


#### Scaling *MySQL* DB
* Data modeling:
    * Table schemas and queries are in harmony. It means that table schemas
      fit to the use cases, such that no complex queries are required.
      For examples, queries can be boiled down to
      ```SELECT * FROM table WHERE primary_key = {CONSTANT}```.
    * Define **indexes** and **keys** on the table properly,
      where indexes are for fast lookup; primary/foreign keys are for fast join.

* Architecture:
    * Caching: Have **MEMCACHED** in the front of DB.

    * Vertical scaling
        * Use **SSD**
        * More RAM
        * More cores
        * More powerful CPUs
        * More hard drives

    * Configuration:
        * Read data from RAM instead of disk (by configuring memory parameters property).
            * Get as much **indexes** and **data** in memory as possible

    * Horizontal scaling (comes at a cost of losing ACID guarantees/complex queries support)
        * Master/Slave(read-only): redirect **SELECT** queries to slaves as much as possible
            * Master is the coordinator.
            * Use master for writing; then updating replication.
            * Use slaves for reading: data might be slightly stale.
        * Master/Master: each master is responsible for one portion of data
            * One master is the coordinator.
            * Use masters for reading & writing.
            * Each master has its own copy.
            * Each master has the privillige to write its portion of data.
            * Write data and update replication.

* Use cases:
    * High read, low write:
        * Well-designed data model: only simple queries are required
        * Properly-defined indexes/keys,
        * Decent hardware
        * Configuration
        * Memcached
        * Read-only replicas
    * High write (maybe high read):
        * Sharding
        * What else??


#### Scaling NoSQL DB
* Why??
    * *Automatic* horizontal scaling
        * sharding
        * replication (to improve latency for read) and synchronization
        * traffic distribution
        * consistency control
    * *Automatic* fault tolerance
        * replication (for fault tolerance)
        * redundency




## Data Modeling

### At Structure Level
* Relational data model: e.g. ```MySQL```
    * Define highly structured entities with strict relationships between them.
    * A table models an entity.
    * A row of a table represents an instance of an entity.
    * A column of a table represents an attribute of an entity.
    * Keys are used to associate rows across tables.
    * Limitations:
        * It does NOT cover all varieties of data types.
          For examples, **set** and **map** are not supported.
        * **Nest-structured** data is stored in some use cases.
        * **Less** structured data is stored in some use cases.
          For example, some rows have different columns than the othr rows.

* Key-value stores:
* Key-data structure stores: e.g. ```Redis```
* Key-document stores: e.g. ```MongoDB```
* Column-family stores: e.g. ```Cassandra```
    * keyspace: it includs a set of column families.
    * column family: a set of (row key, value) pairs
        * where a row key consists of a partition key (for data distribution) and clustering key (for data ordering)
        * where a value consists a tuple of triplets ((column name, column value, timestamp), ...);
          there is no schema defined on the value, so there can be different columns in each value.
          
      


### At Data Level
* Case by case...



## Data Stores
[https://kkovacs.eu/cassandra-vs-mongodb-vs-couchdb-vs-redis/](https://kkovacs.eu/cassandra-vs-mongodb-vs-couchdb-vs-redis/)

### Redis
* Features:
    * In-memory key-data structure stores (very fast...)
    * Master/slave replication
    * Auto failover
    * Supports various data types such as queue, set, map, etc.
* Use cases:
    * Needs intensive *update* (not insert!)
    * Data size is predictable (to fit data in-memory)
    * Real-time messaging queue
    * e.g. real-time stock price
    * e.g. real-time analytics

### MongoDB
* Features:
* Use cases:

### Cassandra
* Features:
    * Column-family data stores
    * Decentralized, peer-to-peer arch, NO single point of failure, every node can take request
    * High write performance (fast write)
    * Read / write throughput both increase linearly as new nodes are added
    * Data are automatically replicated across nodes
    * Automatic fault tolerance
    * Tunable consistency: strong consistency, eventual consistency, weak consistency
* Use cases:
    * needs intensive write
    * stores huge data sets
    * data size grows very fast
    * e.g. web analytics, to count hits by hour, by browser, by IP, etc.
    * e.g. transaction logging
    * e.g. data collection

### ElasticSearch
* Features:
* Use cases:
    * needs advanced search functionality
        * e.g. geo search
        * e.g. age difference



# Data Flow Models
## Push Model
* data driven
## Pull Model
* demand driven




## Data Replication

### Objectives:
* fault tolerance
* accessibility

### Architecture
* Master/Slave
* Master/Master

### Strategies
* Synchronous replication
    1. A write request comes to Master and Slaves (maybe redirected from Master)
    2. Master completes the write
    3. Slaves complete the write
    4. Master and Slaves both completes the write and send ACK back
    * Zero data loss
    * Atomic write
    * all or nothing
    * high latency

* Asynchronous replication
    1. A write request comes to Master only
    2. Master completes the write
    3. Master sends ACK back
    4. Slaves complete the write asynchronously
    * Data loss
    * Replica is lagging
    * low latency

* Journal/log are kept generated in Master while Master executes write operations
  and are sent to Slaves periodically or in a steaming fashion.
  Slaves play back the journal/log and update data accordingly.
  







# Qs
* inter-process communication
    * file
    * signal
    * socket
    * message passing
* tcp vs udp
* process vs thread
* map/reduce
* synchronization
    * lock
    * semaphore
* synchronization in java

* Cache
    * write-through
    * write-around
    * write-back

* Data replication
    * synchronous: not send ACK until all writes have completed
    * asynchronous: through log shipping, aka lazy update
    * e.g. master/slave
    * e.g. master/master

* Data consistency
    * http://www.allthingsdistributed.com/2007/12/eventually_consistent.html
    * N, R, W
    * R + W > N: strong consistency
    * N >= 3: fault-tolerance
    * W = N: consistency
    * R = 1: fast read
    * W = 1: fast write, but not durable, W = 3 instead

# Data modeling


























