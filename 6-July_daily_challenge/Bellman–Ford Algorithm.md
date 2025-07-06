from pathlib import Path

# Content for the Bellman-Ford Algorithm Markdown file
md_content = """
# 📘 Bellman-Ford Algorithm

The **Bellman-Ford Algorithm** is used to find the shortest paths from a single source vertex to all other vertices in a weighted graph, even when some of the edge weights are negative.

---

## 🧠 Key Concepts

- Handles **negative edge weights**.
- Can **detect negative weight cycles**.
- Based on **edge relaxation** repeated (V - 1) times.
- Time Complexity: **O(V × E)**

---

## 📌 Problem Statement

Given a graph with `V` vertices and `E` edges, and a source vertex `src`, compute the shortest distance to all vertices from `src`.

### ➤ Special Cases

- If a node is **unreachable**, mark its distance as `108` (1e8).
- If there's a **negative weight cycle**, return `-1`.

---

## 🧮 Example 1

**Input**:  
`V = 5`  
`edges = [[0, 1, 5], [1, 2, 1], [1, 3, 2], [2, 4, 1], [4, 3, -1]]`  
`src = 0`

**Output**: `[0, 5, 6, 6, 7]`

### 📊 Explanation


---

## ❌ Example 2 (Negative Cycle)

**Input**:  
`V = 4`  
`edges = [[0, 1, 4], [1, 2, -6], [2, 3, 5], [3, 1, -2]]`  
`src = 0`

**Output**: `[-1]`

### ❗Explanation

A negative weight cycle exists: `1 -> 2 -> 3 -> 1` with total weight < 0.

---

## 🔧 Why (V - 1) Relaxations?

A shortest path can have at most (V - 1) edges (any more forms a cycle).  
So relaxing all edges (V - 1) times guarantees covering all simple paths.

---

## 🔄 Detecting Negative Cycles

If a **V-th** relaxation changes any distance, a negative cycle exists.  
This is because shortest paths should have stabilized after (V - 1) iterations.

---

## 💡 Principle of Edge Relaxation

Relax edge (u, v) with weight w:  
```cpp
if dist[v] > dist[u] + w:
    dist[v] = dist[u] + w


#include <iostream>
#include <vector>
using namespace std;

vector<int> bellmanFord(int V, vector<vector<int>>& edges, int src) {
    vector<int> dist(V, 1e8);
    dist[src] = 0;

    for (int i = 0; i < V; i++) {
        for (vector<int> edge : edges) {
            int u = edge[0], v = edge[1], wt = edge[2];
            if (dist[u] != 1e8 && dist[u] + wt < dist[v]) {
                if (i == V - 1)
                    return {-1};
                dist[v] = dist[u] + wt;
            }
        }
    }
    return dist;
}

int main() {
    int V = 5;
    vector<vector<int>> edges = {
        {1, 3, 2}, {4, 3, -1}, {2, 4, 1}, {1, 2, 1}, {0, 1, 5}
    };
    int src = 0;
    vector<int> ans = bellmanFord(V, edges, src);
    for (int dist : ans) cout << dist << " ";
    return 0;
}
