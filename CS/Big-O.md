- we have some complex function $f(n)$ representing the running time of our algorithm, and we want to bound it using some well understood function $g(n)$, so that we can say that *$f$ grows no faster than $g$*
- formally: there exists a real constant $c$ and integer constant $N$ such that $$|f(n)| \ \leq|c \ \cdot g(n)|
\  \forall \  n \geq N$$
- we always want the tighest $g$, i.e if an algorithm has worst-case complexity $O(n)$ then $O(n^2)$ is obviously also a bound for $f$ but not the best/tightest one.