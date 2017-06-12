
# Redis
* availability
* consistency
* fault tolerance: some degree

* auto shard

* [Ref] https://redis.io/topics/cluster-tutorial
* [Ref] http://highscalability.com/blog/2011/7/6/11-common-web-use-cases-solved-in-redis.html



## Replication - HW + SW + data
* Why
    * data backup
    * no data loss
    * durability
    * fault tolerance - no single point of failure
    * high availability
    * throughput in master/master arch

* Arch
    * master-slave
    * master-master
    * sync
        * write does not complete
    * async
        * ship log
        * replay log
        * catch up with the master













# HDFS
* distributed file system
* high throughput (distributed)
* high latency (file system, data is stored in disk)
* fault tolerance
* high availability

* Arch
    * name node
    * data nodes

* Replication
    * sync master/master (data nodes)

















