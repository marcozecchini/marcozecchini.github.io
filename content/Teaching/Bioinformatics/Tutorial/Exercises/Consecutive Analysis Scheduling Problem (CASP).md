---
title: Consecutive Analysis Scheduling Problem (CASP)
tags:
  - teaching
  - DP
---

A bioinformatics researcher is running several **computational analyses** on a workstation.  
Each analysis:

- starts at a specific time,
- ends at a specific time,
- has a **base profit** (e.g., relevance or scientific value).
    
However, the workstation has an optimization feature:  
	**if an analysis starts immediately after another one finishes**, it receives a fixed **bonus** due to warm caches and loaded libraries.

But analyses may **overlap**, and overlapping analyses cannot both be executed.

The goal is to select a subset of **non-overlapping analyses** that maximizes the **total profit**, including bonuses.

---
## Problem Description

You are given `n` analyses.  
Each analysis `i` is described by:

- a **start time** `s_i`    
- an **end time** `f_i`
- a **base profit** `p_i`
    
In addition, you are given a **bonus value** `b`.

If analysis `i` starts **exactly** at the finishing time of a chosen analysis `j`  
(i.e., `f_j == s_i`), then analysis `i` yields:

$\text{profit}_i = p_i + b$

Otherwise, its profit is simply:

$\text{profit}_i = p_i$

Compute the maximum total profit obtainable by selecting a compatible set of analyses.

---

## Example

**Input**

```
b = 10

(1, 3, 20)
(3, 5, 20)
(4, 6, 50)
(6, 7, 30)
(7, 9, 30)
```

Each line represents `(start, end, profit)`.

**Output**

```
120
```

**Explanation**

One optimal schedule is:

- Analysis 1: `(1–3, profit 20)`
    
- Analysis 2: `(3–5, profit 20 + bonus 10 = 30)`
    
- Analysis 4: `(6–7, profit 30)`
    
- Analysis 5: `(7–9, profit 30 + bonus 10 = 40)`
    

Total profit = **20 + 30 + 30 + 40 = 120**.

All selected intervals are non-overlapping.

---

## Function Description

Implement the following function:

```python
class Job:
    def __init__(self, start, finish, profit):
        self.start = start
        self.finish = finish
        self.profit = profit

def maxAnalysisProfit(intervals: Job, bonus: int) -> int:
    # Write your code here
```

### Parameters

- `intervals`: a list of tuples `(start, end, profit)` representing the analyses
    
- `bonus`: an integer value added to the profit of an analysis that starts right after another ends
    

### Returns

- `int`: maximum achievable total profit
    

---

## 💡 Modeling Hint

This problem can be solved with **Dynamic Programming**, following the [[Weighted DNA Fragment Selection]] pattern with a small modification.

---

Use this helper in Python:

```python
# A Binary Search based function to find the latest job
# (before current job) that doesn't conflict with current job.
# Returns -1 if no valid previous job exists.

def binarySearch(jobs, index):
    lo = 0
    hi = index - 1

    while lo <= hi:
        mid = (lo + hi) // 2

        if jobs[mid].finish <= jobs[index].start:
            # Try to see if there’s a later compatible job
            if mid + 1 <= hi and jobs[mid + 1].finish <= jobs[index].start:
                lo = mid + 1
            else:
                return mid
        else:
            hi = mid - 1

    return -1


# Driver code example
jobs = [
    Job(1, 3, 20),
    Job(3, 5, 20),
    Job(4, 6, 50),
    Job(6, 7, 30),
    Job(7, 9, 30)
]

print("Optimal profit is:", maxAnalysisProfit(jobs, bonus=10))
```