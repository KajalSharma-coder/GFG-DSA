## 01. Min Flips for Alternate

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/min-number-of-flips3210/1)

### Problem Description

**Task:** Given a binary string s, we can flip any bit (change 0 to 1 or 1 to 0) to make the string alternating. A string is called alternating if no two adjacent characters are the same. Find the minimum number of bit flips required to make the string alternating.Examples:Input: s = "001"

#### Examples

##### Example 1

- **Output:**
```text
1
```
- **Explanation:** Flip the bit at index 0 from 0 to 1 to obtain "101", which is an alternating binary string. Hence, the minimum number of flips required is 1.

##### Example 2

- **Input:**
```text
s = "0001010111"
```
- **Output:**
```text
2
```
- **Explanation:** Flip the bit at indices 1 and 8 to obtain "0101010101", which is an alternating binary string. Hence, the minimum number of flips required is 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-20 07:39:09
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
public:
    int minFlips(string &s) {
        int cnt1 = 0, cnt2 = 0;

        for (int i = 0; i < s.size(); i++) {
            // Pattern 010101...
            if (s[i] != (i % 2 == 0 ? '0' : '1'))
                cnt1++;

            // Pattern 101010...
            if (s[i] != (i % 2 == 0 ? '1' : '0'))
                cnt2++;
        }

        return min(cnt1, cnt2);
    }
};
```

*Generated on: 11/20/2026, 7:40:09 AM*