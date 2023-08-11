# Slide window - Leetcode

## Leetcode 3

### **Longest Substring Without Repeating Characters**

Very elegant code

```cpp
int lengthOfLongestSubstring(string s) {
    unordered_map<char, int> table;
    int result = 0;
    for (int i = 0, j = 0; i < s.size(); ++i) {
        table[s[i]]++;
        while (table[s[i]] > 1) table[s[j++]]--;
        result = max(result, i - j + 1);
    }
    return result;
}
```

### Min Window Substring

```cpp
string minWindow(string s, string t) {
    unordered_map<char, int> need;
    for (auto c : t) need[c]++;
    int need_count = need.size();
    int res = 0;
    int startIndex = -1, endIndex = -1;
    for (int i = 0, j = 0, cur_count = 0; i < s.size(); ++i) {
        if (--need[s[i]] == 0) cur_count++;
        while (cur_count == need_count) {
            if (res == 0 || i - j + 1 < res) {
                res = i - j + 1;
                startIndex = j, endIndex = i;
            }
            if (need[s[j]] == 0) cur_count--;
            need[s[j++]]++;
        }
    }
    if (res == 0) return "";
    return s.substr(startIndex, res);
}
```