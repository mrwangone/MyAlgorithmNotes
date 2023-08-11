# Binary Search - Leetcode

## Leetcode 34

### Search for boundary

Applying the template, first think about what is the `check` funtion

e.g. Search for left boudary, we want to search `nums[mid] >= target`

```cpp
int binary_search1(vector<int>& nums, int l, int r, int target) {
      while (l < r) {
          int mid = l + r >> 1;
          if (nums[mid] >= target) r = mid;
          else l = mid + 1;
      }
      if (nums[l] != target) return -1;
      else return l;
  }

  int binary_search2(vector<int>& nums, int l, int r, int target) {
      while (l < r) {
          int mid = l + r + 1 >> 1;
          if (nums[mid] <= target) l = mid;
          else r = mid - 1;
      }
      if (nums[l] != target) return -1;
      else return l;
  }
```

## Leetcode 33

### **Search in Rotated Sorted Array**

非常经典的一道二分，运用的不是单调性，而是数组可以被划分为两部分，拥有不同的性质

`前面一部分 ≥ nums[0]， 后一部分 < nums[0]`

两次二分

1. 找到分界点
2. 根据target的性质，在对应的部分二分查找

```cpp
int search(vector<int>& nums, int target) {
     int n = nums.size(); 
     if (n == 0) return -1;
     int l = 0, r = n - 1;
     while (l < r) {
         int mid = l + r + 1 >> 1;
         if (nums[mid] >= nums[0]) l = mid;
         else r = mid - 1;
     }
     if (target >= nums[0]) l = 0;
     else {
         l = r + 1;
         r = n - 1;
     }
     while (l < r) {
         int mid = l + r >> 1;
         if (nums[mid] >= target) r = mid;
         else l = mid + 1;
     }
     if (nums[r] == target) return r;
     else return -1;
  }
```

## Leetcode 81

### **Search in Rotated Sorted Array II**

基本和上一个一样，区别是可以有重复

那么破坏了可以二分的性质，我们把结尾的和`nums[0]` 相等的元素都删掉，使他重新具有可以被二分的性质

```cpp
bool search(vector<int>& nums, int target) {
        int n = nums.size();
        int R = n - 1;
        while (R >= 0 && nums[R] == nums[0]) R--;
        if (R < 0) return nums[0] == target;

        int l = 0, r = R;
        while (l < r) {
           int mid = l + r + 1 >> 1;
           if (nums[mid] >= nums[0]) l = mid;
           else r = mid - 1;
        }
        if (target >= nums[0]) l = 0;
        else {
            l = r + 1;
            r = n - 1;
        }
        while (l < r) {
            int mid = l + r >> 1;
            if (nums[mid] >= target) r = mid;
            else l = mid + 1;
        }
        if (nums[r] == target) return true;
        else return false;
    }
```

## Leetcode 162

### **Find in Peak element**

Find the first element that is grater than the next element

`if (nums[mid] > nums[mid + 1]) r = mid;`

```cpp
int findPeakElement(vector<int>& nums) {
    int n = nums.size();
    int l = 0, r = n - 1;
    while (l < r) {
        int mid = l + r >> 1;
        if (nums[mid] > nums[mid + 1]) r = mid;
        else l = mid + 1;
    }
    return l;
}
```

## Leetcode 1095

### **Find in Mountain Array**

Similar to previous one, first we find where the peak is, and search on both side seperately

```cpp
int findInMountainArray(int target, MountainArray &mountainArr) {
    int n = mountainArr.length();
    int l = 0, r = n - 1;
    while (l < r) {
        int mid = l + r >> 1;
        if (mountainArr.get(mid) > mountainArr.get(mid + 1)) r = mid;
        else l = mid + 1;
    }
    int pivot = l;

    l = 0, r = pivot;
    while (l < r) {
        int mid = l + r >> 1;
        if (mountainArr.get(mid) >= target) r = mid;
        else l = mid + 1;
    }
    if (target == mountainArr.get(l)) return l;

    l = pivot, r = n - 1;
    while (l < r) {
        int mid = l + r >> 1;
        if (mountainArr.get(mid) <= target) r = mid;
        else l = mid + 1;
    }
    if (target == mountainArr.get(l)) return l;
    return -1;
}
```

## Leetcode 74

### **Search a 2D Matrix**

本质是二分，重点是如何将二维数组下标映射到一维

`n = # column`

`row = mid / n`

`col = mid % n`

```cpp
bool searchMatrix(vector<vector<int>>& matrix, int target) {
    int m = matrix.size(), n = matrix[0].size();
    int l = 0, r = m * n - 1;
    while (l < r) {
        int mid = l + r >> 1;
        if (matrix[mid / n][mid % n] >= target) r = mid;
        else l = mid + 1;
    }
    if (matrix[l / n][l % n] == target) return true;
    return false;
}
```

## Leetcode 287

### **Find the Duplicate Number**

