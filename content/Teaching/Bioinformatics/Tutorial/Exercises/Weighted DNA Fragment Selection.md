---
title: Weighted DNA Fragment Selection
draft: false
tags:
  - teaching
  - DP
---
A bioinformatician is analyzing a DNA sample composed of multiple **sequence fragments**.  
Each fragment:
- starts and ends at specific positions on the genome,
- has a **quality score** (indicating its reliability).

However, some fragments **overlap** — and only one fragment can be selected from any overlapping region.

The goal is to select a subset of **non-overlapping fragments** that maximizes the total quality score.

---
## Problem Description
You are given `n` DNA fragments.  

Each fragment `i` is described by:
- a **start position** `s_i`
- an **end position** `f_i`
- a **quality score** `w_i`

Compute the **maximum total quality** achievable by selecting non-overlapping fragments.

---
## Example

**Input**
```
(1, 3, 5)
(2, 5, 6)  
(4, 6, 5)  
(6, 7, 4)
```

Each line represents: `(start, end, weight)`.

**Output**
```
14
````

**Explanation**
- You can select fragment 1 `(1–3, weight 5)`, fragment 3 `(4–6, weight 5)` and fragment 4  `(6–7, weight 4)`.
- They do not overlap, and their total score is `5 + 5 + 4 = 14`.
- This is the optimal configuration.

---
## Function Description

Implement the following function:

```python
class Job:
	def __init__(self, start, finish, profit):
		self.start = start
		self.finish = finish	
		self.profit = profit

def maxFragmentQuality(intervals: Jobs) -> int:
    # Write your code here
````
### Parameters

- `intervals`: a list of tuples `(start, end, weight)` representing fragments
### Returns

- `int`: maximum achievable total quality (sum of weights)

---

## 💡 Modeling Hint


![[Pasted image 20251110124951.png]]

[[Weighted DNA Fragment Selection - GUIDED]]
##  Guided steps

1. **Sort the fragments by end position** (to sort `Job` objects use the function [`sorted`](https://www.w3schools.com/python/ref_func_sorted.asp), properly setting `key`). Why the end? In this order, the fragments that do **not** overlap with fragment `i` are always the **first ones** in the list, up to some position `p(i)`: everything after `p(i)` and before `i` overlaps with it. So "what I can still use if I select `i`" is simply a shorter prefix of the list, a smaller problem we have already solved. Try sorting `(1, 10)`, `(2, 3)`, `(4, 5)` by **start** instead: which earlier fragments are compatible with `(4, 5)`?
2. For each fragment `i`, find the last fragment `p(i)` that finishes **before** `i` starts.
3. **Decide what to do with fragment `i`.** Imagine you have already solved the problem for every shorter prefix of the sorted list: you know the best total quality using only the first fragment, only the first two, and so on up to the first `i-1`. Now consider fragment `i`. There are only two possibilities:
    - **You do not select it.** Then nothing changes: the best you can do is what you could already do with the first `i-1` fragments.
    - **You select it.** You gain its quality score, but every fragment that overlaps with it is now forbidden. Because the list is sorted by end position, the fragments you can still use are exactly the ones up to `p(i)`. So the total is the score of fragment `i` plus the best you could do with the fragments up to `p(i)`.

    The best total for the first `i` fragments is the **larger** of these two values. Call it `dp[i]` and store it, so that later fragments can reuse it without recomputing it.

    Before writing any code:
    - fill the `dp` table **by hand** for the example above, one fragment at a time, writing next to each cell whether you selected the fragment or not;
    - write the rule above as a **formula** for `dp[i]`;
    - what is the value of `dp` when there are **no fragments** to consider?

Use a **1D array `dp`** for tabulation.

    
---

Use these parts in python

```python
# A Binary Search based function to find the latest job
# (before current job) that doesn't conflict with current
# job. "index" is index of the current job. This function
# returns -1 if all jobs before index conflict with it.

def binarySearch(jobs, start_index):
    # Initialize 'lo' and 'hi' for Binary Search
    lo = 0
    hi = start_index - 1
    # Perform binary Search iteratively
    while lo <= hi:
        mid = (lo + hi) // 2
        if jobs[mid].finish <= jobs[start_index].start:
            if jobs[mid + 1].finish <= jobs[start_index].start:
                lo = mid + 1
            else:
                return mid
        else:
            hi = mid - 1
    return -1


# Driver code to test above function
jobs = [Job(1, 2, 50), Job(3, 5, 20), Job(6, 19, 100), Job(2, 100, 200)]
print("Optimal profit is"),
print(schedule(jobs))
```