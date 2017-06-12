

# MAPREDUCE
* a programming model for parallel distributed data processing
* the idea comes from functional programming
* key contributions:
    * scalability
    * fault tolerance
    * (optimized shuffle operations)

Computations
* Map: (key0, value0) => [(key1_i,value1_i), ...]
* Shuffle: group by key1
* Reduce: (key1, [value1j, ...]) => (key1, agg([Value1j, ...]))


## Facts
* # mappers = # input data splits
* reduce may be applied recursively in the REDUCE process



* https://chamibuddhika.wordpress.com/2012/02/26/joins-with-map-reduce/













## join

## group by

## sort

