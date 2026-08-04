**** Elementary Data Structures Implementation and Discussion:****

Overview:
The primary goal of Step 2 is to evaluate the runtime efficiency, memory consumption, and structural tradeoffs of the foundational data structures implemented (Custom Array, Matrix, Array Stack, Circular Array Queue, Singly Linked List, and Rooted Tree).
By combining Theoretical Big-O Analysis with Empirical Benchmarking, Step 2 validates whether real-world execution times align with theoretical upper bounds across small, medium, and large input scale sizes (N).

Implemented Data Structures
* **Custom Dynamic Array:** Contiguous memory array supporting indexed access, dynamic scaling, insertions, and deletions.
* **Matrix Structure:** Multi-dimensional representation for fast O(1) grid lookup and row/column traversals.
* **Array Stack (LIFO):** Fixed-position push, pop, and peek operations.
* **Circular Array Queue (FIFO):** Fixed-capacity circular buffer optimizing enqueue and dequeue to $O(1)$ without element shifting.
* **Singly Linked List:** Node/pointer-based structure supporting O(1) head insertions/deletions and sequential O(n) search.
* **Rooted Tree:** Linked hierarchical tree supporting child insertions, node pruning (deletion), search, and pre-order DFS / level-order BFS traversals.

## Project Structure
	Medians and Order Statistics & Elementary Data Structures_Step2.ipynb  # Source code for algorithms
	Step2_Documentation # Project documentation 
	Step2_README.md                # Summary of findings

Environment Requirements
	Python 3.8+

Environment & Setup
Prerequisites
	Python Version: Python 3.8+ (Python 3.10+ recommended)
	Standard Libraries Used: sys, time, tracemalloc, typing, collections

Setup Instructions
	Theoretical vs. Empirical Time Complexity
  
Data Structure	Operation	Theoretical Big-O	Empirical Scaling Behavior
Custom Array	Access	O(1)	Near instantaneous across all N
Custom Array	Insertion (at 0)	O(n)	Quadratic time growth due to element shifting
Circular Queue	Enqueue / Dequeue	O(1)	Constant execution time regardless of capacity
Singly Linked List	Head Insertion	O(1)	Constant time; avoids dynamic array resizing
Singly Linked List	Search / Access	O(n)	Strictly linear growth; suffers from cache misses
Rooted Tree	Traversal (DFS/BFS)	O(n)	Linear scaling proportional to total node count

2. Key Empirical Insights
	CPU Cache Locality Overhead: Although Linked Lists and Custom Arrays both exhibit O(n) linear traversal times theoretically, contiguous Arrays executed significantly faster in real-world trials. Arrays leverage sequential memory prefetching at the CPU cache level, whereas node pointer traversals incur frequent cache misses.
	Circular Buffer Efficiency: The Circular Array Queue eliminated the dynamic O(n) element shifting cost common in simple array queues, yielding sustained O(1) runtime efficiency under heavy workloads.
	Memory Footprint Tradeoffs: Pointer-based structures (Singly Linked Lists and Trees) exhibited roughly 2× to 3× higher memory overhead per element compared to contiguous arrays due to storing explicit object headers and pointer references.


