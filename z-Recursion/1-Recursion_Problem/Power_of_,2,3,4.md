# Creating the markdown content as a file to be downloaded

md_content = """
# 🔢 Power Checks – Efficient Algorithms

This document includes optimized approaches and pseudocode for checking:
1. Power of 2
2. Power of 3
3. Power of 4

---

## ✅ Question 1: Power of 2

**🧾 Problem Statement:**  
Determine whether a given integer `n` is a power of two.

A number is a power of two if it can be written as \( 2^x \) where x is a non-negative integer.

**🧪 Example Inputs:**
- Input: `1` → Output: `true` (2^0)
- Input: `16` → Output: `true` (2^4)
- Input: `18` → Output: `false`

---

### 🧠 Approach:

- A number is a power of 2 if:
  - It is greater than 0
  - It has exactly **one bit set** in binary (e.g., 2 → 10, 4 → 100)
- This is checked using:  
  \[
  (n > 0) \land (n \& (n - 1)) == 0
  \]

---

### 💻 Pseudocode:

```cpp
bool isPowerOfTwo(int n) {
    return n > 0 && (n & (n - 1)) == 0;
}


# Creating the markdown content as a file to be downloaded

md_content = """
# 🔢 Power Checks – Efficient Algorithms

This document includes optimized approaches and pseudocode for checking:
1. Power of 2
2. Power of 3
3. Power of 4

---

## ✅ Question 1: Power of 2

**🧾 Problem Statement:**  
Determine whether a given integer `n` is a power of two.

A number is a power of two if it can be written as \( 2^x \) where x is a non-negative integer.

**🧪 Example Inputs:**
- Input: `1` → Output: `true` (2^0)
- Input: `16` → Output: `true` (2^4)
- Input: `18` → Output: `false`

---

### 🧠 Approach:

- A number is a power of 2 if:
  - It is greater than 0
  - It has exactly **one bit set** in binary (e.g., 2 → 10, 4 → 100)
- This is checked using:  
  \[
  (n > 0) \land (n \& (n - 1)) == 0
  \]

---

### 💻 Pseudocode:

```cpp
bool isPowerOfTwo(int n) {
    return n > 0 && (n & (n - 1)) == 0;
}



# Creating a markdown file with only the Power of 4 question

power_of_4_md = """
# 🔢 Power Check – Power of 4

---

## ✅ Question: Power of 4

**🧾 Problem Statement:**  
Determine whether a given integer `n` is a power of four.

A number is a power of four if it can be written as \( 4^x \) where x is a non-negative integer.

---

### 🧪 Example Inputs:
- Input: `16` → Output: `true` (4^2)
- Input: `8` → Output: `false` (Power of 2 but not 4)
- Input: `64` → Output: `true` (4^3)

---

## 🧠 Approach:

A number is a power of 4 if:
1. It is greater than 0.
2. It is a power of 2 → `(n & (n - 1)) == 0`
3. Its single set bit is at an even position.

To check the even-position bit, use the bitmask `0x55555555`:



This mask has 1s at all even positions (0-based indexing).

---

## 💻 Pseudocode:

```cpp
bool isPowerOfFour(int n) {
    return n > 0 &&
           (n & (n - 1)) == 0 &&      // Check power of 2
           (n & 0x55555555) != 0;     // Check even bit position
}
