<style>
h1 a {
  display: none;
}

.container-lg {
  min-width: 200px;
  max-width: 880px;
  padding: 45px;
}
</style>

[All Notes](http://karishmadaga.com/course-notes) // [About](http://karishmadaga.com)
# CISC 235: Data Structures
Design and implementation of advanced data structures and related algorithms, including correctness and complexity analysis. Efficient implementation of lists, sets, dictionaries, priority queues, trees, graphs, and networks using arrays, hash tables, heaps, and hierarchical linked structures. String and graph problems, such as string matching and shortest path. External storage and input-output complexity.

## Topics

* [Algorithmic Complexity](#algorithmic-complexity)
* [Stacks, Queues, and Heaps](#stacks-queues-heaps)
* [Binary Search Trees](#bsts)
* [Hashing](#hashing)

* [Sorting Algorithms](#sorting)
  * [Insertion Sort](#insertion-sort)
  * [Merge Sort](#merge-sort)
  * [Quick Sort](#quick-sort)
  * [Heap Sort](#heap-sort)

* [Graphs](#graphs)
  * [Breadth First Search](#bfs)
  * [Depth First Search](#dfs)
  * [Minimum Spanning Trees](#minspantrees)

* [Disjoint Sets](#disjoin-sets)
* [Shortest Paths](#shortest-paths)
  * [Dijkstra](#dijkstra)
  * [Bellman-Ford](#bell-ford)
  * [Extras](#extra-paths)

### Administrative Details:
  * Office Hours: Goodwin 537 from Monday 2:00-4:00 pm
    and Thursday 9:30-11:30 am (may change).
  * There are assigned readings, so do them!
  * 4 Assignments: lowest counts **4%**, the other three count **8%** (total: 28%)
  * 4 Tests: lowest counts **12%**, the other three count **20%** (total: 72%)

<hr>

<h1 id="algorithmic-complexity">Algorithmic Complexity</h1>


### Data structures are a smart way of organizing data, based on which we can develop efficient algorithms easily

* They're a way of storing and organizing data to facilitate access and modifications
* We learn the strength and limitations of each data structure so that we know which one to use!
* **programs = algorithms + data structures**

### Possible Problems:
1. Organize a dictionary to facilitate spell checking and/or autocorrect
2. Organize a representation of the internet to facilitate routing decisions
3. Organize a set of "high interest" words so that documents can be scanned for containing any of them (if we are okay with a few false positives)
4. Given a data set that is larger than internal memory, organize it on an external device to facilitate searches
5. Create a login/password system where the passwords aren't stored in any form on the server

### Analysis:

* Looking at worst-case, average-case, amortized, and expected worst-case for randomized algorithms
* This is more important than algorithms, but less fun to learn :')

#### Abstract Data Types (ADTs) and Data Structures: Two related **but** different concepts.

ADT: describes <strong>what</strong> (the interface)
  * what data is stored
  * what operation is supported

Data structure: describes <strong>how</strong> (the implementation)
  * how the data is stored
  * how to perform the operations

**Complexity** is the amount of resource required by an algorithm, measured as a function of the input size. Complexity can be split into two types:
* time complexity: number of steps (running time) executed by an algorithm
* space complexity: number of units of space required by an algorithm
  * i.e. the number of elements in a list, the number of nodes in a tree/graph, etc.


Example: Search a linked list.
```
    SearchFortyTwo(L):
      z = L.head     // z is pointing at the linked list's first element
      while z != None and z.key != 42
        z = z.next   // while neither of the above conditions are met, z will increment along L
      return z
```

So let L = 41 -> 51 -> 12 -> 42 -> 20 -> 88. How many times will line 2 be executed?
* Since the z.key = 42 case is true after the z has been compared 4 times, line 2 will be executed **4 times**!


*Now let L = 41 -> 51 -> 12 -> 24 -> 20 -> 88. How many times will line 2 be executed?*
* **7 times!** The first case (z = None) is true when z is pointed at the last node.


#### Analysis: Best-case, Worst-case, Average-case

1. **Worst Case Running time**: What is the maximum (longest) running time for some input of size *n*?

Let t(x) be the *running time* of an algorithm A with input of size x.
T(n) = max {t(x): x is an input of size n}

1. **Best Case Running time**: Not very interesting, rarely studied. We should prepare for the worst, not the best!

T(n) = max {t(x): x is an input of size n}

1. **Average Case Running time**: The reality is, running time is "distributed" between the best and worst cases. So for our search linked list example, the running time is distributed between 1 and n + 1. The average case is the **expectation** of the running time. Let t_n be a random discrete variable whose possible values are between 1 and n + 1. The expectation would be:

summation from best to worst case of t multiplied with the P(t_n = t)
hold on! to take the expectation of a r.v., we need its pmf (which we get from its distribution)


Example: What is the worst case running time among all possible linked lists L with length n?

*  This would be the case where no node is 42 (42 is not in L). So, T(n) = n + 1 (max number of steps to compare all nodes plus a final none).

#### Asymptotic: Upper, tight, and lower bounds:

1. O(f(n)) is the set of functions that grow *no faster* than f(n). If g is an element of O(f(n)), then we can say that g is asymptotically *upper bounded by f(n)* (g cannot grow faster than f(n)).
2. Omega(f(n)) is the set of functions that grow *no slower* than f(n). If g is an element of Omega(f(n)), then we can say that g is asymptotically *lower bounded by f(n)* (g cannot grow slower than f(n)).
3. If g is an element of O(f(n)) and Omega(f(n)), then g is an element of the tight bound of f(n), where the tight bound is the set of functions that grow no slower or faster than f(n).

Ideas behind Asymptotic Notations:

- We only care about the **rate** of growth, so constant factors don't matter
- We only care about **large inputs**, so only the highest degree term matters

Growth rate ranking (slow --> fast): f(n) = 1 --> logn --> sqrt(n) --> n --> nlogn --> n^2 --> n^3 --> 2^n --> n^n
High level look at asymptotic notations:

- it is a **simplification**(!!) of the 'real' running time. In the real world, constant factor matters! Hardware matters! Implementation matters!
- simplification allows the development of the theory of computational complexity (an entire subfield of cs)

##### Combining Best/Avg/Worst and Asymptotic**: O and Omega can BOTH be used to upper and lower bound worst/best/average running time.

Example: Commuting time to school from home case:
* "Even the **worst** day is *less than 2 hours*". So _everyday_ is less than 2 hours. This is the upper bound on the worst case for commuting.
(!) Equivalently, *how do you argue that some algorithm A(x)'s worst case running time is in O(n^2)?*
<p>First, let's deconstruct the question. Worst case is the longest running time for some input of size n. Big O is the set of functions that grow no faster than f(n) (i.e., the upper bound, and in this case, cn^2). So, the question is asking, how do we know that the running time is no larger than cn^2?</p>
<p>We can check for every input x of size n, the running time of the algorithm A with input x is no larger than cn^2, where c > 0 and a constant.</p>
* 2."The **worst** day is *more than 2 hours*". So there is no day where the commute is less than 2 hours. This is the lower bound on the best case for commuting.
(!) Equivalently, *how do you argue that some algorithm A(x)'s best case running time is in Omega(n^2)?*
<p>The best case is the shortest running time of an algorithm for some input x of size n. Omega is the set of functions that grow no slower than f(n) (in this case, cn^2).</p>
<p>So, the question is asking, how do we know that the shortest running time is no less than cn^2?</p>
We can check for every input x of size n, the running time of the algorithm A with input x is no less than cn^2, where c > 0 and a constant.

<h1 id="stacks-queues-heaps">Stacks, Queues, and Heaps</h1>

## Stacks

## Queues and Heaps
This week, we're looking at the abstract data type called 'queue' and the heap data structure.
##### Queue: first in, first serve (FIFO). A queue is a collection of elements with the supported operations **enqueue(Q,x), dequeue(Q), and peekfront(Q)**.
##### Max-Priority Queue: a collection of elements **with priorities**, i.e., each element x has k priority. (ex: oldest person is served first). It has the supported operations **insert(Q,x), ExtractMax(Q), Max(Q), and IncreasePriority(Q,x,k) which increases x's priority to k**.


The applications of Priority Queues include job scheduling in operating systems (processes have different priorities), bandwidth management in a router, finding the minimum spanning tree of a graph, etc.

##### Implement a Max-Priority Queue
Using an unsorted linked list,
* **Insert(Q,x)** : x is a node. Insert x at the head, which has the tight bound of 1.
* **IncreasePriority(Q,x,k)** : Change x's priority to k, which has the tight bound of 1.
* **Max(Q)** : Have to go through the whole list, which has the tight bound of n.
* **ExtractMax(Q)** : Go through the whole list to find x with max priority (O(n)), then delete it (O(1) if double linked) and return it, so overall it has a tight bound of n.
Using a sorted and unsorted linked list both give us pretty bad tight bounds of n for some operations, and that does not scale well for very large inputs. Is there a better way to link these elements?
... Yes! We can use a heap!

##### **Heap**: A heap is a **binary heap** stored in an array, which is a binary tree
###### **Binary Max-Heap**: A binary max-heap is a *nearly-complete* binary tree that has the *max-heap property*. A binary tree has at most 2 children for each node. A nearly-complete binary tree means that every level is completely filled except for the bottom level, where nodes are filled to as *far left* as possible.
Why is it important for it to be a nearly-complete binary tree?
1. Because we can then store the tree in an array, and each node knows which index has its parent or left/right child.
LeftChild(index) = 2*index
RightChild(index) = 2(index) + 1
Parent(index) = floor(index/2)
2. The height of a complete binary tree with n nodes is the tight bound of log n (which is why the operations for a max-priority queue have logn worst-case running time)

**Max-Heap property**: Every node has a key (priority) greater than or equal to the keys of its immediate children, implying that every node is larger than or equal to all of its descendants (i.e. every subtree of a heap is also a heap).


Now that we have defined a few things, we can work on the operations!
* **Max(Q): Returns the largest key in Q in O(1) time**
Because of the max-heap property, we just have to return Q[1]! The worst case is then the tight bound of 1.
* **Insert(Q, x): Insert node x into heap Q in O(log n) time**
First thing to note: Which spot do we add the new node? We would need to add x to the end of the heap to keep it a complete binary tree. However, the heap property might be broken. X could be greater than its parent node. If that's true, we should 'bubble-up' the new node to a proper position by swapping with the parent and keep doing this until it is less than its parent. This operation's worst case is then O(height) = O(log n).
* **ExtractMax(Q): Delete and returns the largest key in Q in O(logn) time**
How do we delete the root and keep the heap a complete binary tree? The only spot we can delete to keep a complete binary tree is the last element, but we want the root to be deleted! Our solution is to overwrite the root with the last key and then delete the last guy. Now that the max-heap property is broken, we need to fix it by swapping (or 'bubbling down') with a child.. but which child do we swap with? We swap with the elder child because it's the largest among the three and we want to maintain the max-heap property.


<h1 id="bsts">Binary Search Trees</h1>

<h1 id="hashing">Hashing</h1>

<h1 id="sorting">Sorting Algorithms</h1>
<h2 id="insertion-sort">Insertion Sort</h2>
<h2 id="merge-sort">Merge Sort</h2>
<h2 id="quick-sort">Quick Sort</h2>
<h2 id="heap-sort">Heap Sort</h2>

<h1 id="#graphs">Graphs</h1>
<h2 id="bfs">Breadth First Search</h2>
<h2 id="dfs">Depth First Search</h2>
<h2 id="minspantrees">Minimum Spanning Trees</h2>

<h1 id="#disjoint-sets">Disjoint Sets</h1>

<h1 id="#shortest-paths">Shortest Paths</h1>
<h2 id="#dijkstra">Dijkstra</h2>
<h2 id="#bell-ford">Bellman-Ford</h2>
<h2 id="#extra-paths">Extras</h2>
