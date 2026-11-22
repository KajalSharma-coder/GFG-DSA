## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/longest-subarray-with-sum-divisible-by-k1259/1)

### Problem Description

**Task:** Given an array arr[] and a positive integer k, find the length of the longest subarray with the sum of the elements divisible by k.Note: If there is no subarray with sum divisible by k, then return 0.Examples :Input: arr[] = [2, 7, 6, 1, 4, 5], k = 3

#### Examples

##### Example 1

- **Output:**
```text
2
```
- **Explanation:** The subarray is [2, -2] has sum = 0, which is divisible by 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(min(n, k))

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-22 09:17:55
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
public:
    int longestSubarrayDivK(vector<int>& arr, int k) {
        unordered_map<int, int> mp;

        mp[0] = -1;

        long long sum = 0;
        int ans = 0;

        for (int i = 0; i < arr.size(); i++) {
            sum += arr[i];

            int rem = ((sum % k) + k) % k;

            if (mp.find(rem) != mp.end()) {
                ans = max(ans, i - mp[rem]);
            }
            else {
                mp[rem] = i;
            }
        }

        return ans;
    }
};
```

*Generated on: 11/22/2026, 9:19:14 AM*