---
title: Lesson 11 - Graph Algorithms
subject: Computer Science
unit: 11
competency: Implement BFS, Dijkstra, DSU, Kruskal's MST, and Topological Sort
tags:
  - Computer-Science
  - Competitive-Programming
  - Graphs
  - Dijkstra
  - DSU
  - TopologicalSort
  - Flashcards
---
---
# :LiBook: Lesson 11: Graph Algorithms

> [!ABSTRACT] Scope
> Master foundational graph algorithms: BFS, Dijkstra's Shortest Path, Disjoint Set Union (DSU), Kruskal's MST, and Kahn's Topological Sort.

---
## 1. Dijkstra's Algorithm (Non-Negative Weighted Graphs)

Find shortest distance from source to all vertices in $O((V + E) \log V)$ time.

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

const long long INF = 1e18;

vector<long long> dijkstra(int n, int src, const vector<vector<pair<int, int>>>& adj) {
    vector<long long> dist(n, INF);
    // Min-Heap priority queue storing {distance, vertex}
    priority_queue<pair<long long, int>, vector<pair<long long, int>>, greater<pair<long long, int>>> pq;

    dist[src] = 0;
    pq.push({0, src});

    while (!pq.empty()) {
        auto [d, u] = pq.top(); pq.pop();
        if (d > dist[u]) continue; // Skip stale heap entry

        for (auto [v, weight] : adj[u]) {
            if (dist[u] + weight < dist[v]) {
                dist[v] = dist[u] + weight;
                pq.push({dist[v], v});
            }
        }
    }
    return dist;
}
```

---
## 2. Disjoint Set Union (DSU) & Kruskal's MST

```cpp
struct DSU {
    vector<int> parent, sz;
    DSU(int n) : parent(n), sz(n, 1) {
        for (int i = 0; i < n; i++) parent[i] = i;
    }

    int find(int i) {
        if (parent[i] == i) return i;
        return parent[i] = find(parent[i]); // Path compression
    }

    bool unite(int i, int j) {
        int root_i = find(i), root_j = find(j);
        if (root_i != root_j) {
            if (sz[root_i] < sz[root_j]) swap(root_i, root_j);
            parent[root_j] = root_i;
            sz[root_i] += sz[root_j];
            return true;
        }
        return false;
    }
};

struct Edge {
    int u, v, w;
    bool operator<(const Edge& other) const { return w < other.w; }
};

long long kruskalMST(int n, vector<Edge>& edges) {
    sort(edges.begin(), edges.end());
    DSU dsu(n);
    long long mst_cost = 0;
    int edges_count = 0;

    for (const auto& e : edges) {
        if (dsu.unite(e.u, e.v)) {
            mst_cost += e.w;
            edges_count++;
        }
    }
    return (edges_count == n - 1) ? mst_cost : -1;
}
```

---
## 3. Topological Sort (Kahn's BFS Algorithm)

Sort vertices in a Directed Acyclic Graph (DAG) such that for every directed edge $u \to v$, $u$ comes before $v$.

```cpp
vector<int> topoSort(int n, const vector<vector<int>>& adj, vector<int>& indegree) {
    queue<int> q;
    for (int i = 0; i < n; i++) {
        if (indegree[i] == 0) q.push(i);
    }

    vector<int> topo_order;
    while (!q.empty()) {
        int u = q.front(); q.pop();
        topo_order.push_back(u);

        for (int v : adj[u]) {
            indegree[v]--;
            if (indegree[v] == 0) q.push(v);
        }
    }
    return (topo_order.size() == n) ? topo_order : vector<int>(); // Empty if graph has cycle!
}
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

When is Dijkstra's algorithm valid? :: When all edge weights in the graph are non-negative.

What does Kahn's algorithm use to perform Topological Sorting? :: A queue tracking vertices with an indegree of 0.

What is the time complexity of Kruskal's Minimum Spanning Tree algorithm? :: $O(E \log E)$ time for sorting edges.
