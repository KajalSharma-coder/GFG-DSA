## 01. Sort in Specific Order

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sort-in-specific-order2422/1)

### Problem Description

**Task:** Given an array arr[] of non-negative integers. Your need to sort them so that The first part of the array contains odd numbers sorted in descending order.The rest of the portion contains even numbers sorted in ascending order.Examples:Input: arr[] = [1, 2, 3, 5, 4, 7, 10]

#### Examples

##### Example 1

- **Output:**
```text
[7, 5, 3, 1, 0, 2, 4]Explanation: 7, 5, 3, 1 are odd numbers in descending order and 0, 2, 4 are even numbers in ascending order.
```
- **Explanation:** 7, 5, 3, 1 are odd numbers in descending order and 2, 4, 10 are even numbers in ascending order.Input: arr[] = [0, 4, 5, 3, 7, 2, 1]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-19 19:41:38
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
public:
    void sortIt(vector<int>& arr) {
        sort(arr.begin(), arr.end(), [](int a, int b) {
            if (a % 2 != b % 2)
                return a % 2 > b % 2;

            if (a % 2 == 1)
                return a > b;

            return a < b;
        });
    }
};
```

*Generated on: 11/19/2026, 7:42:09 PM*