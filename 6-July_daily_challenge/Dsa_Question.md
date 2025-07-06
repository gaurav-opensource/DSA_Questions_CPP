## Problem: Find Sum Pairs

### Problem Statement:

You are given two integer arrays `nums1` and `nums2`. You need to design a class `FindSumPairs` with the following operations:

* **Constructor**: Initializes the object with the integer arrays `nums1` and `nums2`.
* **add(index, val)**: Adds `val` to `nums2[index]`.
* **count(tot)**: Returns the number of pairs `(i, j)` such that `nums1[i] + nums2[j] == tot`.

### Code Implementation (C++):

```cpp
class FindSumPairs {
public:
    vector<int> nums1;
    vector<int> nums2;
    unordered_map<int, int> freq2;

    FindSumPairs(vector<int>& nums1, vector<int>& nums2) {
        this->nums1 = nums1;
        this->nums2 = nums2;

        // Count frequency of elements in nums2
        for (int num : nums2) {
            freq2[num]++;
        }
    }

    void add(int index, int val) {
        int oldVal = nums2[index];
        freq2[oldVal]--;

        if (freq2[oldVal] == 0) {
            freq2.erase(oldVal);
        }

        nums2[index] += val;
        freq2[nums2[index]]++;
    }

    int count(int tot) {
        int count = 0;
        for (int num : nums1) {
            int complement = tot - num;
            if (freq2.find(complement) != freq2.end()) {
                count += freq2[complement];
            }
        }
        return count;
    }
};
```

### Approach:

1. **Constructor:**

   * Store `nums1` and `nums2`.
   * Create a frequency map `freq2` of elements in `nums2`.

2. **add(index, val):**

   * Decrease the frequency of the current value at `nums2[index]`.
   * Update the value at `index` by adding `val`.
   * Increase the frequency of the new value in `freq2`.

3. **count(tot):**

   * For each number `num` in `nums1`, calculate `tot - num` (complement).
   * If `complement` exists in `freq2`, add its frequency to the count.

### Use Cases:

* Efficient way to maintain dynamic pairs.
* Fast lookup due to hash map (unordered\_map).

### Time Complexity:

* Constructor: O(n), where n = size of nums2
* add: O(1)
* count: O(m), where m = size of nums1






## 802. Find Eventual Safe States

### Problem Statement

There is a directed graph of `n` nodes labeled from `0` to `n - 1`. The graph is represented by a 2D integer array `graph` where `graph[i]` is a list of all nodes that node `i` has edges to.

A node is called a **terminal node** if it has no outgoing edges.
A node is called a **safe node** if every possible path starting from that node leads to a terminal node (or another safe node).

**Return:**
An array containing all the safe nodes of the graph. The answer must be **sorted in ascending order**.

---

### Example:

```
Input: graph = [[1,2],[2,3],[5],[0],[5],[],[]]
Output: [2,4,5,6]
```

---

### Pseudocode (Using Reverse Graph and Kahn's Algorithm):

```
function eventualSafeNodes(graph):
    n = graph.length
    reverseGraph = [[] for _ in range(n)]
    indegree = [0] * n

    for u in range(n):
        for v in graph[u]:
            reverseGraph[v].append(u)
            indegree[u] += 1

    queue = [i for i in range(n) if indegree[i] == 0]
    result = []

    while queue is not empty:
        node = queue.pop()
        result.append(node)

        for neighbor in reverseGraph[node]:
            indegree[neighbor] -= 1
            if indegree[neighbor] == 0:
                queue.append(neighbor)

    return sorted(result)
```

---

### Concepts Used:

* Graph traversal
* Reverse graph
* Kahn’s algorithm (Topological Sort)
* Terminal & safe node definitions

### Time Complexity:

* **O(V + E)** where V is the number of nodes and E is the number of edges

### Space Complexity:

* **O(V + E)** for storing the graph and auxiliary structures

---

### Alternate Approach:

* DFS with memoization to detect cycles and mark safe nodes accordingly



## 802. Find Eventual Safe States

### Problem Statement

There is a directed graph of `n` nodes labeled from `0` to `n - 1`. The graph is represented by a 2D integer array `graph` where `graph[i]` is a list of all nodes that node `i` has edges to.

A node is called a **terminal node** if it has no outgoing edges.
A node is called a **safe node** if every possible path starting from that node leads to a terminal node (or another safe node).

**Return:**
An array containing all the safe nodes of the graph. The answer must be **sorted in ascending order**.

---

### Example:

```
Input: graph = [[1,2],[2,3],[5],[0],[5],[],[]]
Output: [2,4,5,6]
```

---

### Pseudocode (Using Reverse Graph and Kahn's Algorithm):

```
function eventualSafeNodes(graph):
    n = graph.length
    reverseGraph = [[] for _ in range(n)]
    indegree = [0] * n

    for u in range(n):
        for v in graph[u]:
            reverseGraph[v].append(u)
            indegree[u] += 1

    queue = [i for i in range(n) if indegree[i] == 0]
    result = []

    while queue is not empty:
        node = queue.pop()
        result.append(node)

        for neighbor in reverseGraph[node]:
            indegree[neighbor] -= 1
            if indegree[neighbor] == 0:
                queue.append(neighbor)

    return sorted(result)
```

---

### Concepts Used:

* Graph traversal
* Reverse graph
* Kahn’s algorithm (Topological Sort)
* Terminal & safe node definitions

### Time Complexity:

* **O(V + E)** where V is the number of nodes and E is the number of edges

### Space Complexity:

* **O(V + E)** for storing the graph and auxiliary structures

---

### Alternate Approach:

* DFS with memoization to detect cycles and mark safe nodes accordingly
