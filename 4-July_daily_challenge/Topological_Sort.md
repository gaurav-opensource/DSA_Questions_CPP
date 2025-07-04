# 🧠 Topological Sorting in Directed Acyclic Graphs (DAGs)

---

## 📘 What is Topological Sorting?

Topological sorting of a **Directed Acyclic Graph (DAG)** is a linear ordering of vertices such that for every directed edge `u → v`, vertex `u` comes before `v` in the ordering.

> 🔔 **Note:** Topological sort is **not possible** for:
>
> * Graphs with **undirected edges** (as edges imply mutual dependency).
> * Graphs with **cycles** (circular dependency causes contradiction).

### Example Output

For the graph:

```cpp
Edges: { {2, 3}, {3, 1}, {4, 0}, {4, 1}, {5, 0}, {5, 2} }
```

Possible outputs:

* `5 4 2 3 1 0`
* `4 5 2 3 1 0`
* Multiple valid topological orders may exist.

## 💡 Real Life Analogy

To reach school:

* You must get dressed.
* You cannot wear **shoes before socks**.
* You can brush before or after wearing socks → Some tasks are flexible.

## 🔄 Why DAGs Only?

* **Undirected Graphs:** Implies bidirectional dependency (u → v and v → u), breaking the order logic.
* **Cyclic Graphs:** Every node in the cycle depends on each other, forming a loop — no node can be placed before the others.

---

## ⚙️ DFS-based Algorithm for Topological Sort

### 📋 Pseudocode

```text
function topologicalSort(V, edges):
    adj = build adjacency list
    visited = [false] * V
    stack = empty stack

    for each vertex v in V:
        if not visited[v]:
            dfs(v, adj, visited, stack)

    result = []
    while stack is not empty:
        result.append(stack.pop())

    return result

function dfs(v, adj, visited, stack):
    visited[v] = true
    for each neighbor u in adj[v]:
        if not visited[u]:
            dfs(u, adj, visited, stack)
    stack.push(v)
```

---

## 🧑‍💻 C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

void topologicalSortUtil(int v, vector<vector<int>> &adj, vector<bool> &visited, stack<int> &st) {
    visited[v] = true;
    for (int i : adj[v]) {
        if (!visited[i])
            topologicalSortUtil(i, adj, visited, st);
    }
    st.push(v);
}

vector<vector<int>> constructadj(int V, vector<vector<int>> &edges) {
    vector<vector<int>> adj(V);
    for (auto it : edges) {
        adj[it[0]].push_back(it[1]);
    }
    return adj;
}

vector<int> topologicalSort(int V, vector<vector<int>> &edges) {
    stack<int> st;
    vector<bool> visited(V, false);
    vector<vector<int>> adj = constructadj(V, edges);

    for (int i = 0; i < V; i++) {
        if (!visited[i])
            topologicalSortUtil(i, adj, visited, st);
    }

    vector<int> ans;
    while (!st.empty()) {
        ans.push_back(st.top());
        st.pop();
    }
    return ans;
}

int main() {
    int v = 6;
    vector<vector<int>> edges = {{2, 3}, {3, 1}, {4, 0}, {4, 1}, {5, 0}, {5, 2}};
    vector<int> ans = topologicalSort(v, edges);

    for (auto node : ans) {
        cout << node << " ";
    }
    cout << endl;
    return 0;
}
```

---

## 📌 DSA Interview Questions Based on Topological Sort

1. **[Leetcode 210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)**

   * Find the order in which you should take courses given prerequisites.

2. **[Leetcode 207. Course Schedule](https://leetcode.com/problems/course-schedule/)**

   * Check if it is possible to finish all courses (cycle detection in DAG).

3. **\[Kahn’s Algorithm (Topological Sort using BFS)]**

   * Implement an alternate method of topological sort.

4. **Task Scheduling**

   * Given tasks with dependencies, return a valid task order.

5. **Alien Dictionary (Google)**

   * Given dictionary words in alien language, derive the order of characters (topological sort of chars).

6. **Build System Order (e.g., Makefile)**

   * Build dependencies (modules depending on other modules).


* Note : If you hear “prerequisite”, “dependency”, “order of execution” → Think Topological Sort.
---

Let me know if you want Kahn’s Algorithm version or a Python solution!
