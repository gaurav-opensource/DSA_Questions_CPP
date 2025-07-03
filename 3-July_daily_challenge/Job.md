# 📘 Problem Statement: Minimum Difficulty of a Job Schedule

You are given an array `jobDifficulty[]` where `jobDifficulty[i]` is the difficulty of the `i-th` job. All jobs must be done in a dependent manner — meaning, to work on the `i-th` job, you must finish all jobs `j` where `0 <= j < i`.

You are also given an integer `d` representing the number of days you have to complete all the jobs.

You **must** schedule the jobs such that:
- You complete **at least one job per day**.
- You do not change the order of jobs.
- The difficulty of a day is the **maximum difficulty** among all jobs done on that day.

Your goal is to **minimize** the total difficulty of the schedule, which is the **sum of difficulties** across all days.

### ❗ Return:
- The **minimum total difficulty** of a valid job schedule.
- If it's **not possible** to create a valid schedule (i.e. number of jobs < `d`), return `-1`.

---

## 🧠 Problem Summary

Given:
- An integer array `jobDifficulty[]` of size `n`.
- An integer `d` (number of days to schedule).

### Constraints:
- Jobs are dependent (you must complete job `i-1` before job `i`).
- At least **one job per day** must be scheduled.

### Objective:
Partition the jobs into `d` parts such that:
- Each day has at least one job.
- The difficulty of the day is the **maximum** difficulty of jobs on that day.
- The **total difficulty** is **minimized**.

**Note:**  
If `n < d`, it's impossible to schedule. Return `-1`.

---

## ✅ Approach: Dynamic Programming

We use a DP table:
```cpp
dp[day][i] = Minimum total difficulty to schedule first (i+1) jobs in (day+1) days.

``` cpp

#include <bits/stdc++.h>
using namespace std;

int minDifficulty(vector<int>& jobDifficulty, int d) {
    int n = jobDifficulty.size();
    if (n < d) return -1;

    // dp[day][job]: min total difficulty to schedule first (job+1) jobs in (day+1) days
    vector<vector<int>> dp(d, vector<int>(n, INT_MAX));

    // Base case: first day
    int maxJob = 0;
    for (int j = 0; j < n; ++j) {
        maxJob = max(maxJob, jobDifficulty[j]);
        dp[0][j] = maxJob;
    }

    // Fill DP for days 2 to d
    for (int day = 1; day < d; ++day) {
        for (int j = day; j < n; ++j) {
            int maxDifficulty = 0;
            // Try all partitions ending at j
            for (int k = j; k >= day; --k) {
                maxDifficulty = max(maxDifficulty, jobDifficulty[k]);
                dp[day][j] = min(dp[day][j], dp[day-1][k-1] + maxDifficulty);
            }
        }
    }

    return dp[d-1][n-1];
}
