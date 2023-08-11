# Dijkstra

| https://leetcode.com/problems/network-delay-time/ | Dijkstra%204b5250fcc93d4affaef02447340e8c0f/Dijkstra%20-%20Leetcode%201938cfc08178462099376843677ddc45.md |
| --- | --- |
| https://leetcode.com/problems/path-with-minimum-effort/description/ | Path With Minimum Effort |
| Leetcode 1514 | Dijkstra%204b5250fcc93d4affaef02447340e8c0f/Dijkstra%20-%20Leetcode%201938cfc08178462099376843677ddc45.md |

[Dijkstra - Leetcode](Dijkstra%204b5250fcc93d4affaef02447340e8c0f/Dijkstra%20-%20Leetcode%201938cfc08178462099376843677ddc45.md)

```cpp
	dist[k] = 0;
  priority_queue<PII, vector<PII>, greater<PII>> pq;
  pq.push({0, k});

  while (!pq.empty()) {
      auto top = pq.top();
      pq.pop();
      int u = top.second;
    
      if (visited[u]) continue;
      visited[u] = true;

      for (auto& neighbor : graph[u]) {
          int v = neighbor.first;
          int w = neighbor.second;
          if (dist[v] > dist[u] + w) {
              dist[v] = dist[u] + w;
              pq.push({dist[v], v});
          }
      }
  }
```