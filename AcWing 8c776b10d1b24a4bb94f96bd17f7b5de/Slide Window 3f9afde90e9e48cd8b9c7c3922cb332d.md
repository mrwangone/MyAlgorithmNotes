# Slide Window

| https://leetcode.com/problems/minimum-size-subarray-sum/ | Minimum Size Subarray Sum |
| --- | --- |
| https://leetcode.com/problems/longest-substring-without-repeating-characters/description/ | Slide%20Window%203f9afde90e9e48cd8b9c7c3922cb332d/Slide%20window%20-%20Leetcode%20172f2865d05048afb8bb1ba39b745da0.md |
| https://leetcode.com/problems/find-all-anagrams-in-a-string/ | Find All Anagrams in a String |
| https://leetcode.com/problems/minimum-window-substring/ | Min Window Substring |
| https://leetcode.com/problems/permutation-in-string/ | Permutation in String |
|  |  |
|  |  |

[Slide window - Leetcode](Slide%20Window%203f9afde90e9e48cd8b9c7c3922cb332d/Slide%20window%20-%20Leetcode%20172f2865d05048afb8bb1ba39b745da0.md)

```cpp
/* 滑动窗口算法框架 */
void slidingWindow(string s) {
    unordered_map<char, int> window;
    
    int left = 0, right = 0;
    while (right < s.size()) {
        char c = s[right++];
        winodw.add(c)

        // need shrink?
        while (left < right && window needs shrink) {
				// update result
            char d = s[left++];
            winodw.remove(d)
        }
    }
}
```