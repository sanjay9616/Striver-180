### Table of Contents

| S No. | Approach                    | Time Complexity | Space Complexity | Result   |
| ----- | --------------------------- | --------------- | ---------------- | -------- |
| 1     | [Brute Force](#Brute-Force) | O(N^2)          | O(1)             | Accepted |

### <h2>Brute Force</h2>

```py
from os import *
from sys import *
from collections import *
from math import *

def getInversions(arr, n) :
	# Write your code here.
    c = 0
    for i in range(n):
        for j in range(i+1, n):
            if (arr[i] > arr[j] and i < j):
                c += 1
    return c

# Taking inpit using fast I/O.
def takeInput() :
    n = int(input())
    arr = list(map(int, stdin.readline().strip().split(" ")))
    return arr, n

# Main.
arr, n = takeInput()
print(getInversions(arr, n))
```

**[⬆ Back to Top](#table-of-contents)**

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
