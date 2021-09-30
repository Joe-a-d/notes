# Stack

### Operations

- `create`
-  `isEmpty`
-  `push`
-  `pop`

- all $O(1)$

### Properties

- grows upwards
- removal is LIFO

### Implementation

- can be implemented as an [[array]] or as a [[linked list]]

# Queue

### Operations

- `create`
-  `isEmpty`
-  `insert`
-  `delete`

- all $O(1)$

### Properties

- grows backwards
- removal is FIFO

### Implementation

- can be implemented as an [[array]] or as a [[linked list]]
	- array needs to be implemented as a [circular queue](https://opendatastructures.org/ods-cpp/2_3_Array_Based_Queue.html). Essentially as we reach the end of the array, there is space at the start as we remove elements, but we can't resize the array, so we keep incrementing the indices but use modular arithmetic to add new elements to the start of the array

# Priority Queue

### Operations

- `create`
-  `isEmpty`
-  `insert`
-  `delete`

- insert $O(1)$ and delete $O(n)$ if implemented as an unordered list
	- vice-versa for ordered list implementation
- $O(log n)$ as a heap

### Properties

- remove elements by priority

### Implementation

- can be implemented as an ordered ,unordered list or heap