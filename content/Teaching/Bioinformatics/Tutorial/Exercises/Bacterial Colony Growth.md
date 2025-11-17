---
title: Bacterial Colony Growth
draft: false
tags:
  - teaching
  - DP
---
A microbiologist is monitoring the evolution of a bacterial colony inside a controlled environment.  
This time, the colony’s growth depends on **both multiplication and decay effects** happening simultaneously.

The growth rule is now:

- The colony grows proportionally to **twice yesterday’s population**
    
- …but also **loses** a fraction tied to the population from two days ago
    

---

## Problem Description

Given three integers `p1`, `p2`, and `n`, representing the number of bacteria on **day 1**, **day 2**, and the **day to predict**, compute the population on day `n` according to the rule:

$p_n = 2 \cdot p_{n-1} - p_{n-2}$

---

## Example

**Input**

```
3 5 6
```

**Output**

```
21
```

### Explanation

```
Day 1: p1 = 3  
Day 2: p2 = 5  
Day 3: p3 = 2*5 - 3 = 7  
Day 4: p4 = 2*7 - 5 = 9  
Day 5: p5 = 2*9 - 7 = 11  
Day 6: p6 = 2*11 - 9 = 13  
```

So on day 6, the colony contains **13** bacteria.

---

## Function Description

Implement the following function:

```python
def bacteriaGrowth(p1: int, p2: int, n: int) -> int:
    # Write your code here
```

### Parameters

- `p1`: bacteria count on day 1    
- `p2`: bacteria count on day 2
- `n`: the day to compute
### Returns
- `int`: population on day `n`

---
## Modeling Hint

Before coding, identify:

1. **What type of recurrence** this is and whether you prefer recursion or iteration
2. **Which base cases** correspond to days 1 and 2
3. **How each step depends on the previous two populations**