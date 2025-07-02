# 📘 DSA C++ Basics – Core Data Structures

A comprehensive list of basic data structures and their implementations in C++.

---

## 🧮 Array Representation
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {1, 2, 3, 4, 5};  // Static array
    cout << arr[0]; // Access element
}
```

---

## 📦 Vector (Dynamic Array)
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v;
    v.push_back(10);
    v.push_back(20);
    cout << v[1]; // 20
}
```

---

## 🔗 Linked List
```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;

    Node(int val) {
        data = val;
        next = NULL;
    }
};

int main() {
    Node* head = new Node(1);
    head->next = new Node(2);
    cout << head->next->data; // 2
}
```

---

## 📚 Stack
```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<int> st;
    st.push(10);
    st.push(20);
    st.pop();         // Removes 20
    cout << st.top(); // 10
}
```

---

## ⏳ Queue
```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<int> q;
    q.push(1);
    q.push(2);
    q.pop();         // Removes 1
    cout << q.front(); // 2
}
```

---

## 🌀 Deque
```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<int> dq;
    dq.push_back(1);
    dq.push_front(2);
    dq.pop_back();
    cout << dq.front(); // 2
}
```

---

## 🔁 Set
```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    set<int> s;
    s.insert(10);
    s.insert(20);
    cout << *s.begin(); // 10
}
```

---

## 🗂 Map (Key-Value Pairs)
```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<string, int> mp;
    mp["apple"] = 2;
    mp["banana"] = 3;
    cout << mp["banana"]; // 3
}
```

---

## 🧭 Unordered Map
```cpp
#include <iostream>
#include <unordered_map>
using namespace std;

int main() {
    unordered_map<string, int> ump;
    ump["a"] = 10;
    cout << ump["a"]; // 10
}
```

---

## 🔼 Priority Queue (Max-Heap)
```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    priority_queue<int> pq;
    pq.push(10);
    pq.push(5);
    cout << pq.top(); // 10 (largest)
}
```

---

## 🌐 Graph (Adjacency List)
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int V = 5;
    vector<vector<int>> adj(V);

    adj[0].push_back(1);
    adj[1].push_back(2);

    // Print neighbors of node 1
    for(int v : adj[1])
        cout << v << " "; // 2
}
```

---

## 🌳 Binary Tree
```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;

    TreeNode(int x) {
        val = x;
        left = right = NULL;
    }
};

int main() {
    TreeNode* root = new TreeNode(1);
    root->left = new TreeNode(2);
    root->right = new TreeNode(3);
    cout << root->left->val; // 2
}
```

---

> ✅ Save this file to your GitHub repository as `README.md` under a folder like `CPP-DSA-Basics`.

Let me know if you want the GitHub upload steps too!