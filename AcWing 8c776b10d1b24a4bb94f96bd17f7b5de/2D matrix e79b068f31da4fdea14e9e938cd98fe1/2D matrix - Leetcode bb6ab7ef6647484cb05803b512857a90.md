# 2D matrix - Leetcode

### Rotate image

技巧：沿对角线对折再反转行

```cpp
void rotate(vector<vector<int>>& matrix) {
    for (int i = 0; i < matrix.size(); ++i) {
        for (int j = 0; j < i; ++j) {
            swap(matrix[i][j], matrix[j][i]);
        }
    }
    for (auto& row : matrix) {
        reverse(row.begin(), row.end());
    }
}
```

### Sprial Matrix

使用方向向量，有点类似bfs的感觉，沿着方向向量走，走不通了之后变换方向向量继续

```cpp
vector<int> spiralOrder(vector<vector<int>>& matrix) {
    int m = matrix.size();
    int n = matrix[0].size();
    int dx[] = {0, 1, 0, -1};
    int dy[] = {1, 0, -1, 0};
    vector<int> res;
    vector<vector<bool>> visited(m, vector<bool>(n, false));

    for (int i = 0, x = 0, y = 0, d = 0; i < m * n; ++i) {
        res.push_back(matrix[x][y]);
        visited[x][y] = true;

        int a = x + dx[d], b = y + dy[d];
        if (a < 0 || a >= m || b < 0 || b >=n || visited[a][b]) {
            d = (d + 1) % 4;
            a = x + dx[d], b = y + dy[d];
        }
        x = a, y = b;
    }
    return res;
}
```