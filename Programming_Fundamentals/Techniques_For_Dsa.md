
# 🔢 Sorting Techniques in C++ (DSA Focus)

## 🔹 Sorting 1D Array / Vector
```cpp
#include <algorithm>
#include <vector>
using namespace std;

vector<int> v = {4, 2, 9, 1};

// Ascending sort
sort(v.begin(), v.end());

// Descending sort
sort(v.begin(), v.end(), greater<int>());
```

---

## 🔹 Sorting Strings (Alphabetical)
```cpp
#include <algorithm>
#include <string>
using namespace std;

string s = "dcbagf";

// Ascending
sort(s.begin(), s.end()); // "abcdfg"

// Descending
sort(s.rbegin(), s.rend()); // "gfdcba"
```

---

## 🔹 Sort Vector of Pairs by First Element
```cpp
#include <algorithm>
#include <vector>
using namespace std;

vector<pair<int, int>> vp = {{3, 5}, {1, 7}, {2, 6}};

// Sort by first element
sort(vp.begin(), vp.end());
```

---

## 🔹 Sort Vector of Pairs by Second Element
```cpp
sort(vp.begin(), vp.end(), [](pair<int,int> a, pair<int,int> b){
    return a.second < b.second;
});
```

---

## 🔹 Sort 2D Vector by First Column
```cpp
vector<vector<int>> mat = {{3, 2}, {1, 5}, {2, 4}};

sort(mat.begin(), mat.end(), [](vector<int> &a, vector<int> &b){
    return a[0] < b[0];
});
```

---

## 🔹 Sort 2D Vector by Second Column Descending
```cpp
sort(mat.begin(), mat.end(), [](vector<int> &a, vector<int> &b){
    return a[1] > b[1];
});
```

---

## 🔹 Sort Strings by Length
```cpp
vector<string> vs = {"a", "abc", "ab"};

sort(vs.begin(), vs.end(), [](string &a, string &b){
    return a.length() < b.length();
});
```

---

## 🔹 Sort Vector of Structs by Custom Field
```cpp
struct Student {
    string name;
    int marks;
};

vector<Student> st = {{"Amit", 90}, {"Rita", 80}};

sort(st.begin(), st.end(), [](Student &a, Student &b){
    return a.marks > b.marks;
});
```

---

## 🔹 Stable Sort and Partial Sort
```cpp
// Stable Sort
stable_sort(v.begin(), v.end());

// Partial Sort (first k smallest elements)
partial_sort(v.begin(), v.begin() + k, v.end());
```

---

> ✅ Now your notes contain all **core data structures** and **sorting techniques** used in DSA with clean examples.
> You can now start practicing problems using these!
