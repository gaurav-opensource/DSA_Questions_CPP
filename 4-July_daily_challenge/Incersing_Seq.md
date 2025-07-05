# 🔍 Find Length of Longest Continuous Increasing Subsequence (LCIS)

## 📌 Problem Statement

Given an integer array `nums`, return the **length of the longest continuous increasing subsequence** (LCIS).

A **continuous increasing subsequence** is a subarray (not necessarily the whole array) where each element is strictly greater than the one before, and all elements are **contiguous**.

---

## 🧪 Example

### Input:


### Explanation:
- The increasing subarrays are: `[1, 3, 5]`, `[4, 7]`
- The longest one is `[1, 3, 5]` → length = **3**

---

## 🧠 Logic

We scan the array from left to right and:
- Track current length of increasing sequence (`currLen`)
- Reset `currLen` to 1 when the sequence breaks
- Update `maxLen` each time we find a longer sequence

---

## 🔁 Pseudocode


function findLengthOfLCIS(nums):
    if nums is empty:
        return 0

    currLen = 1
    maxLen = 1

    for i from 1 to nums.length - 1:
        if nums[i] > nums[i-1]:
            currLen += 1
            maxLen = max(maxLen, currLen)
        else:
            currLen = 1  // reset if not increasing

    return maxLen

```cpp
class Solution {
public:
    int findLengthOfLCIS(vector<int>& nums) {
        if (nums.empty()) return 0;

        int maxLen = 1;
        int currLen = 1;

        for (int i = 1; i < nums.size(); i++) {
            if (nums[i] > nums[i - 1]) {
                currLen++;
                maxLen = max(maxLen, currLen);
            } else {
                currLen = 1;  // reset if sequence breaks
            }
        }

        return maxLen;
    }
};
