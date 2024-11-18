---
title: "Tutorial 6:  18-11-2024"
draft: false
tags:
  - teaching
---
## Map Reduce

Open this [Gdrive folder](https://drive.google.com/drive/folders/1mHLPa0EIPznmFHj_1JctEq9v35sfKZCS?usp=sharing), open the Jupiter Notebook and let us execute the command together.

Then, let's do the exercise at the bottom of the notebook. 

## Dynamic Programming exercise

Solve this exercise on the `unbounded knapsack problem` from Hackerrank: https://www.hackerrank.com/challenges/unbounded-knapsack/problem?isFullScreen=true

> Given an array of integers and a target sum, determine the sum nearest to but not exceeding the target that can be created. To create the sum, use any element of your array zero or more times. 
> 
> For example, if $arr = [2,3,4]$ and your target sum is $10$, you might select $[2,2,2,2,2]$, $[2,2,3,3]$ or $[3,3,3,1]$ . In this case, you can arrive at exactly the target.

### Example with $k = 11$ and $arr = [2,3,4]$ 
In dynamic programming we use the solutions of subproblems to build the solution to the problem. Hence, we build a table like this one to understand the optimal substructure property:

| Capacity (i) | dp[0] | dp[1] | dp[2] | dp[3] | dp[4] | dp[5] | dp[6] | dp[7] | dp[8] | dp[9] | dp[10] | dp[11] |
|--------------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|--------|--------|
| Initial      |   0   |   0   |   0   |   0   |   0   |   0   |   0   |   0   |   0   |   0   |    0   |    0   |
| Value 2      |   0   |   0   |   2   |   2   |   4   |   4   |   6   |   6   |   8   |   8   |   10   |   10   |
| Value 3      |   0   |   0   |   2   |   3   |   4   |   5   |   6   |   7   |   8   |   9   |   10   |   11   |
| Value 4      |   0   |   0   |   2   |   3   |   4   |   5   |   6   |   7   |   8   |   9   |   10   |   11   |


#### Explanation of the table

1. **Initialization**: The `dp` array is initialized to 0.
2. **Value 2**: Update `dp[i]` for each \( i \) from 1 to 10, choosing the maximum between `dp[i]` and `dp[i - 2] + 2`.
3. **Value 3**: Update `dp[i]` for each \( i \) from 3 to 11, choosing the maximum between `dp[i]` and `dp[i - 3] + 3`.
4. **Value 4**: Update `dp[i]` for each \( i \) from 4 to 11, choosing the maximum between `dp[i]` and `dp[i - 4] + 4`.

The final array shows that the maximum value obtainable for a capacity of \( k = 11 \) is 11.

