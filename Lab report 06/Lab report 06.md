# Lab 06: Graph Algorithms – BFS and DFS Traversals

## I. Learning Objectives
- Understand graph representation (adjacency list).
- Implement Breadth-First Search (BFS).
- Implement Depth-First Search (DFS).
- Analyze time and space complexities.

---

## Experiment 1: Breadth-First Search (BFS)

### Algorithm Complexity
- Time Complexity: O(V + E)
- Space Complexity: O(V)

---

### Source Code (C++)
```cpp
// Breath-First Search (BFS)
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

void BFS(int start, vector<vector<int>> &adj, vector<bool> &visited) {
    queue<int> q;
    q.push(start);
    visited[start] = true;

    while (!q.empty()) {
        int u = q.front();
        q.pop();
        cout << u << " ";

        for (int v : adj[u]) {
            if (!visited[v]) {
                visited[v] = true;
                q.push(v);
            }
        }
    }
}

int main() {
    int V, E;
    cout << "Enter number of vertices and edges: ";
    cin >> V >> E;

    vector<vector<int>> adj(V);

    cout << "Enter edges (u v):" << endl;
    for (int i = 0; i < E; i++) {
        int u, v;
        cin >> u >> v;
        adj[u].push_back(v);
        adj[v].push_back(u); // Undirected graph
    }

    vector<bool> visited(V, false);
    cout << "BFS traversal starting from node 0: ";
    BFS(0, adj, visited);
    cout << endl;

    return 0;
}
```
### Sample Output

![Breath-First Search (BFS) Output](https://github.com/SHUVO-05/CSE-2202-Algorithm-Design-and-Analysis-Sessional/blob/main/Lab%20report%2006/Breath-First%20Search.png)


# Experiment 2: Depth-First Search (DFS)

## Algorithm Complexity
- Time Complexity: O(V + E)
- Space Complexity: O(V)

---

## Source Code (C++)
```cpp
// Depth-First Search (DFS)
#include <iostream>
#include <vector>
using namespace std;

void DFS(int u, vector<vector<int>> &adj, vector<bool> &visited) {
    visited[u] = true;
    cout << u << " ";

    for (int v : adj[u]) {
        if (!visited[v]) {
            DFS(v, adj, visited);
        }
    }
}

int main() {
    int V, E;
    cout << "Enter number of vertices and edges: ";
    cin >> V >> E;

    vector<vector<int>> adj(V);

    cout << "Enter edges (u v):" << endl;
    for (int i = 0; i < E; i++) {
        int u, v;
        cin >> u >> v;
        adj[u].push_back(v);
        adj[v].push_back(u); // Undirected graph
    }

    vector<bool> visited(V, false);
    cout << "DFS traversal starting from node 0: ";
    DFS(0, adj, visited);
    cout << endl;

    return 0;
}
```
### Sample Output

![Depth-First Search (DFS) Output](https://github.com/SHUVO-05/CSE-2202-Algorithm-Design-and-Analysis-Sessional/blob/main/Lab%20report%2006/Depth-First%20Search.png)
## Summary Table

| Lab | Algorithm(s)                   | Time Complexity  | Space Complexity |
|-----|-------------------------------|------------------|------------------|
| 04  | Greedy Coin Change             | O(n)             | O(1)             |
| 05  | Fibonacci (Memo), 0/1 Knapsack | O(n), O(nW)      | O(n), O(nW)      |
| 06  | BFS, DFS                      | O(V + E)         | O(V)             |