1. 每次把值域分成两段，遍历给定的整个数组，统计其落在左半边子值域之间值的数字的个数 
2. 若落在此值域的数字个数大于该值域长度，说明该值域区间的数字必有重复

```cpp
int findDuplicate(vector<int>& nums) {
    int n = nums.size();
    int range = n - 1;
    int l = 1, r = n - 1;
    while (l < r) {
        int mid = l + r >> 1;
        int count = 0;
        for (int num : nums) {
            if (num >= l && num <= mid) count++;
        }
        if (count > mid - l + 1) r = mid;
        else l = mid + 1;
    }
    return l;
}
```

## Leetcode 378

### **Kth Smallest Element in a Sorted Matrix**

扫描矩阵中小于等与`mid` 的个数，然后二分

搜索方式：找小于等于x的数的个数cnt和k比较
cnt >= k：由于可能有多个x相同，因此答案可能是当前位置或之前位置
cnt < k：说明x位置太靠左了，答案在右边

与上一道题异曲同工，并利用了**单调矩阵**的特点，在 `O(n)` 的时间内遍历

Question：mid是值域范围内的中间值，不一定是matrix里面的值，为什么最后结果 就一定是matrix里面的值呢？

Answer：如果最后二分出的`t`不在矩阵中，那么`<= t`的数的个数必然跟`<= t - 1`的数的个数一样多，说明`t - 1`也是满足要求的，但是我们二分出的是满足要求的最小值，就矛盾了

```cpp
int kthSmallest(vector<vector<int>>& matrix, int k) {
      int n = matrix.size();
      int l = matrix[0][0], r = matrix[n - 1][n - 1];
      while (l < r) {
          int mid = (long long) l + r >> 1;
          int j = n - 1, count = 0;
          for (int i = 0; i < n; ++i) {
              while (j >= 0 && matrix[i][j] > mid) j--;
              count += j + 1;
          }
          if (count >= k) r = mid;
          else l = mid + 1;
      }
      return r;
  }
```

## Leetcode 668

### **Kth Smallest Number in Multiplication Table**

与上一题几乎一模一样

```cpp
bool check(int m, int n, int mid, int k) {
      int count = 0;
      for (int i = 1; i <= n; ++i) {
          count += min(m, mid / i);
      }
      return count >= k;
  }
  int findKthNumber(int m, int n, int k) {
     
      int l = 1, r = (m * n);
      while (l < r) {
          int mid = (long long) l + r >> 1;
          if (check(m, n, mid, k)) r = mid;
          else l = mid + 1;
      }
      return r;
  }
```

## Leetcode 410

### **Split Array Largest Sum**

思考过程：判断是否有一种方案，使得每一段 `≤ mid`， 能够分成`k`段

那么我们就可以check最少可以分成多少段，如果 `≤ m`, 那么符合条件（贪心）

```cpp
bool check(vector<int>& nums, int mid, int k) {
      int count = 0, sum = 0;
      for (auto num : nums) {
          if (num > mid) return false;
          if (num + sum > mid) {
              count++;
              sum = num;
          } else {
              sum += num;
          }  
      }
      if (sum) count++;
      return count <= k;
  }

  int splitArray(vector<int>& nums, int k) {
      int n = nums.size();
      int l = 0, r = INT_MAX;
      while (l < r) {
          int mid = (long long) l + r >> 1;
          if (check(nums, mid, k)) r = mid;
          else l = mid + 1;
      }
      return l;
  }
```

## Leetcode 793

### **Preimage Size of Factorial Zeroes Function**

巧妙地地方在于如何计算出 结尾0小于等于k的数 的个数

恰好有k个 = `calc(k) - calc(k - 1)`

```cpp
int preimageSizeFZF(int k) {
    return calc(k) - calc(k - 1);
}

long long calc(int k) {
    long long l = -1, r = 1e18;
    while (l < r) {
        long long mid = l + r + 1 >> 1;
        if (calculateTailZero(mid) <= k) l = mid;
        else r = mid - 1;
    }
    return (int) l;
}

long long calculateTailZero(long long mid) {
    long long result = 0;
    while (mid) {
        result += mid / 5;
        mid /= 5;
    }
    return result;
}
```

## Leetcode 878

### **Nth Magical Number**

`get(mid, a, b)` 计算从0到`mid`有多少数能被`a`和`b`整除

```cpp
int gcd(int a, int b) {
    return b ? gcd(b,  a % b) : a;
}

long long get(long long mid, int a, int b) {
    return mid / a + mid / b - mid / ((a * b) / gcd(a, b));
}

int nthMagicalNumber(int n, int a, int b) {
    long long l = 1, r = 4e13;
    const int MOD = 1e9 + 7;
    while (l < r) {
        long long mid = l + r >> 1;
        if (get(mid, a, b) >= n) r = mid;
        else l = mid + 1;
    }
    return l % MOD;
}
```