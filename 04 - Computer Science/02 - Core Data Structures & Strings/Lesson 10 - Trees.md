---
title: Lesson 10 - Trees
subject: Computer Science
unit: 10
competency: Traverse rooted trees, compute subtree dynamics, and calculate tree diameter
tags:
  - Computer-Science
  - Competitive-Programming
  - Trees
  - DFS
  - BFS
  - Flashcards
---
---
# :LiBook: Lesson 10: Trees

> [!ABSTRACT] Scope
> A tree is a connected undirected graph with $N$ vertices and exactly $N-1$ edges (no cycles). Learn subtree properties, DFS/BFS traversals, and Tree Diameter computation.

---
## 1. Adjacency Representation

```cpp
#include <iostream>
#include <vector>
using namespace std;

int n;
vector<vector<int>> adj;

void readTree() {
    cin >> n;
    adj.assign(n, vector<int>());
    for (int i = 0; i < n - 1; i++) {
        int u, v;
        cin >> u >> v;
        u--; v--; // 0-based conversion
        adj[u].push_back(v);
        adj[v].push_back(u);
    }
}
```

---
## 2. Tree DFS & Subtree Calculation

In a tree, passing the `parent` pointer avoids needing a `visited` array.

```cpp
vector<int> subtree_size;

void dfs(int u, int parent) {
    subtree_size[u] = 1;
    for (int v : adj[u]) {
        if (v == parent) continue; // Prevent traversing back
        dfs(v, u);
        subtree_size[u] += subtree_size[v];
    }
}
```

---
## 3. Tree Diameter (2-DFS Algorithm)

The **Tree Diameter** is the longest simple path between any two vertices in a tree.

**2-DFS Algorithm**:
1. Run DFS from any arbitrary vertex (e.g. vertex `0`) to find the farthest vertex $A$.
2. Run DFS from vertex $A$ to find the farthest vertex $B$.
3. The path length between $A$ and $B$ is the Tree Diameter!

```cpp
pair<int, int> farthest_node; // {distance, node}

void dfsDiameter(int u, int parent, int current_dist) {
    if (current_dist > farthest_node.first) {
        farthest_node = {current_dist, u};
    }
    for (int v : adj[u]) {
        if (v != parent) {
            dfsDiameter(v, u, current_dist + 1);
        }
    }
}

int getTreeDiameter() {
    farthest_node = {-1, -1};
    dfsDiameter(0, -1, 0); // 1st DFS: find node A
    int nodeA = farthest_node.second;

    farthest_node = {-1, -1};
    dfsDiameter(nodeA, -1, 0); // 2nd DFS: find node B
    return farthest_node.first; // Diameter distance!
}
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

How many edges does a tree with $N$ vertices have? :: Exactly $N - 1$ edges.

Why is a `visited` array not strictly necessary during a Tree DFS? :: Because passing `parent` is sufficient to prevent walking back on the edge you arrived from (since trees have no cycles).

How do you find the diameter of an unweighted tree in $O(N)$ time using DFS? :: Run 1st DFS from any node to find the farthest node $A$, then run 2nd DFS from $A$ to find the farthest node $B$. The distance between $A$ and $B$ is the diameter.
