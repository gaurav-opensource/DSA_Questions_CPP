# Create markdown content for Different Ways to Add Parentheses

diff_ways_md = """
# 🧮 Different Ways to Add Parentheses

---

## ✅ Question:

**Problem Statement:**  
You are given a string `expression` of numbers and operators.  
Return **all possible results** from computing **all the different possible ways to group numbers and operators** using parentheses.  
You may return the answer in any order.

> The test cases are such that output values fit in a 32-bit integer and do not exceed 10^4 results.

---

## 🧪 Examples:

### Example 1:












---

## 🧠 Approach:

We use **recursion** and **divide and conquer**:

1. For each operator in the expression, we:
    - Split into left and right subexpressions.
    - Recursively compute possible results for each part.
2. Combine each pair of results using the operator.
3. If no operator is found, the string is a number → base case.

---

## 💻 Pseudocode:

```cpp
function diffWaysToCompute(expression):
    if expression is just a number:
        return [number]

    results = []

    for each character in expression:
        if it is an operator:
            leftResults = diffWaysToCompute(left substring)
            rightResults = diffWaysToCompute(right substring)

            for each l in leftResults:
                for each r in rightResults:
                    combine l and r using operator
                    add to results

    return results




```cpp

class Solution {
public:
    void countThePair(vector<int>& result, string exp) {
        bool isNumber = true;
        for (char ch : exp) {
            if (ch == '+' || ch == '-' || ch == '*') {
                isNumber = false;
                break;
            }
        }

        if (isNumber) {
            result.push_back(stoi(exp));
            return;
        }

        for (int i = 0; i < exp.length(); ++i) {
            char ch = exp[i];
            if (ch == '+' || ch == '-' || ch == '*') {
                string left = exp.substr(0, i);
                string right = exp.substr(i + 1);

                vector<int> leftResult;
                vector<int> rightResult;

                countThePair(leftResult, left);
                countThePair(rightResult, right);

                for (int l : leftResult) {
                    for (int r : rightResult) {
                        int ans = 0;
                        if (ch == '+') ans = l + r;
                        else if (ch == '-') ans = l - r;
                        else if (ch == '*') ans = l * r;

                        result.push_back(ans);
                    }
                }
            }
        }
    }

    vector<int> diffWaysToCompute(string expression) {
        vector<int> result;
        countThePair(result, expression);
        return result;
    }
};
