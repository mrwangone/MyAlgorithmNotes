# Difference array

| https://leetcode.com/problems/range-addition/description/ | Range addition |
| --- | --- |
| https://leetcode.com/problems/corporate-flight-bookings/description/ | flights |
| https://leetcode.com/problems/car-pooling/description/ | car pool capacity |

```cpp
给区间[l, r]中的每个数加上c：B[l] += c, B[r + 1] -= c

给以(x1, y1)为左上角，(x2, y2)为右下角的子矩阵中的所有元素加上c：
S[x1, y1] += c, S[x2 + 1, y1] -= c, S[x1, y2 + 1] -= c, S[x2 + 1, y2 + 1] += c
```

We can restore the original array using diff array in place

```cpp
for (int i = 1; i < length; ++i) {
    diff[i] += diff[i - 1];
}
```