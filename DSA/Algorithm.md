# Algorithm

## Characteristics of Algorithm
1. **Input**:
- Data or information provided to the algorithm that it operates on to produce the desired output
- Take various forms depending on the nature of the problem being solved.
2. **Output**:
- Represents the desired outcome or solution to a problem.
- Without output, an algorithm would lack purpose and utility in problem-solving tasks.
3. **Definiteness**:
- Requirement of each step of the algorithm must be precisely and unambiguously defined
- It is a crucial characteristic of algorithms because it ensures clarity, consistency, correctness, interoperability (exchange information seamlessly) , and ease of debugging and maintenance
4. **Finiteness**:
- Refers to the property that an algorithm must terminate after a finite number of steps (OR) there should be a clear endpoint to the execution of the algorithm, and it should not run indefinitely.
- It is a critical property of algorithms because it ensures efficient resource utilization, predictable behavior, a positive user experience, real-world applicability, and ease of debugging.
5. **Effectiveness**:
- Refers to the ability of an algorithm to achieve its intended purpose efficiently and accurately.
- It in algorithms encompasses correctness, efficiency, scalability, robustness, simplicity, and adaptability.

`With the help of an example`: An algorithm, like a recipe, needs clear instructions (**definiteness**) to process information (**input**) and achieve a specific goal (**output**). Just like a recipe shouldn't take forever to bake (**finiteness**), an algorithm should run in a reasonable amount of time. The best recipes, like the best algorithms, are also efficient (**effectiveness**), using the least amount of ingredients and steps to get the job done.

`Analyzation of Algorithm`:
- **Time**
  - In form of time function
  - Every statement in an algorithm takes 1 unit of time
- **Space**
  - Memory consumed
  - Total number of variables
  - Example:
    ```c
      Algorithm swap()
      {
        temp = a;
        a = b;
        b = temp;
      }
    ```
- Time Analysis:
  ```xml
    t = f(n)          |    s = s(n) = s(3)
      = constatnt     |      = total variables
      = O(1)          |      = O(1)
  ```

