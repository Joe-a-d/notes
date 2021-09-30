- algorithms which compare elments pairwise

- can perform no better than $O(n \log n)$

- **Proof** : describe the algorithm by a binary decision tree such that each node represents a comparison between two elements , and each path from the root to a leaf node represents an execution of the algo. Then,
		- the leaf nodes represent the possible outcomes of the algorithm
		- for an input of size $n$ **there must be at least $n!$ leaves**, since these must represent the possible orderings of the items.
	- **Hence**, the worst-case can be no better than $O(h)$, where $h$ is the height of the tree ^7742ac
	- Since a binary tree has at most $2^{h+1} - 1$ nodes, and an equal or smaller amount of leaf nodes. It follows that , $n! \leq 2^{h+1}-1 \leq 2^{h+1}$ ^a6bc83
	- Lastly, inequating [[#^7742ac]] and [[#^a6bc83]] taking the $\log$ of both sides we prove that the running time is at least $O(n \log n)$ as required
	- step 2 : $n! > (n/2)^{n/2}$ 
 $$
\begin{aligned} h+1 & \geq \log _{2}(n !) \\ &>\log _{2}(n / 2)^{n / 2} \\ &=(n / 2) \log _{2}(n / 2) \\ &=(n / 2) \log _{2} n-(n / 2) \log _{2} 2 \\ &=(n / 2) \log _{2} n-n / 2 \end{aligned}
$$