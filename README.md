# 303. Range Sum Query - Immutable

## Problem
Given an integer array `nums`, answer multiple queries where each query asks for the sum of elements between indices `left` and `right` (inclusive).

## Approach
Use a Prefix Sum Array.

- Build a prefix sum array where `prefix[i]` stores the sum of the first `i` elements.
- The sum of any range `[left, right]` can be calculated as:
  
  `prefix[right + 1] - prefix[left]`

This allows each query to be answered in constant time.

## Complexity
- Time Complexity:
  - Constructor: `O(n)`
  - sumRange: `O(1)`
- Space Complexity: `O(n)`

## C++ Code

```cpp
class NumArray {
public:
    vector<int> prefix;

    NumArray(vector<int>& nums) {
        int n = nums.size();
        prefix.resize(n + 1, 0);

        for (int i = 0; i < n; i++) {
            prefix[i + 1] = prefix[i] + nums[i];
        }
    }

    int sumRange(int left, int right) {
        return prefix[right + 1] - prefix[left];
    }
};
