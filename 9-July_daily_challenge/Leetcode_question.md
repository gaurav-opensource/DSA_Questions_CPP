# 🧠 Maximize Free Time During Event

## 📌 Problem Statement

You are given:

- An integer `eventTime` — total time duration of an event (from `t = 0` to `t = eventTime`).
- Two integer arrays:
  - `startTime[i]` — start time of the i-th meeting.
  - `endTime[i]` — end time of the i-th meeting.

Each meeting:
- Is non-overlapping.
- Occurs in given order.
- Lies entirely within the event time.

### 🔄 Operation Allowed

You are allowed to **reschedule at most `k` meetings** by shifting their **start times** only.

Rules:
- Duration of each meeting must remain unchanged.
- Order of meetings must not change.
- Rescheduled meetings must not overlap.
- Meetings must remain within `[0, eventTime]`.

---

## 🎯 Goal

Rearrange at most `k` meetings to **maximize the longest continuous period of free time** during the event.

---

## ✅ Approach Explanation

### 🔸 Step 1: Understand the Problem

- The day consists of **meetings** and **free time**.
- Free time can be:
  - Before the first meeting.
  - Between meetings.
  - After the last meeting.

Your goal is to **reschedule up to `k` meetings** to combine free time and **maximize the longest continuous stretch** without any meeting.

---

### 🔸 Step 2: Model Free Time

Define a `freeArray[]`:
- `freeArray[0]` = gap from `t = 0` to `startTime[0]`
- `freeArray[i]` = gap between `endTime[i-1]` and `startTime[i]`
- `freeArray[n]` = gap from `endTime[n-1]` to `eventTime`

📌 **Example**

Given:
- Meetings: `[2–4], [5–7], [9–10], [13–15]`
- `eventTime = 20`

Free gaps:
- `[0–2], [4–5], [7–9], [10–13], [15–20]`

So:
```text
freeArray = [2, 1, 2, 3, 5]

``` cpp
function maxFreeTime(eventTime, k, startTime, endTime):
    freeArray = []
    freeArray.append(startTime[0])  // gap before first meeting

    for i from 1 to startTime.length:
        gap = startTime[i] - endTime[i - 1]
        freeArray.append(gap)

    freeArray.append(eventTime - endTime[-1])  // gap after last meeting

    maxSum = 0
    currSum = 0
    i = 0

    for j from 0 to freeArray.length:
        currSum += freeArray[j]

        if window size > k+1:
            currSum -= freeArray[i]
            i += 1

        if window size == k+1:
            maxSum = max(maxSum, currSum)

    return maxSum

```cpp
class Solution {
public:
    int maxFreeTime(int eventTime, int k, vector<int>& startTime, vector<int>& endTime) {
        vector<int> freeArray;

        // Gap before the first meeting
        freeArray.push_back(startTime[0]);

        // Gaps between meetings
        for (int i = 1; i < startTime.size(); i++) {
            freeArray.push_back(startTime[i] - endTime[i - 1]);
        }

        // Gap after the last meeting
        freeArray.push_back(eventTime - endTime.back());

        // Sliding window of size k+1
        int maxSum = 0, currSum = 0, i = 0;
        int n = freeArray.size();

        for (int j = 0; j < n; j++) {
            currSum += freeArray[j];

            if (j - i + 1 > k + 1) {
                currSum -= freeArray[i];
                i++;
            }

            if (j - i + 1 == k + 1) {
                maxSum = max(maxSum, currSum);
            }
        }

        return maxSum;
    }
};
``` cpp
