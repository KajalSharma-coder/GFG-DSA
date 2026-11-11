## 01. Any Duplicate Within K Distance

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/kth-distance3757/1)

### Problem Description

**Task:** Given an array of integers, arr[] and an integer k, check whether there exist two distinct indices i and j such that arr[i] is equal to arr[j] and the absolute difference between i and j is at most k.Examples:Input: arr[] = [1, 5, 4, 5, 1], k = 3Output: trueExplanation: The element 5 occurs at indices 1 and 3. Their distance is |3 - 1| = 2, which is less than or equal to k.Input: arr[] = [10, 2, 3, 4, 10, 5], k = 3Output: falseExplanation: The element 10 occurs at indices 0 and 4. Their distance is |4 - 0| = 4, which is greater than k. Hence, no duplicate exists within the given distance.Input: arr[] = [5, 1, 3, 2, 4], k = 3Output: falseExplanation: All elements are distinct, so no duplicate exists.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(min(n, k))

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-11 14:37:05
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
public:
    bool checkWithinK(vector<int>& arr, int k) {
        unordered_set<int> st;

        for (int i = 0; i < arr.size(); i++) {

            // Remove element outside the window
            if (i > k) {
                st.erase(arr[i - k - 1]);
            }

            // Duplicate found within distance k
            if (st.find(arr[i]) != st.end()) {
                return true;
            }

            st.insert(arr[i]);
        }

        return false;
    }
};
```

*Generated on: 11/11/2026, 2:37:30 PM*