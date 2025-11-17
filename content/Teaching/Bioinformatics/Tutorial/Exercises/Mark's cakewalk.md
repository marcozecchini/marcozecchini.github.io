---
title: Mark's cakewalk
tags:
  - teaching
  - greedy
---

## Problem Description

Marc loves cupcakes, but he also likes to stay fit.  
Each cupcake has a certain **calorie count**, and Marc can burn those calories by walking.

If Marc has already eaten `j` cupcakes and eats a new one with `c` calories,  
he must walk at least:	
						$2^j × c$
miles to maintain his weight.

Marc can eat the cupcakes in **any order**.  
Your goal is to find the **minimum total distance** (in miles) he must walk.

---
## Example

Suppose the calorie values are:

```
[1, 3, 2]
```

If Marc eats them in this order (3, 2, 1):

| Order | Calories | Miles to walk (`2^j × c`) | Total so far |
| ----- | -------- | ------------------------- | ------------ |
| 1     | 3        | 2^0 × 3 = 3               | 3            |
| 2     | 2        | 2^1 × 2 = 4               | 7            |
| 3     | 1        | 2^2 × 1 = 4               | 11           |

✅ Minimum total miles = **11**

---
## Function Description

Write the function:

```python
def marcsCakewalk(calorie: list[int]) -> int:
```

### The function should:
- Take a list of calorie values.
- Return the **minimum total miles** Marc needs to walk.
 
 **Hint.**
 *  use `max()` Python function to find the maximum value in a list
 * `list.index(<value>)` to find the index of an element given its value in a list
 * `list.pop(<index>)` to remove an element from a list given its index
 
---
## Sample Input 1

```
[1, 3, 2]
```

### Sample Output 1

```
11
```

---

## Sample Input 2

```
[7, 4, 9, 6]
```

### Sample Output 2

```
79
```

---

## Guided Steps

1. **Understand the formula.**  
    For each cupcake `i` (in the chosen order), Marc walks `2^j * calorie[i]` miles,  
    where `j` is the number of cupcakes already eaten.  
    Try computing it for a few small examples.
    
2. **Write pseudocode.**
	Before writing the code, write the pseudocode implementing the following logic:
    - Think about how the order of eating affects the total.
        
    - To make `2^j * calorie[i]` small, should Marc eat the _largest_ or _smallest_ cupcakes first?
        
    - Keep a variable to track the total miles.  
        Initialize it properly, e.g. `total = 0`.
        
3. **Implement and test.**  
    Translate your plan into Python.  
    Use the sample inputs to check if your result matches the expected outputs.
