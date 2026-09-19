---
title: Lesson 10 - Trees
subject: Computer Science
unit: 10
competency: Traverse rooted trees and compute information over subtrees
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
> A tree is a connected graph with no cycles. Root it at a convenient node, then use parent-child structure to solve many problems with DFS or BFS.

---
## 1. Representation

For (n) vertices numbered `0` to `n-1`:

```cpp
vector<vector<int>> adj(n);
for (int i = 0; i < n - 1; i++) {
    int u, v;
    cin >> u >> v;
    --u; --v;                 // if input is 1-indexed
    adj[u].push_back(v);
    adj[v].push_back(u);
}
```

A tree with (n) vertices has exactly (n-1) edges.

---
## 2. DFS and Subtree Size

```cpp
vector<int> sub(n);

void dfs(int u, int parent) {
    sub[u] = 1;
    for (int v : adj[u]) {
        if (v == parent) continue;
        dfs(v, u);
        sub[u] += sub[v];
    }
}
```

After `dfs(root, -1)`, `sub[u]` is the number of vertices in the subtree of `u` under that chosen root.

---
## 3. BFS and Distances

```cpp
vector<int> dist(n, -1);
queue<int> q;
dist[source] = 0;
q.push(source);
while (!q.empty()) {
    int u = q.front(); q.pop();
    for (int v : adj[u]) if (dist[v] == -1) {
        dist[v] = dist[u] + 1;
        q.push(v);
    }
}
```

In an unweighted graph, BFS gives shortest path lengths in number of edges.

> [!TIP] Parent instead of visited
> In a tree DFS, passing `parent` prevents immediately walking back along the edge you arrived on. In a general graph, use a `visited` array too.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

How many edges does a tree with (n) vertices have? :: Exactly (n-1).

Why pass a parent argument in tree DFS? :: To avoid traversing back to the vertex from which DFS arrived.

What distances does BFS compute in an unweighted graph? :: Shortest distances measured by number of edges.
