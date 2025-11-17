---
title: Modified Fibonacci with DP
tags:
  - DP
  - teaching
---

## Description
Implement a **modified Fibonacci sequence** using the following definition:

$t_n = t_{n-2} + (t_{n-1})^2$

Given three integers `t1`, `t2`, and `n`, compute and print the `n`-th term of this modified Fibonacci sequence.

---
## Example

**Input**
```
0 1 5
```

**Output**
```
5
```

### Explanation
The sequence evolves as follows:
```
t1 = 0  
t2 = 1  
t3 = 0 + 1² = 1  
t4 = 1 + 1² = 2  
t5 = 1 + 2² = 5
t6 = 2 + 5² = 27
````
Therefore, the 5th term is **5**.

A one-dimensional table to keep track of the already computed values would be something like:

| 0   | 1   | 2   | 3   | 4   | 5   | 6   |
| --- | --- | --- | --- | --- | --- | --- |
| 0   | 1   | 1   | 2   | 5   | 27  |     |

---

## Function Description

Implement the following function:

```python
def fibonacciModified(t1: int, t2: int, n: int) -> int:
    # Write your code here
````

### Parameters

- `t1`: first term of the sequence
    
- `t2`: second term of the sequence
    
- `n`: index (1-based) of the term to compute
    

### Returns

- `int`: the `n`-th term of the modified Fibonacci sequence
     
---

## 💡 Hint

Use a loop to build the sequence up to the desired index.  
Remember that each term depends on the **square** of the previous one.

---
## Test

**Input2**
```
0 1 10
```

**Output2**
```
84266613096281243382112
```
