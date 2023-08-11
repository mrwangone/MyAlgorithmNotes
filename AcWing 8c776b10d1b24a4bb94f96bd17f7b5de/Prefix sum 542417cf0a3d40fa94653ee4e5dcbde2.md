# Prefix sum

| https://leetcode.com/problems/range-sum-query-immutable/ | 1d Prefix sum |
| --- | --- |
| https://leetcode.com/problems/range-sum-query-2d-immutable/ | 2d Prefix sum |
|  |  |

### Prefix

```cpp
S[i] = a[1] + a[2] + ... a[i]
a[l] + ... + a[r] = S[r] - S[l - 1]

S[i, j] = 第i行j列格子左上部分所有元素的和
以(x1, y1)为左上角，(x2, y2)为右下角的子矩阵的和为：
S[x2, y2] - S[x1 - 1, y2] - S[x2, y1 - 1] + S[x1 - 1, y1 - 1]
```