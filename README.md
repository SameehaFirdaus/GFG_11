# GFG_11
---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Arrays  
---

# 🚀 _Day 11. Maximum Product Subarray_ 🧠
The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/arrays-gfg-160/problem/maximum-product-subarray3604)


## 💡 **Problem Description:**

Given an array `arr[]` that contains both positive and negative integers (and possibly zeros), find the maximum product of any subarray within the array.

**Note:** The result will always fit within the range of a 32-bit integer.

## 🔍 **Example Walkthrough:**

**Input:**  
`arr[] = [-2, 6, -3, -10, 0, 2]`  
**Output:**  
`180`

**Explanation:**  
The subarray with the maximum product is {6, -3, -10} with product = 6 * (-3) * (-10) = 180.

**Input:**  
`arr[] = [-1, -3, -10, 0, 60]`  
**Output:**  
`60`

**Explanation:**  
The subarray with the maximum product is {60}.

**Input:**  
`arr[] = [2, 3, 4]`  
**Output:**  
`24`

**Explanation:**  
For an array with all positive elements, the result is the product of all elements.

### Constraints:
- $`1 ≤ arr.size() ≤ 10^6`$
- $`-10 ≤ arr[i] ≤ 10`$

## 🎯 **My Approach:**

1. **Dynamic Programming with Two Variables (maxVal, minVal):**  
   The idea is to track the maximum and minimum product subarrays up to the current index. The minimum product may become the maximum product if multiplied by a negative number.

2. **Steps:**  
   - Traverse the array, updating the `maxVal` and `minVal` at each step based on the current number.
   - If the current number is negative, we swap `maxVal` and `minVal`.
   - Update `maxProduct` after processing each element to keep track of the overall maximum product encountered.

## 🕒 **Time and Auxiliary Space Complexity** 📝

- **Expected Time Complexity:** O(n), where `n` is the size of the array. The algorithm requires a single pass through the array, making it efficient.  
- **Expected Auxiliary Space Complexity:** O(1), as we use a constant amount of extra space.

## 📝 **Solution Code**
## Code (Python)

```python
class Solution:

    def maxProduct(self, arr):
        max_product = arr[0]
        max_val = arr[0]
        min_val = arr[0]

        for i in range(1, len(arr)):
            if arr[i] < 0:
                max_val, min_val = min_val, max_val

            max_val = max(arr[i], max_val * arr[i])
            min_val = min(arr[i], min_val * arr[i])

            max_product = max(max_product, max_val)

        return max_product
```
