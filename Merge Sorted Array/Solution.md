### Table of Contents

| S No. | Approach                                                                                | Time Complexity | Space Complexity | Result  |
| ----- | --------------------------------------------------------------------------------------- | --------------- | ---------------- | ------- |
| 1     | [Two Pointers In-place Merge](#Two-Pointers-In-place-Merge)                             | O(N+M)          | O(1)             | Success |
| 2     | [Using-Python-Built-in-Functions](#UsingPython-Built-in-Functions)                      | O(N+M)          | O(1)             | Success |
| 3     | [Traverse From Beginning using Two Pointer](#Traverse-From-Beginning-using-Two-Pointer) | O(N+M)          | O(M+N)           | Success |

### <h2>Two Pointers In-place Merge</h2>

```py
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i, j, k = m - 1, n - 1, m + n - 1
        while(i >= 0 and j >= 0):
            if(nums1[i] > nums2[j]):
                nums1[k] = nums1[i]
                i -= 1
            else:
                nums1[k] = nums2[j]
                j -= 1
            k -= 1
        # If there are remaining elements in nums2
        while(j >= 0):
            nums1[k] = nums2[j]
            j -= 1
            k -= 1
```
**[⬆ Back to Top](#table-of-contents)**

### <h2>Using-Python-Built-in-Functions</h2>

```py
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        nums1[m:] = nums2  # Fill in nums1's empty spaces with nums2
        nums1.sort()
```
**[⬆ Back to Top](#table-of-contents)**

### <h2>Traverse From Beginning using Two Pointer</h2>

```py
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i, j, merged = 0, 0, []
        while i < m and j < n:
            if nums1[i] < nums2[j]:
                merged.append(nums1[i])
                i += 1
            else:
                merged.append(nums2[j])
                j += 1
        while i < m: # If there are remaining elements in nums1
            merged.append(nums1[i])
            i += 1
        while j < n: # If there are remaining elements in nums2
            merged.append(nums2[j])
            j += 1
        for k in range(len(merged)): # Copy the merged result back to nums1
            nums1[k] = merged[k]
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/merge-two-sorted-lists/description/">21. Merge Two Sorted Lists</a>
2. <a href="https://leetcode.com/problems/squares-of-a-sorted-array/description/">977. Squares of a Sorted Array</a>
3. <a href="https://leetcode.com/problems/interval-list-intersections/description/">986. Interval List Intersections</a>
4. <a href="https://leetcode.com/problems/take-k-of-each-character-from-left-and-right/description/">2516. Take K of Each Character From Left and Right</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
