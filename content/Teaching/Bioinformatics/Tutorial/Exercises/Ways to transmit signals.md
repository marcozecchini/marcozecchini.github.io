---
title: Ways to transmit signals
draft: false
tags:
  - teaching
  - DP
---
In a synthetic biology experiment, a micro-organism is trying to send an internal signal across a chain of molecular “checkpoints”.  
Each checkpoint can be activated in two different ways:

- by sending a **weak signal** (cost +1), or  
- by sending a **strong signal** (cost +3).

The organism starts at cost 0 and wants to reach **exactly** a total cost of `n`.  
Different sequences of signals matter, because they trigger different reaction cascades.

For example, if `n = 4`, the possible sequences are:

```

1 + 1 + 1 + 1  
1 + 3  
3 + 1

````

→ **3 distinct ways**.

---

## Problem Description

Given an integer `n`, determine how many different ways the organism can reach *exactly* cost `n`, if at each step it can spend either `1` or `3` energy units.

---

## Function Description

```python
def countSignalWays(n: int) -> int:
    # Write your code here
````

### Parameters

- `n`: target total cost
    

### Returns

- `int`: number of distinct ways to reach exactly cost `n`
    

---

## Example

**Input**

```
4
```

**Output**

```
3
```

---

## 💡 Hint

Think in terms of recurrence:

```
ways(n) = ways(n - 1) + ways(n - 3)
```

(because the last signal could have been weak or strong)

Then convert it to an iterative DP using a 1D array.

---

## Test

**Input**

```
10
```

**Output**

```
28
```