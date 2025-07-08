
# 📚 Monotonic Stack (Complete Notes)

## 🔷 What is a Monotonic Stack?

A monotonic stack is a stack where elements are kept in either:

- **Increasing order** (from bottom to top) → *Monotonic Increasing Stack*
- **Decreasing order** (from bottom to top) → *Monotonic Decreasing Stack*

These stacks are used to efficiently solve problems involving **next/previous greater or smaller elements**.

---

## 🔹 Monotonic Increasing Stack

### 🔸 Definition:
- Stack maintains **increasing order** from bottom to top.
- While pushing: Remove elements **greater** than the current to maintain order.

### 🔸 Properties:
- Top always holds the **smallest recent element**.
- Used to find **Next Smaller Element**, **Previous Smaller Element**, etc.

### 🔸 Example:
**Input:** `[3, 1, 4, 1, 5, 9, 2, 6]`  
**Output Stack:** `[1, 1, 2, 6]`

### 🔸 JavaScript Code:
```javascript
function monotonicIncreasing(nums) {
    const stack = [];
    const result = [];

    for (let i = 0; i < nums.length; ++i) {
        while (stack.length && stack[stack.length - 1] > nums[i]) {
            stack.pop();
        }
        stack.push(nums[i]);
    }

    while (stack.length) {
        result.unshift(stack.pop());
    }

    return result;
}
```

### 🔸 Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(N)

---

## 🔹 Monotonic Decreasing Stack

### 🔸 Definition:
- Stack maintains **decreasing order** from bottom to top.
- While pushing: Remove elements **smaller** than the current.

### 🔸 Properties:
- Top always holds the **largest recent element**.
- Used to find **Next Greater Element**, **Previous Greater Element**, etc.

### 🔸 Example:
**Input:** `[3, 1, 4, 1, 5, 9, 2, 6]`  
**Output:** `[-1, 3, -1, 4, -1, -1, 9, 9]` (Nearest greater to left)

### 🔸 JavaScript Code:
```javascript
function monotonicDecreasing(nums) {
    let stack = [];
    let result = [];

    for (let num of nums) {
        while (stack.length && stack[stack.length - 1] < num) {
            stack.pop();
        }
        result.push(stack.length ? stack[stack.length - 1] : -1);
        stack.push(num);
    }

    return result;
}
```

### 🔸 Time & Space Complexity:
- **Time:** O(N)
- **Space:** O(N)

---

## ✅ Step-by-Step Approach (General):

1. Initialize an empty stack.
2. Loop through each element in the array:
   - While stack is not empty **AND** stack[top] breaks the desired condition:
     - Pop from the stack.
   - Push the current element.
3. Use the stack as needed (for result, comparisons, etc.)

---

## 🔁 Practice Problems (Must Know)

| Problem | Type |
|--------|------|
| 🔸 Next Greater Element | Monotonic Decreasing |
| 🔸 Next Smaller Element | Monotonic Increasing |
| 🔸 Nearest Smaller to Left | Monotonic Increasing |
| 🔸 Largest Rectangle in Histogram | Monotonic Stack |
| 🔸 Stock Span Problem | Monotonic Stack |
| 🔸 Maximum Area Rectangle in Binary Matrix | Monotonic Stack |
| 🔸 Redundant Brackets | Stack |
| 🔸 Sliding Window Maximum/Minimum | Monotonic Stack |
| 🔸 Expression Evaluation | Stack |
| 🔸 Lexicographically Largest Subsequence | Monotonic Stack |
| 🔸 Sum of Maximum in All Subarrays | Monotonic Stack |

---

## 📌 Applications of Monotonic Stack

- Next/Previous Greater or Smaller Element
- Histogram Problems (Largest Area)
- Binary Matrix Max Area
- Stock Span
- Sliding Window Minimum/Maximum
- Expression Parsing and Evaluation
- Balanced Brackets Check
- Tracking Max Element in Stack

---

## 👍 Advantages

- Very efficient: Mostly **O(N)** time.
- Used in many **competitive programming** and **interview problems**.
- Applicable in **stack-based parsing**.

---

## 👎 Disadvantages

- Requires **extra stack space**.
- Can be a bit **tricky for beginners** to understand at first.
