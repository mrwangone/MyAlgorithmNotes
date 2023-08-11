# Knapsack Problem

| https://leetcode.com/problems/coin-change/description/ | Coin Change | 完全背包 |
| --- | --- | --- |
| https://leetcode.com/problems/coin-change-ii/description/ | Coin Change II  | 完全背包 |
| https://leetcode.com/problems/climbing-stairs/description/ | Climbing Stairs | 完全背包 |
| https://leetcode.com/problems/perfect-squares/description/ | Perfect Squares | 完全背包 |
| https://leetcode.com/problems/combination-sum-iv/description/ | Combination Sum IV |  |
| https://leetcode.com/problems/word-break/description/ | Word Break |  |
| https://leetcode.com/problems/partition-equal-subset-sum/description/ | Partition Equal Subset Sum | 0/1背包 |
| https://leetcode.com/problems/target-sum/description/ | Target Sum | 0/1背包 |
| https://leetcode.com/problems/ones-and-zeroes/ | Ones and Zeroes | 0/1背包 |
| https://leetcode.com/problems/profitable-schemes/description/ | Profitable Schemes | 0/1背包变型 |
| https://leetcode.com/problems/last-stone-weight-ii/description/ | Last Stone Weight II | 0/1背包 |
- 0/1背包
- 完全背包
- 多重背包
- 分组背包

![Untitled](Knapsack%20Problem%20f3ea6bc787a342629b289dcce2fd1cba/Untitled.png)

[Knapsack - Leetcode](Knapsack%20Problem%20f3ea6bc787a342629b289dcce2fd1cba/Knapsack%20-%20Leetcode%200f24a92b0e4a4b33b609dd77717e25c3.md)

## 0/1背包问题

```cpp
// 朴素做法
for (int i = 1; i <= n; i++) {
      for (int j = 1; j <= m; j++) {
          f[i][j] = f[i - 1][j];
          if (j >= v[i]) f[i][j] = max(f[i][j], f[i - 1][j - v[i]] + w[i]);
      }
  }
```

### 滚动数组优化

```cpp
// 先写出二维的，然后降维，从代码中删除一维
for (int i = 1; i <= n; i ++ )
		// 从大到小， 因为j - v[i] < j, 如果从小到大， 
		// j -v[i]已经是更新后的i层的值了
    for (int j = m; j >= v[i]; j -- )
        f[j] = max(f[j], f[j - v[i]] + w[i]);
```

## 完全背包

```cpp
for(int i = 1 ; i<= n ;i++)
  for(int j = 0 ; j<= m ;j++)
  {
      for(int k = 0 ; k * v[i] <= j ; k++)
          f[i][j] = max(f[i][j], f[i - 1][j - k * v[i]] + k * w[i]);
  }
```

### 优化

![Untitled](Knapsack%20Problem%20f3ea6bc787a342629b289dcce2fd1cba/Untitled%201.png)

```cpp
for(int i = 1; i <= n; i ++ ) {
    for(int j = 0; j <= m; j ++ ) {
        dp[i][j] = dp[i - 1][j];
        if(j >= v[i]) dp[i][j] = max(dp[i - 1][j], dp[i][j - v[i]] + w[i]);
    }
}

// 降维
for(int i = 1 ; i< = n ;i++)
	for(int j = v[i] ; j <=m ;j++) {
        f[j] = max(f[j], f[j - v[i]] + w[i]);
}
```

## 多重背包

```cpp
for (int i = 1; i <= n; i ++ ) {
    for (int j = 0; j <= m; j ++ ) {
        for (int k = 0; k <= s[i] && k * v[i] <= j; k ++ ) {
            f[i][j] = max(f[i][j], f[i - 1][j - v[i] * k] + w[i] * k);
				}
		}
}
```

### 优化

二进制优化，将s个物品使用二进制拆分，转化为0/1背包问题，从而将时间复杂度转为`n^2logs`