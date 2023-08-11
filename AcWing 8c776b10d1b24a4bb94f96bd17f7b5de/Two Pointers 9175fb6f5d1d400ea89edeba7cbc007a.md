# Two Pointers

- [ ]  Additional paractice question in labuladong

| Array |  |
| --- | --- |
| https://leetcode.com/problems/remove-duplicates-from-sorted-array/ | Remove duplicates from sorted array |
| https://leetcode.com/problems/remove-element/ | Remove element |
| https://leetcode.com/problems/reverse-string/ | Reverse String |
| https://leetcode.com/problems/move-zeroes/ | Move Zeros |
| https://leetcode.com/problems/longest-palindromic-substring/ | Longest Palindrome |
| https://leetcode.com/problems/is-subsequence/ | Is Subsequence |
| https://leetcode.com/problems/squares-of-a-sorted-array/ | Squares of a Sorted Array |
| https://leetcode.com/problems/reverse-words-in-a-string/ | Reverse Words in a String |
| https://leetcode.com/problems/trapping-rain-water/description/ | Trapping Rain Water |
|  |  |
| Linkedin List |  |
| https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/ | Remove Duplicates from Sorted List |
| https://leetcode.com/problems/merge-two-sorted-lists/description/ | Merge Two Sorted Lists |
| https://leetcode.com/problems/partition-list/description/ | Partition List |
| https://leetcode.com/problems/merge-k-sorted-lists/description/ | Merge k Sorted Lists |
| https://leetcode.com/problems/remove-nth-node-from-end-of-list/ | Remove Nth Node From End of List |
| https://leetcode.com/problems/middle-of-the-linked-list/ | Middle of the Linked List |
| https://leetcode.com/problems/linked-list-cycle/description/ | Linked List Cycle |
| https://leetcode.com/problems/linked-list-cycle-ii/description/ | Linked List Cycle II |
| https://leetcode.com/problems/intersection-of-two-linked-lists/ | Intersection of Two Linked Lists |
|  |  |
| N Sum |  |
| https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/ | 2 Sum II |
| https://leetcode.com/problems/4sum-ii/description/ | 4 Sum II |
| https://leetcode.com/problems/3sum/ | 3 Sum  |
| https://leetcode.com/problems/3sum-smaller/description/ | 3 Sum Smaller |
| https://leetcode.com/problems/3sum-closest/description/ | 3 Sum Closest |
|  |  |
|  |  |
|  |  |

## 判断子序列

```cpp
bool isSubsequence(string s, string t) {
    int i, j;
    for (i = 0, j = 0; i < s.size() && j < t.size(); ) {
        if (s[i] == t[j]) i++;
        j++;
    }
    if (i == s.size()) return true;
    else return false;
}
```

[N Sum](Two%20Pointers%209175fb6f5d1d400ea89edeba7cbc007a/N%20Sum%20ef885f958b114aca97f7280053528d90.md)