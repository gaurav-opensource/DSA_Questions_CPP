# Write the Josephus problem details to a markdown file (not downloading, just writing content)

josephus_md = """
# 🔄 Josephus Problem – Last Person Standing

---

## ✅ Question:

**Problem Statement:**  
You are playing a game with `n` people standing in a circle, numbered from 1 to `n`.  
Starting from person 1, every `k`th person is eliminated in a **circular** fashion.  
The process continues until only one person remains.

🎯 Your task is to return the **position (1-based index)** of the person who will survive.

---

## 🧪 Examples:

- Input: `n = 5, k = 2` → Output: `3`  
- Input: `n = 7, k = 3` → Output: `4`

---

## 🧠 Approach:

This problem is a classic example of **recursion** known as the **Josephus Problem**.

### 💡 Logic:
Let `f(n, k)` be the position of the survivor among `n` people when every `k`th person is eliminated.  
The recurrence relation is:


This gives a 0-based index. To convert to 1-based index, add 1 at the end.

---

## 💻 Pseudocode (C++ Style):

```cpp
class Solution {
  public:
    int josephus1(int n, int k) {
        if (n == 1) return 0; // 0-based index
        return (josephus1(n - 1, k) + k) % n;
    }
    int josephus(int n, int k) {
       return josephus1(n, k) + 1;
    }
};
