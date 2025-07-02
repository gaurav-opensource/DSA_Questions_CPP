# 🧮 countGoodNumbers - C++ Solution with Explanation

## 📌 Problem Statement

You're given a number `n`, which represents the number of digits in a **"good number"**.

A number is **good** if:
- At **even indices (0-based)** → you can use any of `{0, 2, 4, 6, 8}` → **5 choices**
- At **odd indices** → you can use any of the prime digits `{2, 3, 5, 7}` → **4 choices**

---

## 📝 Goal

Count the **total number of good numbers** of length `n`, **modulo** \(10^9 + 7\).

---

## 🧠 Key Concepts

Let:

- `evenN = (n + 1) / 2` → number of even-position digits
- `oddN = n / 2` → number of odd-position digits

### Formula:

\[
\text{Total Good Numbers} = (5^{evenN} \times 4^{oddN}) \mod (10^9 + 7)
\]

---

## 💡 Why `long long`?

In C++, `int` has a range of approximately ±2 × 10⁹.  
But powers like \(5^{10^9}\) become **extremely large**, leading to **integer overflow**.

### ❌ Example of Overflow with `int`:
```cpp
int a = 100000;
int b = 100000;
int result = a * b; // Overflow


function countGoodNumbers(n):
    evenN = (n + 1) / 2
    oddN = n / 2

    result = (power(5, evenN) * power(4, oddN)) % MOD
    return result

function power(a, b):
    if b == 0: return 1

    half = power(a, b/2)
    result = (half * half) % MOD

    if b is odd:
        result = (result * a) % MOD

    return result

```cpp
class Solution {
public:
    const int m = 1e9 + 7;  // Modulo value

    // Modular Exponentiation Function
    long long findPower(long long a, long long b) {
        if (b == 0) return 1;

        long long half = findPower(a, b / 2);
        long long result = (half * half) % m;

        if (b % 2 == 1) {
            result = (result * a) % m;
        }

        return result;
    }

    int countGoodNumbers(long long n) {
        long long evenN = (n + 1) / 2;
        long long oddN = n / 2;

        long long evenWays = findPower(5, evenN);
        long long oddWays = findPower(4, oddN);

        return (evenWays * oddWays) % m;
    }
};






# 🔢 Implement pow(x, n) using Recursion and Binary Exponentiation

## 📌 Problem Statement

Implement a function `pow(x, n)` that calculates `x` raised to the power `n`, i.e.,  
\[
x^n
\]

- If `n < 0`: compute using \( \frac{1}{x^{-n}} \)
- Use efficient **recursive binary exponentiation**

---

## 🔁 Recursive Power – Logic

### Handle 3 cases:

1. **Base Case:**  
   If `n == 0`, return `1`.

2. **Negative Power:**  
   If `n < 0`, convert to:  
   \[
   \text{pow}(x, n) = \text{pow}\left(\frac{1}{x}, -n\right)
   \]

3. **Binary Exponentiation:**

   - If `n` is **even**:  
     \[
     \text{pow}(x, n) = \text{pow}(x \times x, n / 2)
     \]

   - If `n` is **odd**:  
     \[
     \text{pow}(x, n) = x \times \text{pow}(x \times x, n / 2)
     \]

---

## ✅ C++ Code – Recursive Implementation

```cpp
class Solution {
public:
    double myPow(double x, int n) {
        // Convert n to long long to avoid overflow on INT_MIN
        long long power = n;

        if (power < 0) {
            x = 1 / x;
            power = -power;
        }

        return powerRecursive(x, power);
    }

private:
    // Recursive function using binary exponentiation
    double powerRecursive(double x, long long n) {
        if (n == 0) return 1;

        // If n is even: x^n = (x * x)^(n/2)
        if (n % 2 == 0) {
            return powerRecursive(x * x, n / 2);
        } 
        // If n is odd: x^n = x * (x * x)^(n/2)
        else {
            return x * powerRecursive(x * x, n / 2);
        }
    }
};
