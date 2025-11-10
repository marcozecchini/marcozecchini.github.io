---
title: Weighted DNA Fragment Selection
draft: false
tags:
  - teaching
---
### **What is the problem?**

We have several DNA fragments, each with a **start**, **end**, and **quality score**.  
Some fragments **overlap**, and we can’t select two that overlap.  
The goal is to choose a subset of **non-overlapping fragments** that gives the **maximum total quality**.

Formally:  
Given intervals $(s_i, f_i, w_i)$, find  $\max \sum w_i$  such that no two chosen intervals overlap.

### **What are the sub-problems?**
First, we need to find a way to identify sub-problems. 

Every fragment has a start and an end position, and some of them overlap.  
If we want to build an optimal solution step by step, we need a clear order to process them.  
Otherwise, we wouldn’t know which fragments are compatible or which combinations we’ve already evaluated.

- How can we guarantee that, when we evaluate a fragment, all the possible compatible choices have already been considered?
- How can we quickly find the last fragment that doesn’t overlap with the current one? 

The natural answer is to **sort all fragments by their end position**.

When the fragments are **sorted by end position**, the problem of finding the optimal subset up to fragment `i` depends only on:

- the **best solution without using fragment i** (`dp[i-1]`), and
    
- the **best solution that includes fragment i**, which equals the fragment’s weight `wᵢ` plus the **best total quality before the last compatible fragment** (`dp[p(i)]`, where `p(i)` ends before `sᵢ`).

So the sub-problem is:

> _What is the maximum achievable total quality among the first `i` fragments?_

Each sub-problem reuses the results of smaller ones → that’s the essence of **dynamic programming**.

### **What would the solution roughly look like?**

We build an array `dp` where `dp[i]` is the best total quality for the first `i` fragments.  
For each fragment `i`:

```
dp[i] = max(
    w[i] + dp[p(i)],   # include fragment i
    dp[i-1]            # exclude fragment i
)
```

The final answer is `dp[n]`.

Algorithm outline:

1. Sort fragments by `end`.
2. For each fragment, find `p(i)` = the last fragment that ends before `start[i]`.
3. Apply the recurrence above.
    

Time complexity: `O(n log n)` (sorting + binary search for `p(i)`).  
Result for the example: **14**.

---
### **Define the Base Case**

The simplest possible situation is when we have **no fragments** to consider.  
In that case, the maximum total quality is `0`.

So:  

$dp[0] = 0$ 

That’s our **base case** — the starting point for building all other `dp[i]`.

###  **What Decision Do I Make at Step n?**

At fragment `n` (the last one in the sorted list), we face a **binary choice**:

- **Include** the fragment → add its weight `wₙ` to the best total before the last non-overlapping fragment (`dp[p(n)]`);
    
- **Exclude** the fragment → just keep the previous best total (`dp[n−1]`).
    

Formally:  

$dp[n] = \max(wₙ + dp[p(n)],\ dp[n−1])$

This is the **decision rule** — the core of the DP recurrence.

### **What Decision Do I Make at Step n−1 and n+1?**

The same decision logic applies **at every step**:

- At **step n−1**, you decide whether to include fragment `n−1` or skip it.
    
    - If you include it: add `w_{n−1}` + `dp[p(n−1)]`.
        
    - If you skip it: use `dp[n−2]`.
        
- At **step n+1** (if we extended the sequence), you’d again check whether the new fragment `n+1` overlaps with previous ones, then:  
    $dp[n+1] = \max(w_{n+1} + dp[p(n+1)],\ dp[n])$
    
    — same pattern, just shifted one position forward.
    

So at every `i`, the **decision** is always:

> _Include fragment i (and jump back to the last compatible one) or exclude it._

---
### **How many state variables do we have in our subproblems?**

Our subproblem only needs to remember _how far_ we’ve gone in the sorted list of fragments.

We have **1 state variable** in our subproblem:

> the **index `i`** of the fragment we’re considering (after sorting by end time).

Each subproblem asks:

> “What is the maximum achievable total quality using the first `i` fragments?”

So the dynamic programming table `dp[i]` has **one dimension** — it depends only on how many fragments we’ve considered so far.

### **How big is the set of the variables?**

The variable `i` ranges over all fragments:  

$i \in {0, 1, 2, \dots, n}$

So there are **n + 1** possible subproblems (including the base case `i = 0`).

Each subproblem is solved in $O(1)$ once we know `p(i)` 
and computing all `p(i)` values requires $O(n \log n)$ (via binary search after sorting).


