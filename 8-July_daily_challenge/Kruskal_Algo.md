# 🌲 Kruskal's Algorithm - Minimum Spanning Tree (MST) Cheat Sheet

## ✅ What is Kruskal’s Algorithm?

Kruskal’s algorithm is a **greedy algorithm** used to find the **Minimum Spanning Tree (MST)** of a **connected, undirected, weighted graph**.

---

## 📚 Key Concepts

- **Spanning Tree**: A subset of the graph that connects all vertices with no cycles.
- **MST**: The spanning tree with the **minimum total edge weight**.
- **Greedy Nature**: Always pick the edge with the **lowest weight** that doesn't form a cycle.

---

## 🧠 Steps to Find MST Using Kruskal’s Algorithm

1. **Sort** all edges in **non-decreasing** order of their weights.
2. Initialize Disjoint Set Union (DSU) to track connected components.
3. For each edge in sorted list:
    - If it **doesn't form a cycle**, include it in MST.
    - Otherwise, **discard** it.
4. Stop when the MST has **(V - 1)** edges.

---

## 🧩 Cycle Detection via Disjoint Set Union (DSU)

### DSU Operations:
- `FIND(x)` → returns representative (parent) of set x belongs to
- `UNION(x, y)` → merges the two sets if they're disjoint

These help efficiently detect cycles while building the MST.

---

## 🔧 Pseudocode

```text
function KruskalMST(V, edges):
    sort(edges by increasing weight)
    DSU = new DisjointSet(V)
    mstWeight = 0
    count = 0

    for each edge (u, v, weight) in edges:
        if DSU.find(u) != DSU.find(v): // no cycle
            DSU.union(u, v)
            mstWeight += weight
            count += 1
            if count == V - 1:
                break

    return mstWeight
