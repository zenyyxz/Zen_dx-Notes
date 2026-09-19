---
title: Lesson 11 - Graph Algorithms
subject: Computer Science
unit: 11
competency: Choose foundational graph algorithms based on edge weights and graph structure
tags:
  - Computer-Science
  - Competitive-Programming
  - Graphs
  - Dijkstra
  - DSU
  - Flashcards
---
---
# :LiBook: Lesson 11: Graph Algorithms

> [!ABSTRACT] Scope
> Graph problems are about vertices and relationships. First identify: directed or undirected, weighted or unweighted, and whether negative weights exist.

---
## 1. Algorithm Choice

| Situation | Typical tool |
| :--- | :--- |
| unweighted shortest paths | BFS |
| non-negative weighted shortest paths | Dijkstra |
| connected components / cycle checks | DFS, BFS, or DSU |
| build a minimum spanning tree | Kruskal or Prim |
| prerequisites in a directed acyclic graph | topological sort |

---
## 2. Dijkstra's Algorithm

Dijkstra works only if all edge weights are non-negative.

```cpp
using P = pair<long long, int>;
priority_queue<P, vector<P>, greater<P>> pq;
vector<long long> dist(n, LLONG_MAX);
dist[source] = 0;
pq.push({0, source});

while (!pq.empty()) {
    auto [d, u] = pq.top(); pq.pop();
    if (d != dist[u]) continue; // stale heap entry
    for (auto [v, w] : adj[u]) {
        if (dist[v] > d + w) {
            dist[v] = d + w;
            pq.push({dist[v], v});
        }
    }
}
```

---
## 3. Disjoint Set Union (DSU)

DSU maintains components while edges are added.

```cpp
struct DSU {
    vector<int> p, sz;
    DSU(int n) : p(n), sz(n, 1) { iota(p.begin(), p.end(), 0); }
    int find(int x) { return p[x] == x ? x : p[x] = find(p[x]); }
    bool unite(int a, int b) {
        a = find(a); b = find(b);
        if (a == b) return false;
        if (sz[a] < sz[b]) swap(a, b);
        p[b] = a; sz[a] += sz[b];
        return true;
    }
};
```

`unite(a,b)` returns false exactly when adding that edge would create a cycle inside an existing component.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

When is Dijkstra's algorithm valid? :: When all edge weights are non-negative.

What does DSU efficiently maintain? :: Which vertices belong to the same connected component as edges are added.

What does a stale priority-queue entry in Dijkstra mean? :: A shorter distance to that vertex was found after the entry was pushed, so the entry should be skipped.