![Time & space complexity](https://imgur.com/RyipAuZ.png)

![Questions on Time Complexity](https://imgur.com/CFdq54L.png)

![Types of time functions](https://imgur.com/7in33rc.png)

![Graphs of time function](https://imgur.com/fwoCqDg.png)

#### `Time Complexity and Big-O Notation`:
![Time & Space Complexity](https://imgur.com/L2JUO1G.png)
![Time & Space Complexity](https://imgur.com/W6FXMs8.png)

#### *`Asymptotic Notations`*
- Asymptotic notation gives us an idea about how good a given algorithm is compared to some other algorithm.
- There are three types of asymptotic notstions:
  1. Big-O notation (`O`)
  2. Big omega notation (`Ω`)
  3. Big theta notation (`θ`) --> "Widely Used"

#### **`Big-O Notation (O)`**:
- Describe an asymptotic upper bond.
- Mathematically, if `f(n)` describes the running time of an algorithm; `f(n)` is `O(g(n))` if and only if there exist positive constants c and n° such that:
```htXMLml
0 ≤ f(n) ≤ c g(n)        for all n ≥ n°. 
```
- Here, `n` is the input size, and `g(n)` is any complexity function.
- If a function is `O(n)`, it is automatically `O(n^2)` as well! Because it satisfies the equation given above.

![Big-O Graph](https://imgur.com/hUAVM0t.png)

#### **`Big Omega Notation (Ω)`**:
- Describe an asymptotic lower bond.
- Let `f(n)` describes the running time of an algorithm; `f(n)` is `Ω(g(n))` if and only if there exist positive constants `c` and `n°` such that:
```html
0 ≤ c g(n) ≤ f(n)        for all n ≥ n°.  
```
- If a function is `Ω(n^2)` it is automatically `Ω(n)` as well since it satisfies the above equation.

![Big Omega Graph](https://imgur.com/KeGxTlU.png)

#### **`Big theta notation (θ)`**:
- Let `f(n)` define the running time of an algorithm.
- `f(n)` is said to be **θ (g(n))** if `f(n)` is `O(g(n))` and `f(n)` is `Ω(g(n))` both. 
```html
    0 ≤ f(n) ≤ c1 g(n)      ∀    n ≥ no.      --------(i)
    0 ≤ c2 g(n) ≤ f(n)      ∀    n ≥ no.      --------(ii)  
    
              On Combining both the equation:

    0  ≤ c2 g(n)  ≤  f(n) ≤ c1 g(n)      ∀    n ≥ no.  

```
![Big-theta Graph](https://imgur.com/olyat4X.png)
- Big theta provides a better picture of a given algorithm, most of the interviewers expect you to provide an answer in terms of Big Theta when they say **Order Of** as it provides the exact posibility of the function to lie at that value. We generally use Big Oh and Big Omega when tthe exact posibility of the gfunction is not known to us

![Order of Runntime Algorithm](https://imgur.com/J8WmSYn.png)

#### Properties of Asymptotic Notations:
- If `f(n)` is `O(g(n))` then that of `a*f(n)` is same
- A function is itself `O(f(n))`
  - Same function is the upper as well as the lower bound of the function
- If `f(n)` is `O(g(n))` and `g(n)` is `O(h(n))`
- If `f(n)` is `θ(g(n))` then `g(n)` is `θ(f(n))`
- If `f(n)` is `O(g(n))` then `g(n)` is `Ω(f(n))`
- If `f(n) = O(g(n))`  and `f(n) = Ω(g(n))`. Therefore, `f(n) = θ(g(n))`
- If `f(n) = O (g(n))` & `d(n) = O (e(n))`. Then:
```xml
f(n) + d(n) = O (max(g(n),e(n)))
f(n) * d(n) = O (g(n)*e(n))
```

- For the comparision of two functions we use the mathematical concept `log`: Apply log on both the functions.

#### Best Case, Worst Case and Average Case Analysis of an Algorithm:

1. **Best Case**: The scenario in which the algorithm performs optimally, achieving the lowest possible time    complexity or space complexity for a given input size
2. **Worst Case**: The scenario of an algorithm in which the algorithm exhibits the highest time complexity or resource usage
   - Worst Case can also varies from maximum to minimum. As, worst case for binary search depends on the height of the binary search tree, and height of the binary search tree depends from minimum as `log n` and maximum as `n`.
      - So, the worst case flactuates from: `O(log n)` to `O(n)`
3. **Average Case**: Represents its expected performance when given random inputs from the problem domain. It involves analyzing the algorithm's behavior over a range of possible inputs, considering their probability distribution, and calculating the average performance based on this distribution. This analysis helps in understanding how the algorithm typically behaves in real-world scenarios and guides decision-making in algorithm selection and design.

#### Analysis of an Algorithm:
- We are given a sorted array `arr[]={1, 7, 18, 28, 50, 180}`. Here, we have to search a given number and report whether it’s present in the array or not. So, we got two situations here: 
  - **Algorithm 1**: Start from the first element until an element greater than or equal to the number to be searched is found.
  - **Algorithm 2**: Check whether the first or last element is equal to the number. If not, find the number between these two elements (center of the array); if the center element is greater than the number to be searched, repeat the process for the first half else, repeat for the second half until the number is found. And this way, keep dividing your search space, making it faster to search.

`Analyzing Algorithm 1`: (**Linear Search**)
- Suppose we find out the element at the first element of the array. Therefore, we only made one comparison which is obviously constant for any size of the array.
  - *Best case complexity* = `O(1)`
- Suppose, the element will be at the last position. Therefore, our program made **`n`** comparision.
  - *Worst case complexity* = `0(n)`
- *Average case complexity* = `Σ(list of all possible cases)/(total no. of cases)`

`Analyzing Algorithm 2`: (**Binary Search**)
- Suppose, the first element will be the only element that gets compared. Hence, a constant time.
  - *Best case complexity* = `O(1)`
- If not, then we will have to keep dividing the array into halves until we get a single  element.
  -  Therefore, time taken = `n + n/2 +n/4 + ....... + 1` = `logn` with base `2`
  - *Worst case complexity* = `O(log n)`

#### `Space Complexity`:
- Time is not the only thing we worry about while analyzing algorithms. Space is equally important.
- Creating an array of size n (size of the input) → `O(n)` Space  
- If a function calls itself recursively n times, its space complexity is `O(n)`.

####  Why we can't calculate complexity in seconds when dealing with time complexities ?
- Not everyone’s computer is equally powerful. So, We just measure the growth of time with an increase in the input size.
- Asymptotic analysis is the measure of how time (runtime) grows with input.

![Time Complexity Tricks](https://imgur.com/jcvH6cV.png)

### Dis-Joint Sets:
- A set to be an equivalence:
  - `Reflexive`: For every elemet [a ⊆ S]
  - `Symmetric`: a R b; b R a [a ⊆ S]
  - `Transitive`: a R b; b R c --> a R c [a ⊆ S]
- In a non-connected, non-directed graph with two components, each component can be represented as a set. If the intersection of these two sets is an empty set, they are said to be disjoint.
![Dis-Joint Sets](https://imgur.com/qbvmDa4.png)
- We perform two operations here:
  - `FIND`: for finding a given element in a set
  - `UNION`:  For finding the union operations. Perform only when two elements are in two different sets, after performing the union we need to simplify the set by combining the two sets. See, below examples for more clarity:
- `Applications`: 
  - To represent network connectivity
  - To find least common ancestor
  - Kruskal's minimum spanning tree algorithm(graph theory)
- Used where there is a need to partition a set of elements into disjoint subsets and perform operations like merging two sets or finding which set an element belongs to.

#### Operations on Disjoint Sets:
- `MakeSet(x)`: Creates a new set containing element x.
- `Union(x, y)`: Merges the sets containing elements x and y into a single set.
- `Find(x)`: Returns the representative (also known as the "root" or "leader") of the set containing element x
  ![Dis-joint Sets](https://imgur.com/Sr40Mdr.png)

### `Recurrence Relation`:
- **A recurrence relation is an equation or inequality that describes a function in terms of its value on smaller inputs**
- A recurrence relation in algorithms is a mathematical expression that defines the running time or resource usage of an algorithm in terms of smaller subproblems of the same nature.
- Recurrence relations are commonly used to analyze the time complexity of algorithms, particularly in divide-and-conquer algorithms, dynamic programming, and recursive algorithms.

- `Implementation & Solving Techniques of Recurrence Relation`:
  - **Substitution Method**: In this approach, we make an educated guess about the form of the solution and then prove its correctness by induction or other means.
  - **Recursion Tree Method**: This method involves drawing a tree to represent the recursive calls made by the algorithm and then analyzing the total work done at each level of the tree.
  - **Master Theorem**: The Master Theorem provides a concise way to solve recurrence relations of a specific form, particularly those that arise in divide-and-conquer algorithms. It gives solutions in terms of asymptotic bounds.

![Recurrence Relation-1](https://imgur.com/JYj1M4k.png)

![Recurrence Relation-Tricks](https://imgur.com/Qs85OBA.png)


![Questions on recurrence Relation-I](https://imgur.com/iArXmYR.png)

![Questions on Recurrence Relation-II](https://imgur.com/PfhaLY4.png)

### `Masters Theorem`:

- The Master Theorem is a tool used in the analysis of algorithms, particularly in the context of recursive algorithms.
- Determine the time complexity of divide-and-conquer algorithms by providing a simple formula to calculate their time complexity.

![Masters Theorem](https://imgur.com/UXE72fV.png)

### `Binary Search`:

- Algorithm used for finding a target value within a sorted array or list
- Repeatedly divide the search interval in half until the target value is found or determined to be not present in the array.
- Here we need two index pointers: **low** and **high** and if the  low croses the high then index is not found.
- No. of comparison are less than linear search.
- Time Complexity:
  - Minimum = O(1)
  - Maximum = O(log n)
- `Need for Binary Search` because the inefficiency of linear search when dealing with large datasets.
- We `Use Binary Search` because of its speed and efficiency, It drastically reduces the number of comparisons required to find a target value compared to linear search. Hence, ideal choice where quick search operations are necessary, such as searching in databases, sorting algorithms like quicksort and mergesort, and more.

`Binary Search Iterative Method`

```c
int Bin search(A, n, key)
{
  l = 1;
  h = n;
  while(l <= h)
  {
    mid = (l + h) / 2;

    if(key == A[mid])
    {
      return mid;
    }
    if( key <= A[mid])
    {
      h = mid - 1;
    }
    else
      h = mid + 1;
  }
  return 0;
}
```

![Binary Search](https://imgur.com/TPbUq8L.png)

`Binary Search Recursive Method`

```c
Algorithm RBinSearch (l, h, key)
{

  if(l == h)
  {
    if(A[l] == key)
      return l;
    else
      return 0;
  }
  else
  {
      mid = (l + h)/2;
      if(key == A[mid])
        return mid;
      if(key < A[mid])
        return RBinSearch (l, mid-1, key);
      else
        return RBinSearch (mid+1, h, key);
  }
}
```

### `Binary Tree`:

- It is a fundamental hierarchical data structure where each node can have at most two children: a **left child** and a **right child**.
- The topmost node in the tree is called the `root`.
- We should a have nodes from left-right

```md
         1 ---> Root (2 & 3--> its children)
       /   \
      2     3
     / \   / \
    4  5   6  7
```

![Binary Tree](https://imgur.com/fLHtGGi.png)

- **Need and Usage of Binary Trees**:

  - _Efficient Searching and Sorting_: Enables efficient searching (lookup in a dictionary) and sorting due to their inherent ordering.
  - _Dynamic Data Management_: They can grow or shrink as needed, making them suitable for datasets that change over time.
  - _Fast Access_: By following branches based on comparisons, you can quickly locate or insert data.

- **Types**:
  1. `Full Binary Tree`:
    - Every node (except possibly leaf nodes) has two children.
    - All leaf nodes are at the same level.
    - Useful for theoretical considerations or when compactness is a priority
    - Every full binary tree is a complete binary tree
    - ![Full Binary Tree](https://imgur.com/eqFelkz.png)
  2. `Complete Binary Tree`:
    - A binary tree in which every level, except possibly the last, is completely filled, and all nodes are as far left as possible.
    - If we construct a complete binary tree from an array without any gaps or missing elements, it's still called a complete binary tree.
    - A complete binary tree is a full binary tree upto a height `h-1`
    - Efficient heap implementations and certain types of balanced binary search trees where level-order traversal is important.
    - Height of the complete binary tree is minimum only i.e. `log n`
    - ![Complete Binary Tree](https://imgur.com/3cYlwSK.png)

### `Heap`

- A heap is a specialized tree-based data structure designed for efficient retrieval of the minimum or maximum element.
- Retrieving the minimum or maximum element takes constant time `O(1)`
- `Maximum Heap`:

  - Every node has a value greater than or equal to the values of its children.
  - Maximum value is always at the root of the tree.

    - `When to Use`

      1. Scheduling high-priority jobs in a system.
      2. Implementing the Huffman coding algorithm for data compression.

      ```md
             50
            /  \
          30    20
         / \    / \
       15  10  8   16

      Index:   0   1   2   3   4  5   6
      Array: [50, 30, 20, 15, 10, 8, 16]
      ```

- `Minimum Heap`:

  - Every node is having value smaller/equal to all its descend nodes

    - `When to Use`

    1. Finding the shortest path in Dijkstra's algorithm for graph traversal.
    2. Implementing the Prim's algorithm for finding the minimum spanning tree.

    ```md
           8
          /  \
        10    16
        / \   / \
       15 30 20 50

    Index:  0   1   2   3   4   5   6
    Array: [8, 10, 16, 15, 30, 20, 50]
    ```

#### `Insertion Element in Heap`:

- Add new element as a leaf at the below most position
- Then adjust its position while comparing with the ancestors
- Always the direction of adjustment is upward
- _Time Complexity_: **O(1) to O(log n)**

#### `Deletion element from Heap`:

- **Time Complexity**: log n
- **Delete Root**: The element at the root (the maximum in a max-heap, minimum in a min-heap) is removed
- **Move Last Element to Root**: The last element in the heap (which might not be the largest or smallest) is placed in the root position.
- **Heapify Down**
  - If either child is greater/smaller than the new root, swap the new root with the larger/smaller child.
  - Repeat the comparison and swapping process until a position is found where the parent is greater/less than or equal to both children. This ensures the largest/smallest element eventually reaches the root.
- **Result**:
  - Max-Heap: After deletion and heapify down, the new root element will be the next largest element in the heap.
  - Min-Heap: After deletion and heapify down, the new root element will be the next smallest element in the heap
- **Idea**: Delete the element & fill it on an empty array-sorted array

![Insertion & Deletion fromm Heap](https://imgur.com/orucdLq.png)

#### `Heap Sort`:

- Heap-sort is an efficient sorting algorithm that utilizes the properties of a heap data structure to sort an array in `O(n log n)` time complexity
- `Process`
  1. **Create a Maximum Heap**: Convert given array to maximum heap
  2. **Extract Maximum**:
     - Remove the element at the root (the largest in a max-heap).
     - Place it at the end of the unsorted array
  3. **Reduce Heap Size**:
     - Reduce the size by 1
     - Rest of the elements in the heap (size reduced by 1) might violate the heap property because the new root might be smaller than its children.
  4. **Repeat**:
     - Repeat steps 2-4 i.e,
     - Continue extracting the maximum element & place it at the end of the sorted portion & size reduced by 1
  5. **Get Sorted Array**: The entire array becomes sorted. The largest element is at the end, the second largest is second to last, and so on.

#### `Heapify`:

- Process of creating heap from an array
- **Main idea** is to start from the last non-leaf node (i.e., the parent of the last element) and repeatedly heapify each subtree to build the heap from the bottom up.
- Time Complexity: `O(log n)`

#### `Priority Queue`:

- A priority queue (**Prioritizing Elements for Efficient Processing**) is a data structure where elements have priorities and they can be inserted or deleted accordingly
- Smaller the number higher the priority [MIN HEAP]/ Larger the number higher the priority [MAX HEAP]
- Heap is the best DS for implementing priority queue
- The time complexity of insertion and deletion in a heap is `O(log n)`
- `Need`:
  - **Efficient Handling of Urgent Tasks**: Allows you to focus on the most critical items first
  - **Optimization Algorithms**: Various optimization algorithms (Dijkstra's algorithm)
- _Standard queues_ adhere to FIFO, while _Priority queues_ prioritize based on assigned values.

![Merge Sort](https://imgur.com/vzZBXDw.png)

![aMerging](https://imgur.com/b5e7X1y.png)

#### `Pros & Cons of Merge Sort`:

- Large size list
- Linked List
  - We can merge two linked list without creating 3rd linked list
- External Sorting:
  - We can bring pieces or chunck of files from harddisk & merge them
- Stable:

  - If there is a duplicate element in the array/ then the merge will preserve the order

  ```md
  Element of Array: 8, 6, 4, 3, 8, 5, 9 [8 --> (for R); 8 --> (for A)]

        ||  After Merging  ||

  Element of Array: 3, 4, 5, 6, 8(R), 8(A), 9
  ```

![Quick Sort](https://imgur.com/JonbbLM.png)

### `Greedy Method`:

- A greedy method is a particular approach for solving optimization problems (problems which require either minimum/ maximum result) by making a series of choices that appear best at each stage.
- Makes a series of seemingly best choices at each step to solve optimization problems
- May not find the absolute best solution but offers a fast and efficient approach
- Problems should be solved in stages, i.e, in each stages we consider one problem and if the input is feasible, we include it in soln, hence by including all feasible soln, we got optimal solution.
  ```c
   Algorithm Greedy(a, n)
   {
     for( int i = 1; i<= n; i++)
     {
       x = Select (a);
       if (Feasible(x))
       {
         Solutoin =  Solution + x;
       }
     }
   }
  ```

#### `Knapsack Problem`(Greedy-Method):

- It is an optimization problem, we try to pick objects from a list to maximize the total profit while keeping the weight under a certain limit
- It is a container loading problem
- There are two types of Knapsack Problem:
  - Knapsack and 0-1 Knapsack
  - In **Knapsack**, we can take fraction of an object, but in **0-1 Knapsack** Problem, we can only take the whole object or none of it.
- ![Knapsack Problem](https://imgur.com/RPlIkxk.png)
  - Way to solve it:
    1. Calculate the profit per weight ratio for each object
    2. Sort the objects by their profit per weight ratio in descending order
    3. Now, start adding object a/c to the highest profit per weight ratio.
    4. If adding an object exceed the weight capacity, skip the object
    5. Continue, till the bag is full or there are no more objects to add

#### `Job Sequencing with Deadlines`(Greedy-Method):

- The goal is to sequence the jobs in a way that maximizes the total profit while meeting all the deadlines
  ![Job Sequencing](https://imgur.com/qYczosp.png)

#### `Optimal Merge Sort`(Greedy-Method):

- Here, in these kind of problems we use the concept of merging sorted list and combining them into one sorted list
- Always we should merge a pair of short sized list to get the best result
- Time Complexity is O(m+n)
- **Goal** is to find the way to merge multiple sorted lists that minimizes the total merging cost
  ![Optimal Merge Sort-I](https://imgur.com/XKE5MEE.png)
  ![Optimal Merge Sort-II](https://imgur.com/bsVzE9j.png)
- Result = 15+35+95+60 = 205
- Result = 3(5)+3(10)+2(20)+2(30)+2(30) = 205
  - We can calculate this as `n*(size)` --> n = number of link to reach till root node 
#### `Huffman Coding`(Greedy-Method):

- Huffman coding is a compression tecnique that is used to reduce the size of a file or data before transmission over a network
- Here, the frequently used alphabets are assigned shorter codes and less frequent alphabets are assigned longer codes. This way, the overall size of the encoded message is reduced
  ![Huffman Coding](https://imgur.com/tjDSSAL.png)

#### `Minimum-Cost Spanning Tree`:

- **Spanning tree** is a sub-graph of a graph having all vertices but only (n-1) edges
- They do not have cycles
  ![Spanning Tree](https://imgur.com/Kkz7yPN.png)
- For non-connected graph, we cannot calculate spanning tree
- Ways to find minimum-cost spanning tree:
  - Prim's Algorithm
  - Krushkal's Algorithm

#### `Prim's Algorithm`:

![Prims Algorithm](https://imgur.com/SW6uQnY.png)

- Time Complexity = **O(V^2)**

#### `Krushkal's Algorithm`:

![Krushkal's Algorithm](https://imgur.com/dDztIni.png)

- Time Complexity can be improved to **O(E log V)** using a min-heap data structure.

#### `Dijkstra Algorithm`:

- Dijkstra's algorithm, a powerful tool for finding the shortest paths between a starting point and all other reachable nodes in a weighted graph.
- For single source path problem / minimization problem / optimization problem(Greedy Method).
- Works for non-negative edge weights (travel times cannot be negative).
- It guarantees finding the shortest path for all reachable nodes in the graph.
  ![Dijkstra Algorithm](https://imgur.com/VIwft1W.png)

### `Dyanmic Programming`:

- **Dynamic programming** is a powerful technique that efficiently solves complex problems by breaking them into overlapping subproblems, storing solutions for reuse to avoid redundant computations.
- It is tecnique where you find all the solution and then pick up the best solution, the optimal solution
- Follows the `principle of optimality` (Problems must be solved in sequence of decisions)
- Time consuming process
- We use **iterative** instead recursion to save time
- `Cons`:
  - **Memory usage**: Uses tables or caches to store subproblem solutions and lead to high memory usage, especially for problems with large input sizes
  - **Limited applicability**: All problems cann't be solved and works best for problems with optimal substructure and overlapping subproblems

![alt text](https://imgur.com/undefined.png)

#### `Greedy Method v/s Dynamic Programming`:

|            Feature            |      Greedy Method      |    Dynamic Programming     |
| :---------------------------: | :---------------------: | :------------------------: |
|           Approach            | Locally optimal choices |    Optimal substructure    |
| Guarantee of Optimal Solution |           No            |  Yes (if solution exists)  |
|        Execution Speed        |         Faster          |    Slower (potentially)    |
|   Implementation Complexity   |    Generally simpler    | More complex design needed |

### `MultipleStage Graph`(Dynamic Programming):

- Multi-Stage Graph is a directed weighted graph where the vertices are divided into stages
- It is useful for resource allocation
- `Objective`:- Select the path which give minimum cost.

![Multi-Stage Graph-I](https://imgur.com/dX5ECL4.png)
![Multi-Stage Graph-II](https://imgur.com/T2TUBEj.png)

### `Floyd-Warshall`(Dynamic Programming):

- **Floyd-Warshall** is a dynamic programming algorithm for finding the shortest paths between all parts of vertices in weigted graph.
- Time complexity is `O(n^3)` (n --> number of vertices in the graph)

![Floyd-Warshall](https://imgur.com/35QE4S7.png)

### `Matrix Chain multiplication`(Dynamic Programming):

- Matrix chain multiplication is when you have chain of matrices to multiply
- The order in which you multiply the matrices, affect the amount of multiplications one need to perform.
- So, we use **Dynamic programming** to find the order that minimizes the number of multiplications required.
- Number of parenthesis required = `2n^Cn / (n+1)` where, n = (n-1)
- Here we start by using the concept that differences b/w i and j is 1, then 2 and so on. (refer image)

![Matrix-Chain  Multiplication](https://imgur.com/db0xeXo.png)

### `Bellman Ford Algorithm` (Single Source Shortest Path/ Dynamic Programing):
- A **DP** algorithm used for finding the shortest path in a weighted-graph even for the one having the negative edges.
- It does this by relaxing the edges repeatedly. Basically, it iterates/relax the edges and updates the shortest distance if a short one is found
- Process continues till `n-1`, where **n** is the no. of vertices
- In case of **Complete Graph** (there is an edge between every pair of vertices), *Bellman Ford Algorithm* takes **0(n^3)** --> worst case 
- `Relaxation of (u,v)`:
  - Between a pair of vertices lets say (u,v), if there is an edge then check if the distance of **u + cost of edge (u,v) < distance of v** then change the distance of v to distance **u + cost(u,v)** i.e, 
```c
if (d[u] + c(u,v) < d[v])
then 
  d[v] = d[u] +c(u,v)
```
Here is an example:
![Bellman Ford Algorithm-I](https://imgur.com/k6IC5k3.png)
- Detects if there is a negative weighted cycle is present / not:
  - If after (n-1) relaxation/iteration an edge relaxation changes to distance to a vertex, it means there is a negative weighted cycle. In this way, the Bellman Ford Algorithm cannot find the shortest path in graphs with negative weight cycle, but it can detect them
Here, is an example:
  ![Bellman Ford Algorithm-II](https://imgur.com/irr8Gsc.png)

### `0/1 Knapsack Method:`
- `Objective`: Fill objects in such a way that the total profit gets maximised
![0/1 Knapsack](https://imgur.com/HpLqpi4.png)
![0/1 Knapsack](https://imgur.com/eWocc2A.png)

### `Optimal Binary Search Tree(Successful & Unsuccessful Probability)`

- `Binary Search Tree`: A data structure that consists of nodes, where these nodes contain a **key** and two **link** (Right & Left child)
- `Cost of Searching`:  No. of comparision required to find a key, depends on the level of search
- The cost is defined as the sum of the probabilities of all the nodes in the tree multiplied by their depth
  - Maximum comparision = height/level of binary search tree
  - If the height of binary search tree is less, then comparision  will also be less
- Searches are of two types:
  - `Successful`: Search is called successful, if the key element is found
  - `Un-successful`: Search is called un-successful, if the key element is not found
  
![OBST](https://imgur.com/TcFSkkt.png)
![OBST](https://imgur.com/HqsWlpE.png)
![OBST](https://imgur.com/ojxh0re.png)
- `Optimal Binary Search Tree`: It is a binary search tree such that the cost of searching should be minimum
  - Cost also depends on the height of binary search tree
- We use **DP** for finding the optimal-binary search tree. This include creating the table to store the minimum cost for each possible subtrre. Afterthat, table is built iteratively, starting with the smallest subtrees and upto root. At the end, we use **backtracking** through the table to find the optimal arrangement of nodes in the tree
- Root should be the one that minimizes the total cost of searching in the tree 
- A problem of optimal binary search tree is if the keys and their probabilities are gien and we have to generate a binary search tree such that the cost if searching should be minimum

![OBST](https://imgur.com/shSHqDi.png)

### `Travelling Sales Problem`:
- **Problem**: We have to start from one vertex and travel all other vertices once and to return back to the same starting vertex and the cost of tracking shoukd be minimum
- Order of execution is different/ but the recursion tree in the figure look:
![Travelling Sales Problem](/Images/image-6.png) 

### `Reliability Design-DP`:
- It signifies the optimal number of device copies having max reliability with minimum cost
- Probability of system = **π** (Product of all reliabilities)
- Probability of a product in good working condition = `r`
- Probability of a product not in good working comditin = `(1-r)`
  - Probability of same n products = `(1-r)^n`
- Uppetr bond is the maximum number of copies of a device that can be used for optimal solution
- `Problem`: We have to set-up a system such that if we have total cost ac 'C', by buying devices such that, how many copies of these devices should i buy if within that cost such that the total reliability of the system is maximised


### `Longest Common Sequence`(LCS):
- A classic CS problem that involves finding the longest sequence common to two sequences.
- Its sequence is formed by deleting some elements (not common) without changing the order of the remaining

![LCS](https://imgur.com/7wO92O0.png)
- Recursion way to trace  longest common sequences- top-down approach
- If you are storing the result of recirsion then it is called, `memorization`
- Memorization reduces the number of call

- **Visiting Vertex**: Ging on a particular vertex
- **Exploration of Vertex**: If i'm on a particular vertex then visiting all its adjacent vertex

![alt text](https://imgur.com/XQskRfk.png)

### `Graph Traversal`:
- We use **Graph traversal** to visit and explore all nodes in a graph
![Graph Traversal](https://imgur.com/j2CHCvb.png)
- `Breadth First Search`(**BFS**):
  - Explore all the nodes at the current depth level before moving on to nodes at the next depth level
  - It uses **Queue** data structure to keep track of nodes to visit next
  - It guaranteed to find the shortest path between nodes in an unweighted graph
  - It has a time complexity of `O(V + E)`
![BFS](https://imgur.com/RhMNvjx.png)
- `Depth First Search`(**DFS**):
  - Explore as far as possible along the current branch before backtracking
  - It uses **Stack** data structure(either explicitly & implicitly) to keep track of nodes to visit next
  - It may not always find the shortest path between nodes in an unweighted graph
  - It has a time complexity of `O(V + E)`
  ![DFS](https://imgur.com/XPRxWDH.png)
  ![BFS vs DFS](https://imgur.com/5d1F8EQ.png)

### `Articulation Point`:
- These are the points/vertex in the graph whose removal will disconnect the graphs into multiple components
- We use **DFS** 
![Articulation Point](https://imgur.com/eCcQ6zd.png)
- Two vertices (parent & child) `(u,v)`:
  - L[v] >= d[u],   u will bw an articulation point ---> this isnot for the root
  - If root is having more than one child then it is said that root is an articulationn point

### `Backtracking`(Brute Force Approach):
- It is a general algorithm for finding all (or some) solutions, particularly constraint satisfaction problems.
- Same as DP but the difference is that it is nor optimization problem and do not use binding function
- Followss DFS
![Backtracking](https://imgur.com/LJfbQle.png)
-  Pros:
   - **Flexible**: Can be applied to a wide range of problems
   -  **Efficient**: Works by forming space tree, reducing the number of calls

### `N Queen Problem Using Backtracking`:

- A classic computer science problem where the goal is to place N queens on an N x N chessboard such that no two queens threaten each other.
- One popular approach to solve this problem is using a technique called backtracking.
-  Backtracking is a depth-first search (DFS) algorithm that involves exploring all possible solutions until a valid one is found
- Bounding Function is that:
  - Not in same row 
  - Not in same column
  - Not in same diagonal 

![N Queen](https://imgur.com/Npo1Zv0.png)

### `Sum of Subset Problem`:
![Sum of Set](https://imgur.com/YTdlRhb.png)

### `Graph Coloring Problem`:
- There are two types of problems regarding the colouring of graphs:
  1. Graphs can be coloured or not, called `M-Coloring Decision Problem`. It's also called **Chromatic Problem**
  2. Minimum number of colours required to colour graph, called `M-Colouring Optimization Problem`
- Bounding Function is that the neighbouring vertex shouldn't have same colour
- Exponential Problem
![Graph Coloring Problem](https://imgur.com/aXxygda.png)


### ``Hamiltonian Cycle``:
- Start from a vertex, visit all the other vertices and return back to the starting vertex. This forms a cycle:
  - if cycle is present then it is called `Hamiltonian Cycle`
  - if cycle is not present then it is not called Hamiltonian cycle
- It is **NP-Hard** problem, i.e, Exponential Problem
-  NOTE: If the starting vertex is changed then there is no change in the cycle

![Hamiltonian_Cycle](https://imgur.com/1zv5Lxh.png)
- Duplicate edges are not accepted
- And the last edge is also connected to the starting vertex 
-  If in a cycle a vertex connecting two graphs and behaving as a junction then no Hamiltonina Cycle is present and that's we call `Articulation Point` 
-  Also, Hamiltonian cycle are not present in case of cycle having `pendant`

![Hamiltonian_Cycle](https://imgur.com/bivYxHO.png)
- Bonding Function:
  - Shouldn't take duplicate
  - Whenever you take any vertex, there should be an edge from previous vertex
  - If on the last vertex,then there must be an edge from the last to the first vertex 
- Initially all values are zero `| 0 | 0 | 0 | 0 | 0 |`
- If any vertex is apearing again then it'll be avoided,else if there is an edge present then it's valid
- We fix the first vertex (lets say 1)  `| 1 | 0 | 0 | 0 | 0 |`
- Now, for position **2**,adjacent vertex shouldn't have **1 & 0**. Therefore, the posibility left are (2, 3, 4, 5). After, checking this we have to check whether from **1 to 2** there is a connection in the graph `| 1 | 2 | 0 | 0 | 0 |`
- Now,for position **3**,  *2 and 1* should not be present. Therefore, the possibility left are (3, 4, 5) `| 1 | 2 | 3 | 0 | 0 |`
- Similarly, `| 1 | 2 | 3 | 4 | 5 |`


### `Branch and Bound Function`:
- Uses state space tree and follows BFS
- It uses both the Queue and Stack data structure for developing the state space tree, i.e, FIFO and LIFO
- Useful for solving optimazation problem and minimization problem
- We use 3 methods 
  1. Queue (FIFO)
  2. Stack (LIFO)
  3. Least Cost Branch Bound(LC-BB) 
- The one having least cost expand earlier. Instead of generating the entire tree, we always try to pick up the one with least cost and try to expand it.(Basic idea of LC-BB)
- LC-BB is faster than FIFO and LIFO

### `Job Sequencing with Deadline-Branch and Bound`:
- We have to select the job such that the penality is minimized
- `u` is the sum of all penalties except that included in solution
  - **u =   Σ Pi (i ∈ S)**
- `c` is the sum of all penalties till the last job considered 
  - **c =   Σ Pi (i ∉ S)** 
- If the cost exceeds the upper bond then don't include

![job sequence](https://imgur.com/Efm8R6T.png)


### `0/1 Knapsack using Branch and Bound`:
- Total objects included should be less than the capacity of objective
- Take complete object not the fraction
- Its a maximization problem. So, we need to convert it to minimization problem to solve this via Branch and Bound and we use LC-BB
- We take the uppen bound initially to infinity
- We generate the state-space tree


![0/1 Knapsack](https://imgur.com/KecNXRn.png)


### `Travelling Salesman Problem`:
- While generation cost for everynode, and for any node if the cost is greater than the upper bond then kill the node
- Process:
  - Take the cost adjency-matrixx and start reducing it
    - Write the minimum element of a row
    - Reduce the row (subtracting the minimum value form every element)
    - Add all 
    - Now, reduce the column (same way) and add all
    - Now, solve using **backtracking**
- We need to update the upper bond once we reacch the leaf node
![TSP](https://imgur.com/qqzuaqa.png)

### `NP-Hard and NP-Complete`:
- We distinguish Algorithm here into two categories:
  - Polyomial Time-Taking 
    - Linear Search (n)  
    - Binary Search (log n)
    - Insertion Sort (n^2)
    - Merge Sort (n log n)
    - Matrix Multiplication (n^3)
  - Exponential Time-Taking 
    - 0/1 Knapsack (2^n)
    - Travelling Sales Problem (2^n)
    - Sum of Subsets (2^n)
    - Graph Coloring  (2^n)
    - Hamiltonian Cycle  (2^n)
- We prefer those algorithm that takes less order of time. So, for exponential time taking algorithms (that take more time), we need to convert them to polynomial time taking algorithm (so that time reduced). But, it's not possible till now.
- For showing any exponential problem to the polyhnomial one, we need to do 2 things:
  - Try to show similarity b/w the exponential algorithms such that if one of them gets solved all others solved. We try to relate the problem either by solving it or at least relating them
  - When we are unable to write the deterministic algorithm just try to  write non-deterministic algorithm
- Guidelines or Frame-works made for doing research on exponential time taking algorithm and that guidelines or frameworks are called **NP-Hard** and **NP-Complete** 
- Non-Deterministic Search Algorithm are basically Deterministic Search Algorithm with some extra documents
- We have to preserve our work so that in future if somebody else is working on our problem, then he can make non-determinithstic part as deterministic

![NP-Hard](https://imgur.com/Ujtuyvz.png)

- `Satisfiability Problem` is to find out value of xi. The values include 1(if iincluded) and 0(if not included) 
```md
        x1   x2   x3
       --------------
         0    0    0
         0    0    1
         0    1    0
         1    0    0                            Here, we have 3 variables,
         0    1    1                            therefore this takes **2^3**
         1    0    1                            times. And, for n  it  takes 
         1    1    0                            `2^n` --> exponential time taking algo
         1    1    1
```
- For representing the satisfiability problem we use state space tree
- Our task is to shoe similarities b/w exponential problem and satisfiability. Such that if satisfiability gets solved all gets solved
- If you are unable to solve them, at least show relationship b/w them such that if one of the problems is solved all others gets solved
- **How to relate**:
  - For this we need a base formula, `CNF` formula that is proportional calculate formula using boolean variables.
  
   ```md
    Xi = {x1, x2, x3}
   CNF = (X1 V X̄2 V X3) ^ (X̄1 V X2 V X̄3)
         -------------    --------------
               |                |
               V                V
          clause(C1)         clause(C2)
   Clause are formed using disjunction and they are joined with conjunction
   ```
- By using **Reduction** a relationship procedure used to relate them
- We take a general formu;a and that formula will convert into exponential problem(0/1 Knapsack). If the problem solve in polynomial time then all can solved
- The conversion also takes polynomial time
- We said satisfiability is NP-Hard and 0/1 Knapsack and other as Hard. But, if the reduction happen other also becomes NP-Hard 
- If we reduce satisfiability to some problem `L` then that also become NP-Hard. These are transitive in nature 
```md
    satisfiability <--> L1 <--> L2
         NP             NP      NP
```
![Satisfiability Problem](https://imgur.com/wtN3IiA.png)
- If one is able to prove that `P = NP` then it is proved that whatever is non-determionistic we are writing, tomorrow that may be deterministic 
  ```md
  P ⊆ NP
  P = NP
  ```