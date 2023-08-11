# KMP

| https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/ | Strstr() |
| --- | --- |
| https://leetcode.com/problems/repeated-substring-pattern/description/ | Repeated Substring Pattern |
|  |  |
|  |  |

```cpp
vector<int> next(p.size(), 0);
next[0] = -1;
for (int i = 1, j = -1; i < p.size(); ++i) {
    while (j >= 0 && p[i] != p[j + 1]) j = next[j];
    if (p[i] == p[j + 1]) j++;
    next[i] = j;
}

for (int i = 0, j = -1; i < s.size(); ++i) {
    while (j >= 0 && s[i] != p[j + 1]) j = next[j];
    if (s[i] == p[j + 1]) j++;
    if (j == p.size() - 1) return i - p.size() + 1;
}
return -1;
```

### `next[i] = j` 含义

`p[1, j ] = p[i - j + 1, i]`