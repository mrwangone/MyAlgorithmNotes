# Monotonic Stack

| https://www.acwing.com/problem/content/832/ | 单调栈 |
| --- | --- |
| https://leetcode.com/problems/sliding-window-maximum/description/ | Sliding window maximum |
| https://leetcode.com/problems/next-greater-element-i/description/ | next-greater-element-i |
| https://leetcode.com/problems/next-greater-element-ii/ | next-greater-element-ii |
| https://leetcode.com/problems/daily-temperatures/ | Next greater temperatures |
| https://leetcode.com/problems/trapping-rain-water/ | Trapping Rain Water |
| https://leetcode.com/problems/largest-rectangle-in-histogram/description/ | Largest Rectangle in Histogram |

### 输出每个数左边第一个比它小的数

```cpp
for (int i = 0; i < n; ++i) {
	while (!stk.empty() && stk.top() >= nums[i]) stk.pop();
	if (!stk.empty()) cout << stk.top();
	else cout << -1;
	stk.push(nums[i]);
}
```

### 滑动窗口最大值

```cpp
vector<int> maxSlidingWindow(vector<int>& nums, int k) {
    deque<int> deq;
    vector<int> res;
    for (int i = 0; i < nums.size(); ++i) {
        if (!deq.empty() && i - k == deq.front()) deq.pop_front();
        while (!deq.empty() && nums[i] >= nums[deq.back()]) deq.pop_back();
        deq.push_back(i);
        if (i >= k - 1) res.push_back(nums[deq.front()]);
    }
    return res;
}
```

```cpp
FindPartition(S) {
  if (Fairsplit(S) == false) return "There is no such a partition"
  // There exists a solution
  Initialize two empty set A and B
  while (S not empty) {
      if (|s| >= 2) {
          pick two arbitrary element a, b
          if (Fairsplit(a + b, S\{a,b}) == true) {
              // a and b belong to the same partition
              if (Fairsplit((sum(A) + (a + b)), sum(B), S\{a, b}) == true) {
                  add a and b to set A
              } else {
                  add a and b to set B
              }
          } else {
              // a and b belong to different partition
              if (Fairsplit((sum(A) + a, sum(B) + b, S\{a, b})) == true) {
                  add a and b to set A
              } else {
                  add a and b to set B
              }
          }
          remove a and b from S
      } else {
          // only one element left
          let a = the last element
         
          if ((sum(A) + a == sum(B)) add a to set A
          else add a to set B
					remove a from S
      }
  }
  return A and B
}
```