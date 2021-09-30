- explores the structure of the items being sorted, so may be less versatile
	- **in practice** it is only faster for very large $n$

- **assumptions**
	- items can be treated as bit-sequences of length $m$
	- $b$ is a chosen factor of $m$
	- $b, m$ are constants

- **algo**
	- each item has bit positions labelled `0,1,...,m-1`
	- takes $m/b$ iterations
	- need $2^b$ buckets labeled from [0,2^{b-1}]
	- during the ith iteration an item is placed in the bucket corresponding to the integer represented by the bits in the position $b \times i-1, \cdots, b\times(i-1)$
		- e.g. take $b=4$ and $i=2$, we look at the bits in postion [7,4], such that if the item is `0000101001[0011]0001` we look at the encapsulated bits
		- converting to base 10, gives us the integer `3`
		- Hence, the item is placed in the bucket with label 3/0011
	- at the end of the iteration the buckets are concatenated to form a new sequence
	- repeat $m/b -1$ times

- **complexity**
	- at each iteration the whole sequence is scanned and items are allocated to buckets : $O(n)$
	- at the end the buckets must be concatenated, since there are $2^b$ of them : $O(2^b)$
	- this happens a total of $m/b$ times giving an overall complexity of $Om/b \dot (n+2^b))$
		- but, since $m,b$ are constants $O(n)$
	-  note that there's a *space-time trade-off*, the higher the $b$ the fewer the number of iterations, but the more memory required for the buckets
- **example**

![[1_alg3_radix_example.pdf]]