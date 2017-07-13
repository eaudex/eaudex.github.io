# Title
## Subtitle
### Subsubtitle
This is normal text...

This is a bullet list...
* This is **bold**.
* This is *italic*.
* This is ~~strikethrough~~.

This is a numbered list...
1. This is **bold**.
2. This is *italic*.
3. This is ~~strikethrough~~.

This is a quote...
> This is block quote.
> This is block quote.
> This is block quote.
> This is block quote.
> This is block quote.
> This is block quote.
> This is block quote.
> This is block quote.
> This is block quote.
> This is block quote.

The code is as follows.
```python
def code():
    pass
```

The math is as follows.
$$
f(w) = \|w\|_1 + \sum \epsilon(w; x_i,y_i)
$$

This is a table.
| ABC | BCD | CEF |
| :--- | ---: | :---: |
| A   | B   | C   |
| A   | B   | C   |

---

This is a to-do list.
- [X] task1
- [] task2
- [] task3

This is a hyperlink to http://www.google.com .

This is a [Google](http://www.google.com).

![Google](https://www.google.com/logos/2007/ru_knowledge_day07.gif)


### Scope
### Services
### Storage
### Scability


---


## System
The **CAP** therorem is mentioned at
[https://en.wikipedia.org/wiki/CAP_theorem](https://en.wikipedia.org/wiki/CAP_theorem).
1. Consistency: every read receives the most recent write.
2. Availability: every request receives a response.
3. Partition tolerance: a system continues to operate even if there is network
partition between nodes happening.

No distributed system is safe from netowork failure.
In the presence of network partition, one has to choose one of the two:
consistency or availability.
Traditional systems such as RDBMS choose consistency over availability, while
modern systems such NoSQL DBMS choose availability over consistency.

**Fault tolerance**: a system continues to operate properly (possibly at a reduced
level rather than failing completely).
([https://en.wikipedia.org/wiki/Fault_tolerance](https://en.wikipedia.org/wiki/Fault_tolerance))

There are two common ways to make systems fault tolerant.
1. *Replication*: providing multiple identical instances of a system/component,
direct tasks or requests to all of them in parallel and choose the correct
result.
2. *Redundency*: providing multiple identical instances of a system/component,
switch to one of the remaining instances in case of a failure.


Making a web application fault tolerant: separating model and view.
Data is persisted in the database.
View on the client side sends a short-lived reuqest to get the data relevant to
the request.
* If a request fails to read, then it re-attempts the request.
* If the database fails, then database replication takes over.



### Cassandra Keys
* primary key: partition key + clustering key, e.g. PRIMARY KEY((p1,p2,...), c1, c2, c3, ...)
* partition key: for data distribution across machines, can be composite, minimum required specifier
* clustering key: for data sorting within a partition, can be composite
* [http://stackoverflow.com/questions/24949676/difference-between-partition-key-composite-key-and-clustering-key-in-cassandra](http://stackoverflow.com/questions/24949676/difference-between-partition-key-composite-key-and-clustering-key-in-cassandra)


### Sys
* Simply put, it is to connect users with resources (mostly data).
* Basic operations:
    * Read
    * Write

#### Objectives
1. high throughput (measured in qps)
2. low latency (measured in ms)
4. availability
3. consistency (may be relaxed to eventual consistency)

* fault tolerance
    * single point of failure
    * redundency
    * replication
    * failover
    * failback
    * heartbeat

* scalability (how much load the system can take)
    * scaling
        * vertical scaling
            * more RAM
            * more cores
            * more powerful CPUs
            * more hard drives
            * **There is a ceiling**
        * horizontal scaling
            * more machines
            * load balancing
            * partitioning / sharding
                * vertical sharding
                * horizontal sharding
            * consistent hashing

* Latency


Principles
* service-oriented architecture (SOA)
* CAP theorem
    * availability
    * consistency
    * network tolerance




##
* concurrency vs parallelism
    * concurrency: deal with lots of tasks at once
    * parallelsim: do lots of tasks at once

* synchronous vs asynchronous
    * synchronous:
    * asynchronous (preferred):

* blocking vs non-blocking
    * blocking: one thread delays other threads
    * non-blocking (preferred): no thread delays other threads

* deadlock
* livelock
* starvation

* race condition

