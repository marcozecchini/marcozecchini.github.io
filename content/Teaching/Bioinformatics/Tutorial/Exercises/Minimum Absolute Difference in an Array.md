---
title: Minimum Absolute Difference in an Array
tags:
  - teaching
  - greedy
---


## Problem Description

Given an array of integers, find the **minimum absolute difference** between any two of its elements.

The **absolute difference** between two values `a` and `b` is written as:

							$|a - b|$

It represents the positive difference between the two numbers.

---
## Example

Consider the array:

```
arr = [3, -7, 0]
```

The possible pairs of elements are:

| Pair    | $\|a - b\|$ |
| ------- | ----------- |
| (3, -7) | 10          |
| (3, 0)  | 3           |
| (-7, 0) | 7           |

The smallest absolute difference among these is:

							$\text{min} = 3$

---

## Function Description

Write the function `minimumAbsoluteDifference` with the following signature:

```python
def minimumAbsoluteDifference(arr: list[int]) -> int:
```
 
 Use to compute the absolute value the following Python function:
 
```python
abs()
```
### The function should:

- Receive an array of integers `arr`.
    
- Return a single integer: the **minimum absolute difference** between any two elements in the array.
    
---
## Input Format    
- `n` integers, representing the array elements.
---

## Output Format

Print a single integer — the minimum absolute difference.

## Sample Input 1

```
[3,-7, 0]
```

### Sample Output 1

```
3
```

---
## Sample Input 2

```
 [-59, -36, -13, 1, -53, -92, -2, -96, -54, 75]
```

### Sample Output 2

```
1
```

---
## Sample Input 3

```
[1, -3, 71, 68, 17]
```

### Sample Output 3

```
3
```

### Guided steps

- **Compute absolute differences.**  
    Given two numbers `a` and `b`, compute their absolute difference check if that is correct with python function `abs(a - b)`.  
    Try this on a few pairs from the input array to understand what we are trying to minimize.
    
- **Write pseudocode.**  
    Before writing the code, write the pseudocode implementing the following logic:
    
    - Start with a variable to store the _smallest difference found so far_.  Think carefully about how to initialize it —  it should be a value **larger than any possible difference** (for instance, a very large number).
        
    - Compare every possible pair of elements.
        
    - Each time you find a smaller absolute difference, update your variable.
        
    - After all comparisons, return that smallest value.
        
- **Implement and test.**  
    Translate your pseudocode into Python, then test it on the sample inputs.

