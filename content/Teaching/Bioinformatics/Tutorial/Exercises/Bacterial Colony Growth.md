---
title: note on exercises
draft: true
tags:
  - teaching
---
## Context
A microbiologist is studying the growth of a bacterial colony in a petri dish.  
The number of bacteria does not grow linearly — each day the colony expands depending on both the previous two days' populations.

The growth rule is the following:

- Each new generation depends on the **square** of yesterday’s population (because bacteria divide exponentially)
- ...and also gains a small “residual boost” from the population of two days ago.

---

## Problem Description
Given three integers `p1`, `p2`, and `n`, representing the number of bacteria on **day 1**, **day 2**, and the **day of interest** respectively, compute the total population on day `n`, according to this rule:

$p_n = p_{n-1}^2 + p_{n-2}$

---

## Example

**Input**
```

1 2 5

```

**Output**
```

43

```

### Explanation
```

Day 1: p1 = 1  
Day 2: p2 = 2  
Day 3: p3 = 2² + 1 = 5  
Day 4: p4 = 5² + 2 = 27  
Day 5: p5 = 27² + 5 = 734

````

Therefore, on day 5 the colony has **734** bacteria.

---

## Function Description

Implement the following function:

```python
def bacteriaGrowth(p1: int, p2: int, n: int) -> int:
    # Write your code here
````

### Parameters

- `p1`: bacteria count on day 1
    
- `p2`: bacteria count on day 2
    
- `n`: day to predict population for
    

### Returns

- `int`: population on day `n`
    

---

## 💡 Modeling Hint

Before coding, identify:

1. **What type of problem** this is (recursive? iterative?).
2. **How many base cases** are needed.
3. **What changes each step** (relation between day _n_, _n-1_, _n-2_).
    

---

## 🧑‍💻 Sample Solution (Python)

```python
def bacteriaGrowth(p1, p2, n):
    seq = [p1, p2]
    for i in range(2, n):
        next_val = seq[i-1]**2 + seq[i-2]
        seq.append(next_val)
    return seq[n-1]

print(bacteriaGrowth(1, 2, 5))  # Output: 734
```