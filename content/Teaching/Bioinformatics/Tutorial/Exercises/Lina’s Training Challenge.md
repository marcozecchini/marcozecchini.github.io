---
title: Lina’s Training Challenge
tags:
  - teaching
  - greedy
---


## Problem Description

Lina is training for a marathon.  
Each exercise has an **energy cost** (in calories), but the more exercises she completes,  
the **more tired** she becomes.

If Lina has already completed `j` exercises and performs one with `e` calories,  
she will burn:

`e × (j + 1)`

calories.

Lina can perform the exercises in **any order**.  
Your task is to find the **minimum total energy** she will use.

---

## Example

Suppose the energy costs are:

`[4, 2, 7]`

If Lina performs them in this order (2, 4, 7):

|Order|Energy|Total energy used (`e × (j + 1)`)|Cumulative total|
|---|---|---|---|
|1|2|2 × 1 = 2|2|
|2|4|4 × 2 = 8|10|
|3|7|7 × 3 = 21|31|

✅ Minimum total energy = **31**

---

## Function Description

Write the function:

`def linasTraining(energy: list[int]) -> int:`

### The function should:

- Take a list of energy values.
    
- Return the **minimum total energy** Lina needs to spend.
    

---

## Sample Input 1

`[4, 2, 7]`

### Sample Output 1

`31`

---

## Sample Input 2

`[3, 5, 1, 6]`

### Sample Output 2

`41`

---

## Guided Steps

1. **Understand the formula.**  
    For each exercise `i` (in the chosen order), the energy used is `energy[i] × (j + 1)`,  
    where `j` is the number of exercises already done.
    
2. **Write pseudocode.**
    
    - Think about how the order affects the result.
        
    - To minimize the total, should Lina do the _heaviest_ or _lightest_ exercises first?
        
    - Keep a variable to accumulate the total energy.
        
3. **Implement and test.**  
    Write the Python code, then check that your program matches the sample outputs.