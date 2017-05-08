# PYTHON

### Clear List / Set / Dict
* Clear a list
```
a = [1,2,3]
del a[:]
```

* Clear a set
```
a = set([1,2,3])
a.clear()
```

* Clear a dict
```
a = {1:1, 2:2, 3:3}
a.clear()
```

---

### Pop from List / Set / Dict
* Pop from a list (remove the *last* element from a list)
```
a = [1,2,3]
v = a.pop()     # O(1)
v == 3
```

* Pop from a set (remove an *arbitrary* element from a set)
```
a = set([1,2,3])
v = a.pop()     # O(1)
# v is undeterministic
```

* Pop from a dict (remove a key-value pair *with a specified key* from a dict)
```
a = {1:'a', 2:'b', 3:'c'}
v = a.pop(2)    # O(1)
v == 'b'
```

---

### Remove from List / Set / Dict
* Remove from a list
```
a = [1,2,3]
a.remove(2)     # O(n)
```

* Remove from a set
```
a = set([1,2,3])
a.remove(2)     # O(1)
```


## HEAPQ
* heapify
```
a = [3,1,6]
heapify(a)
a == [1,3,6]
```

* heappush
```
heappush(a, 2)
# a == [1,2,6,3]
```

* heappop
```
v = heappop(a)
v == 1
a == [2,6,3]
```


## BISECT
* bisect: locate the position to be inserted for the given element such that
  the resulting array is sorted
```
from bisect import *
a = [1,2,5]
p = bisect(a, 3)
p == 2
```

* insort: insert the given element
```
from bisect import *
a = [1,2,5]
insort(a, 3)
a == [1,2,3,5]
```


## char to int / int to char
```
v = ord('a')
print v
>>> 97

c = chr(97)
print c
>>> 'a'
```


