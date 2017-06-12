# Cassandra

* a partitioned row store

* a primary key uniquely identifies a row
* a primary key = a partition key + a clustering key
    * partition key: for data distribution across nodes
    * clustering key: for data ordering within a partition
    * both keys can be compound...

* *uuid* type
* collection type: set, list, map
* able to create index on a data column, so the column can be used as a filter
* able to create index on a collection column


## Data Modeling for Large-scaled Web Applications
* Understanding data -> entities & relationships
* Understanding use cases -> query patterns
* Design data schema & define keys/indices perfectly for query patterns

