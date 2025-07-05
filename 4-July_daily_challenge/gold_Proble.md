# 🔍 Path with Maximum Gold (Leetcode #1219)

## 📉 Problem Statement

You are given a `grid[m][n]` where each cell contains some gold (a positive integer) or 0 (no gold). You can start from any cell with gold and move in **4 directions** (up, down, left, right), but you **cannot visit the same cell more than once in the same path**, and you **cannot move to a cell with 0**.

### 🌟 Goal:

Return the **maximum amount of gold** you can collect from any valid path.

---

## 🔍 Example:

### Input:

```cpp
grid = [
  [0,6,0],
  [5,8,7],
  [0,9,0]
]
```

### Output:

```
24
```

### Explanation:

* One possible path is: `9 → 8 → 7`
* Total: `9 + 8 + 7 = 24`

---

## 🧪 Approach: DFS + Backtracking + Direction Array

### Key Points:

* Use DFS to explore from each non-zero cell
* Use a `dir` array to simplify 4-direction movement
* Mark cells visited by setting to 0, and backtrack

---

## 🔀 C++ Code with `dir` Array

```cpp
class Solution {
public:
    int getMaximumGold(vector<vector<int>>& grid) {
        int maxGold = 0;
        int m = grid.size(), n = grid[0].size();

        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                if (grid[i][j] != 0) {
                    maxGold = max(maxGold, dfs(grid, i, j));
                }
            }
        }

        return maxGold;
    }

private:
    // Direction array: up, down, left, right
    vector<vector<int>> dirs = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};

    int dfs(vector<vector<int>>& grid, int i, int j) {
        int m = grid.size(), n = grid[0].size();

        if (i < 0 || i >= m || j < 0 || j >= n || grid[i][j] == 0)
            return 0;

        int currGold = grid[i][j];
        grid[i][j] = 0;  // mark visited

        int maxNeighbor = 0;
        for (auto dir : dirs) {
            int ni = i + dir[0];
            int nj = j + dir[1];
            maxNeighbor = max(maxNeighbor, dfs(grid, ni, nj));
        }

        grid[i][j] = currGold;  // backtrack
        return currGold + maxNeighbor;
    }
};
```

---

## 🔢 Time & Space Complexity

* **Time Complexity:** O(m × n × 4^k), where k = number of gold cells (in worst case)
* **Space Complexity:** O(k) recursion stack (DFS)

---

## 🔍 Summary

* Use DFS and backtracking to explore all paths
* The direction array helps simplify movement code
* Track and return the maximum gold collected in all valid paths

---

## 📚 Useful for:

* Maze traversal problems
* Backtracking practice
* Grid-based DFS optimization with direction arrays

---
