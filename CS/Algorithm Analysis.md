- in most of the cases we are interested in **time complexity**, i.e. how the running time changes with respect to the size of the input
	- either worst-case or average-case
	- *worst-case* is the most commonly used, becauase
		- gives a guarantee of the algorithm's performance
		- we are interested in *asymptotic behaviour*
		- generally expressed using [[Big-O]]

- **polynomial time** : algorithms which run on $O(n^c)$, for some constant c
	- potentially useful in practice
	- even for $n \geq 2$ one doesn't usually run into the worst-case in practice
	- ![[Pasted image 20210914133456.png|300]]

- **exponential time** : no better than $O(c^n)$ for $c>1$
	- potentially useless in practice


