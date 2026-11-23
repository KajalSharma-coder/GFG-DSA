## 01. Character at Position in Infinite String

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/the-infinite-string1049/1)

### Problem Description

**Task:** Given a string s and an integer pos, an infinite string is constructed by repeatedly applying the following operation. In the i-th step, append i consecutive $ characters, followed by the reverse of the current string, to the current string.Formally, if the current string is s, update it as:s = s + ('$' repeated i times) + reverse(s)The initial string is the given s, and the process continues indefinitely. Find and return the character at the pos(1-based indexing) in the resulting infinite string.Examples:Input: s = "12345", pos = 3

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** In "12345...", the character at pos 3 is 3.

##### Example 2

- **Input:**
```text
s = "12345", pos = 10
```
- **Output:**
```text
2
```
- **Explanation:** In "12345$54321...", the character at pos 10 is 2.

##### Example 3

- **Input:**
```text
s = "abc", pos = 7
```
- **Output:**
```text
a
```
- **Explanation:** In "abc$cba...", the character at pos 7 is a.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log (pos))
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-23 21:39:11
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
public:
    char posInfinite(string s, long long pos) {
        vector<long long> len;
        len.push_back(s.size());

        long long i = 1;

        while (len.back() < pos) {
            __int128 nxt = 2 * (__int128)len.back() + i;
            len.push_back(min((long long)nxt, pos));
            i++;
        }

        for (int j = len.size() - 1; j >= 1; j--) {
            long long prev = len[j - 1];
            long long mid = j;

            if (pos <= prev)
                continue;

            if (pos <= prev + mid)
                return '$';

            pos = 2 * prev + mid - pos + 1;
        }

        return s[pos - 1];
    }
};
```

*Generated on: 11/23/2026, 9:39:42 PM*