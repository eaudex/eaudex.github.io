# Optimization

## Algo
Given the objective function $$f(x)$$,
```
# Optimization Algo
x = x0
while x is not optimal:
    1. Compute \eta
    2. Compute step
    3. Update x = x - \eta step
```

## Compute Step
1. The variable $$step$$ is called a *gradient* step if $$step = \nabla f(x)$$.
2. The variable $$step$$ is called a *Newton* step if $$step = (\nabla^2 f(x))^{-1} \cdot \nabla f(x)$$.
3. The variable $$step$$ is called a *quasi Newton* step if $$step = H \cdot \nabla f(x)$$
   and $$H \approx (\nabla^2 f(x))^{-1}$$.

- BFGS: $$H$$ is dense and is constructed by ??.
  (It is not practical when the number of variables in $$x$$ is very large.)
- L(limited-memory)-BFGS: $$H$$ is implicitly formed by a history of the past $$x$$ and $$\nabla f(x)$$.
- CGD: $$H_{ii} = \nabla_{ii} f(x)$$; $$H_{ij} = 0, i \neq j$$.


## Compute Step Size
### Line Search
* Exact line search
* Backtracking line search

### Trust Region

### When to use which??



## Facts
### About Quodratic Functions
Given the quodratic function $$f(x) = (1/2) x^T A x + g^T x$$,
(the minimizer exists under some condition on $$A$$)
* $$\nabla f(x) = Ax + g$$.
* $$\nabla^2 f(x) = A$$.
* $$x* = \arg \min f(x) = - A^{-1} g$$ when $$\nabla f(x) = Ax+g = 0$$.
* Minimizing f(x) is equivalent to solving the linear system $$A x = -g$$.

### About Linear Regression
Solve $$\min_x \|Ax - y\|_2^2$$
* $$\|Ax - y\|_2^2 = (Ax - y)^T (Ax - y) = x^T (A^T A) x - 2 y^T Ax + y^T y$$
* $$\min_x \|Ax - y\|_2^2 $$
  === $$\min_x (1/2) x^T (A^T A) x - y^T Ax$$
* It is equivalent to solving the linear system: $$(A^T A) x = A^T y$$.

### About Ridge Regression
Solve $$\min_x \lambda \|x\|_2^2 + \|Ax - y\|_2^2$$
* $$\min_x \lambda \|x\|_2^2 + \|Ax - y\|_2^2 $$
  === $$\min_x (1/2) x^T (A^T A + \lambda I) x - y^T Ax$$
* It is equivalent to solving the linear system: $$(A^T A + \lambda I) x = A^T y$$.

### About Linear System Solvers ???
1. Direct methods: e.g. Gaussian elimination
2. Iterative methods: e.g. Jacobi and conjugate gradient


# References
* https://en.wikipedia.org/wiki/Broyden%E2%80%93Fletcher%E2%80%93Goldfarb%E2%80%93Shanno_algorithm
* https://en.wikipedia.org/wiki/Limited-memory_BFGS








