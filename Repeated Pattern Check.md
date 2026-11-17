## 01. Repeated Pattern Check

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/the-pattern-matcher/1)

### Problem Description

**Task:** Given a string s made of two characters of 'x' and 'y'. The task is to verify whether s is made by concatenating substrings that follow the pattern x^ny^n (equal number of y's follow equal number of x's). Examples:Input: s = "xxyyxy" Output: trueExplanation: The string can be split into "xxyy" + "xy". Both substrings contain an equal number of consecutive 'x' and 'y' characters.Input: s = "xyx"Output: falseExplanation: The last 'x' cannot form a valid substring because it is not followed by a matching 'y'.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(|s|)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-17 07:18:18
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
public:
    bool findPattern(string& s) {
        int n = s.size();
        int i = 0;

        while (i < n) {
            int x = 0, y = 0;

            // Count consecutive x's
            while (i < n && s[i] == 'x') {
                x++;
                i++;
            }

            // Count consecutive y's
            while (i < n && s[i] == 'y') {
                y++;
                i++;
            }

            // Both counts must be equal and non-zero
            if (x == 0 || x != y)
                return false;
        }

        return true;
    }
};
```

*Generated on: 11/17/2026, 7:21:05 AM*