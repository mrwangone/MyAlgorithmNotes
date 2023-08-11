# Knapsack - Leetcode

## word break

为什么常规完全背包不行？

e.g `s = “applepenapple” dict = “apple, pen”`

在使用apple遍历的时候，dp[8]是为false的，因为没有使用pen遍历，当使用pen遍历时，不会再回到apple遍历了

为什么coin change可以使用常规完全背包？

e.g `coin = 5, 3 target = 13`

在使用5遍历时，`dp[8]` 也是`false`，但`dp[10]`会是`true`，当使用3遍历时，就可以达到5，5，3的valid组合

所以正解是结尾的单词做集合分类，同combination sum IV