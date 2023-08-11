# Backtrack

| https://leetcode.com/problems/permutations/ |
| --- |
| https://leetcode.com/problems/n-queens/ |
| https://leetcode.com/problems/n-queens-ii/ |
| https://leetcode.com/problems/partition-to-k-equal-sum-subsets/ |
| https://leetcode.com/problems/sudoku-solver/ |
|  |
| https://leetcode.com/problems/subsets/ |
| https://leetcode.com/problems/combinations/ |
| https://leetcode.com/problems/permutations/ |
| https://leetcode.com/problems/subsets-ii/ |
| https://leetcode.com/problems/combination-sum-ii/ |
| https://leetcode.com/problems/permutations-ii/ |
| https://leetcode.com/problems/combination-sum/ |
| https://leetcode.com/problems/combination-sum-iii/ |
|  |
|  |
| https://leetcode.com/problems/generate-parentheses/ |
|  |
|  |

```cpp
backtrack(路径, 选择列表):
  if 满足结束条件:
      result.add(路径)
      return
  
  for 选择 in 选择列表:
      做选择
      backtrack(路径, 选择列表)
      撤销选择
```