## 01. Smallest Subarray Sum Greater Than x

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1)

### Problem Description

**Task:** Given an integer x and an array of integers, arr[]. Find the length of the smallest subarray whose sum is strictly greater than x. If no such subarray exists, return 0.Examples:Input: x = 51, arr[] = [1, 4, 45, 6, 0, 19]

#### Examples

##### Example 1

- **Output:**
```text
0
```
- **Explanation:** No subarray has a sum greater than 100. Hence, the answer is 0.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-21 23:21:44
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
public:
    int smallestSubWithSum(vector<int>& arr, int x) {
        int n = arr.size();
        int left = 0;
        long long sum = 0;
        int ans = n + 1;

        for (int right = 0; right < n; right++) {
            sum += arr[right];

            while (sum > x) {
                ans = min(ans, right - left + 1);
                sum -= arr[left];
                left++;
            }
        }

        return ans == n + 1 ? 0 : ans;
    }
};
```

*Generated on: 11/21/2026, 11:22:47 PM*