### Table of Contents

| S No. | Approach                                                                                | Time Complexity | Space Complexity | Result   |
| ----- | --------------------------------------------------------------------------------------- | --------------- | ---------------- | -------- |
| 1     | [Brute Force](#Brute-Force)                                                             | O(N^2)          | O(N)             | Accepted |
| 2     | [Using Sorting](#Using-Sorting)                                                         | O(N*log(N))     | O(N)             | Accepted |
| 3     | [Merge Overlapping Intervals using Sorting](#Merge-Overlapping-Intervals-using-Sorting) | O(N*log(N))     | O(1)             | Accepted |

### <h2>Brute Force</h2>

```py
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        def bubbleSort(Arr):
            n = len(Arr)
            for i in range(n):
                for j in range(n-i-1):
                    if (Arr[j][0] > Arr[j+1][0]):
                        Arr[j], Arr[j+1] = Arr[j+1], Arr[j]
            return Arr
        sortedIntervals = bubbleSort(intervals)
        res = [sortedIntervals[0]]
        for i in range(1, len(sortedIntervals)):
            if (sortedIntervals[i][0] > res[-1][1]):
                res.append(sortedIntervals[i])
            elif (sortedIntervals[i][0] <= res[-1][1] and sortedIntervals[i][1] > res[-1][1]):
                res[-1][1] = sortedIntervals[i][1]
        return res
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using Sorting</h2>

```py
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        sortedIntervals = sorted(intervals)
        res = [sortedIntervals[0]]
        for i in range(1, len(sortedIntervals)):
            if(sortedIntervals[i][0] > res[-1][1]):
                res.append(sortedIntervals[i])
            elif(sortedIntervals[i][0] <= res[-1][1] and sortedIntervals[i][1] > res[-1][1]):
                res[-1][1] = sortedIntervals[i][1]
        return res
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Merge Overlapping Intervals using Sorting</h2>

```py
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        index = 0
        for i in range(1, len(intervals)):
            if (intervals[index][1] >= intervals[i][0]):
                intervals[index][1] = max(intervals[index][1], intervals[i][1])
            else:
                index = index + 1
                intervals[index] = intervals[i]
        return intervals[:index+1]


# Merge Overlapping Intervals using Sorting (time & Space Optimized)
# Time Coplexicity = (n * log(n)) = O(n*logg(n)) => Result = Success
# Space Complexity = O(1)
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/insert-interval/description/">57. Insert Interval</a>
1. <a href="https://leetcode.com/problems/teemo-attacking/description/">495. Teemo Attacking</a>
1. <a href="https://leetcode.com/problems/range-module/description/">715. Range Module</a>
1. <a href="https://leetcode.com/problems/partition-labels/description/">763. Partition Labels</a>
1. <a href="https://leetcode.com/problems/interval-list-intersections/description/">986. Interval List Intersections</a>
1. <a href="https://leetcode.com/problems/longest-substring-of-one-repeating-character/description/">2213. Longest Substring of One Repeating Character</a>
1. <a href="https://leetcode.com/problems/count-integers-in-intervals/description/">2276. Count Integers in Intervals</a>
1. <a href="https://leetcode.com/problems/divide-intervals-into-minimum-number-of-groups/description/">2406. Divide Intervals Into Minimum Number of Groups</a>
1. <a href="https://leetcode.com/problems/determine-if-two-events-have-conflict/description/">2446. Determine if Two Events Have Conflict</a>
1. <a href="https://leetcode.com/problems/count-ways-to-group-overlapping-ranges/description/">2580. Count Ways to Group Overlapping Ranges</a>
1. <a href="https://leetcode.com/problems/points-that-intersect-with-cars/description/">2848. Points That Intersect With Cars</a>
1. <a href="https://leetcode.com/problems/count-days-without-meetings/description/">3169. Count Days Without Meetings</a>



<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
