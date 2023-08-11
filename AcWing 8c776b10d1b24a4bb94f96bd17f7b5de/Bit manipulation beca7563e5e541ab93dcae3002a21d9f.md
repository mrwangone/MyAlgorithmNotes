# Bit manipulation

| https://leetcode.com/problems/number-of-1-bits/description/ | Number of 1 bits |
| --- | --- |
| https://leetcode.com/problems/power-of-two/ | Is pow of 2 |
| https://leetcode.com/problems/single-number/ | Single number |
| https://leetcode.com/problems/missing-number/ | Missing number |

### n的二进制中第k位 `n >> k & 1`

1. 先把k移到最后一位 `n >> k`
2. 看个位 `x & 1`

### `lowbit(x)` 返回x的最后一位1: `x&-x`

`-x == ~x + 1`

求1的个数:

`while (x) x -= lowbit(x), result++`

### **消除数字 `n` 的二进制表示中的最后一个 1 `n & (n-1)`**

### 判断异号

`x ^ y < 0` 异号

### xor: `a ^ b`