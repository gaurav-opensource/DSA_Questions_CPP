# Create markdown content for Fibonacci Series using Recursion

fibonacci_md = """
# 🔁 Fibonacci Series – Using Recursion

---

## ✅ Question:

**Problem Statement:**  
Write a recursive function to return the `n`th Fibonacci number.

The Fibonacci sequence is defined as:
- `F(0) = 0`
- `F(1) = 1`
- For `n > 1`: `F(n) = F(n-1) + F(n-2)`

---

## 🧪 Examples:

- Input: `n = 0` → Output: `0`
- Input: `n = 1` → Output: `1`
- Input: `n = 5` → Output: `5`
- Input: `n = 7` → Output: `13`

Sequence: `0, 1, 1, 2, 3, 5, 8, 13, ...`

---

## 🧠 Approach:

Use recursion by calling the function for the previous two Fibonacci numbers:
- Base Case: If `n == 0` return 0, if `n == 1` return 1
- Recursive Case: Return `fib(n - 1) + fib(n - 2)`

---

## 💻 Pseudocode (C++ Style):

```cpp
class Solution {
public:
    int fib(int n) {
        if (n == 0) return 0;
        if (n == 1) return 1;
        return fib(n - 1) + fib(n - 2);
    }
};
