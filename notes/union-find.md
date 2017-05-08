# Union Find

```
def find(parents, idx):
    curr = idx
    while parents[curr] != curr:
        curr = parents[curr]
    return curr
```

```
def union(parents, idx, jdx):
    pi = find(parents, idx)
    pj = find(parents, jdx)
    if pi != pj:
        parents[pj] = pi
```
