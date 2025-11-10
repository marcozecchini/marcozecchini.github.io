---
title: Ways to climb stairs
draft: false
tags:
  - teaching
---
In a lab experiment, a biologist is studying how a **cell** accumulates energy to activate a certain biochemical process.  
Every few seconds, the cell can **absorb** small energy packets from its environment — but not all packets have the same intensity.

At each step, the cell can:
- absorb a **small packet** (+1 energy unit), or  
- absorb a **large packet** (+2 energy units).

The cell starts with 0 energy and wants to reach *exactly* an energy level of `n` units to trigger a reaction.

However, the **order** in which packets are absorbed matters, because the biochemical reactions depend on the sequence of inputs.  
For example, absorbing a large packet first (`2 + 1`) produces a different internal configuration than starting with a small one (`1 + 2`).

---

## Problem Description
Given an integer `n`, representing the target energy level (or number of steps), determine how many **distinct ways** exist to reach exactly that level if the cell can take either **1-step** or **2-steps** at a time.

For example:
- If `n = 3`, the possible combinations are:
```
1+1+1  
1+2  
2+1
````
→ 3 ways in total.

---
## Function Description

```python
def countWays(n: int) -> int:
  # Write your code here
````

### Parameters

- `n`: total number of steps (energy units)   

### Returns

- `int`: total number of ways to reach the target
    

---

## Example

**Input**

```
3
```

**Output**

```
3
```

---

## 💡 Hint

Think recursively first:  

$ways(n) = ways(n-1) + ways(n-2)$

(because from step `n` you could have come either from `n-1` or from `n-2`)

Then convert it into an **iterative tabulation** with a **1D array**.

| 1   | 2   | 3   | 4   | 5   | 6   |
| --- | --- | --- | --- | --- | --- |
| 1   | 2   | 3   | 5   | ?   | ?   |

Key technique: avoid to recompute every time the recursion!

---
## Test


**Input2**
```
10
```

**Output2**
```
89
```
