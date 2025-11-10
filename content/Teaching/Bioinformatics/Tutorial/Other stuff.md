---
title: note on exercises
draft: true
tags:
  - teaching
---
## Data Visualization 

Complete this [exercise on Jupiter Notebook](https://drive.google.com/file/d/1P9mARbmxR9l9OwTwOUovRcLccQjnndYq/view?usp=drive_link) on the same dataset.

---

https://www.w3resource.com/python-exercises/map/index.php

---
## Unbounded knapsack problem

Solve this exercise on the `unbounded knapsack problem` (source: Hackerrank: https://www.hackerrank.com/challenges/unbounded-knapsack/problem?isFullScreen=true)

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
## Hackerrank - Coin Change Problem

Complete the following **challenge** from Hackerrank: [The Coin Change Problem](https://www.hackerrank.com/challenges/coin-change/problem?isFullScreen=true) 

## Hints

**Example 1**: Suppose you are given the coins 1 cent, 5 cents, and 10 cents with N = 8 cents, what are the total number of combinations of the coins you can arrange to obtain 8 cents. 

```
Input: N=8
        Coins : 1, 5, 10
Output: 2

Explanation: 
1 way: 
      1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 = 8 cents.
2 way:
      1 + 1 + 1 + 5 = 8 cents.
```

All you’re doing is determining all of the ways you can come up with the denomination of 8 cents. Eight 1 cents added together is equal to 8 cents. Three 1 cent plus One 5 cents added is 8 cents. So there are a total of 2 ways given the list of coins 1, 5 and 10 to obtain 8 cents.  

**Example 2**: Suppose you are given the coins 1 cent, 5 cents, and 10 cents with N = 10 cents, what are the total number of combinations of the coins you can arrange to obtain 10 cents. 

```
Input : N=10
        Coins : 1, 5, 10
Output : 4
Explanation: 
1 way: 
   1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 = 10 cents.
2 way: 
   1 + 1 + 1 + 1 + 1 + 5 = 10 cents.
3 way: 
   5 + 5 = 10 cents.
4 way: 
   10 cents = 10 cents.
```

 Remember the idea behind dynamic programming is to cut each part of the problem into smaller pieces. Similar to the example at the top of the page. If we don’t know the value of 4 * 36 but know the value of 4 * 35 (140), we can just add 4 to that value and get our answer for 4 * 36 which by the way is 144.   
 
Okay so we understand what we have to do, but how is a program going to determine how many ways the list of coins can output N? Well lets look that this example. 
```
N = 12         
**Index of Array:** [0, 1,  2]
**Array of coins:** [1, 5, 10]
```

This is a array of coins, 1 cent, 5 cents, and 10 cents. The N is 12 cents. So we need to come up with a method that can use those coin values and determine the number of ways we can make 12 cents.   

Thinking dynamically, we need to figure out how to add to previous data. So what that means is we have to add to previous solutions instead of recalculating over the same values. Clearly, we have to iterate through the entire array of coins. We also need a way to see if a coin is larger than the N value.   
One way to do this is having an array that counts all the way up to the **Nth value**.   

**Array of ways:**

```
 [0, 0, 0 ..... Nth value] in our case it would be up to 12.
```

The reason for having an array up to the Nth value is so we can determine the number of ways the coins make up the values at the index of **Array of ways**. We do this because if we can determine a coin is larger than that value at the index then clearly we can’t use that coin to determine the combinations of the coins because that coin is larger than that value. This can be better understood with an example.  
Using the above numbers as example.

```
N = 12         
**Index of Array of Coins:**    
  [0, 1,  2]     
**Array of coins:**
  [1, 5, 10]

**Index of Array of ways:**   
  [0,  1,  2,  3,  4,  5,  6,  7,  8,  9,  10,  11,  12]
**Array of  ways:**            
  [0,  0,  0,  0,  0,  0,  0,  0,  0,  0,  0,   0,    0]
```

Before we start iterating we have to give a predefined value to our ways array. We must set the first element at index 0 of the ways array to 1. This is because there is 1 way to make the number 0, using 0 coins.   
So if we started iterating through all the coins array and compare the elements to the Array of ways we will determine how many times a coin can be used to make the values at the index of the ways array.  
For example…  
First set ways[0] = 1.  
Lets compare the first coin, 1 cent. 

```
N = 12         
**Index of Array of Coins:**    
  [0, 1,  2]     
**Array of coins:**             
  [1, 5, 10]

**Index of Array of ways:**    
  [0,  1,  2,  3,  4,  5,  6,  7,  8,  9,  10,  11,  12]
**Array of  ways:**            
  [0,  0,  0,  0,  0,  0,  0,  0,  0,  0,  0,   0,    0]

Then compare coins[0] to all of the index's 
of ways array. If the value of the coin is less 
than or equal to the ways index, then
ways[j-coins[i]]+ways[j] is the new value of 
ways[j]. We do this because we are 
trying to break each part down into smaller 
pieces. You will see what is happening as 
you continue to read. So comparing each value of the 
ways index to the first coin, we get the following.

**Index of Array of ways:**    
  [0,  1,  2,  3,  4,  5,  6,  7,  8,  9,  10,  11,  12]
**Array of  ways:**            
  [1,  1,  1,  1,  1,  1,  1,  1,  1,  1,  1,   1,    1]
```

Lets now compare the second coin, 5 cents.

```
N = 12         
**Index of Array of Coins:**    
  [0, 1,  2]     
**Array of coins:**             
  [1, 5, 10]

**Index of Array of ways:**    
  [0,  1,  2,  3,  4,  5,  6,  7,  8,  9,  10,  11,  12]
**Array of  ways:**            
  [1,  1,  1,  1,  1,  1,  1,  1,  1,  1,  1,   1,    1]

Comparing 5 cents to each of the index and
making that same comparison, if the value 
of the coin is smaller than the value of the index at the ways array then ways[j-coins[i]]+ways[j] 
is the new value of ways[j]. Thus we
get the following.

**Index of Array of ways:**    
  [0,  1,  2,  3,  4,  5,  6,  7,  8,  9,  10,  11,  12]
**Array of  ways:**            
  [1,  1,  1,  1,  1,  2,  2,  2,  2,  2,  3,   3,    3]
```

We are determining how many times the second coin goes into all of the values leading up the **Nth** coin. Why are we using all  of the coins? It is to check our previous  result dynamically and update our answer instead of recalculating all over again. For example take the element at index 10  the answer is 3 so far. But how did we get 3?  We know that the value of 10-5 is 5 so that is our j-coins[i] value, that is the difference of what needs to be made up to make the amount 10. So we look at index 5 of the ways array and see it has the value 2, for the same reason as above, there are so far 2  ways to obtain the value 5. So if there are  2 ways to obtain the value 5 then those ways plus the current number of ways is the new updated value of the **TOTAL**  ways to get the value at index 10.                                   

Lets now compare the third coin, 10 cents. 

```
N = 12         
**Index of Array of Coins:**    
  [0, 1,  2]     
**Array of coins:**             
  [1, 5, 10]

Comparing 10 cents to each of the index
and making that same comparison, if the 
value of the coin is smaller than the value of the 
index at the ways array then 
ways[j-coins[i]]+ways[j] is the new value of ways[j]. 
Thus we get the following.

**Index of Array of ways:**    
  [0,  1,  2,  3,  4,  5,  6,  7,  8,  9,  10,  11,  12]
**Array of  ways:**            
  [1,  1,  1,  1,  1,  2,  2,  2,  2,  2,  4,   4,    4]
```

So the answer to our example is ways[12] which is 4.

With all of the above in mind, write a program that:
1. Create the `ways` array of the size of the `N`  plus 1 to stop overflow
2. Set the first element of `ways` to 1 because it is 0 and there is 1 way to make 0 with 0 coins
3. Go through all of the coins, then for each coin
	1. Make a comparison to each index value of ways with the coin value
	2. Update the ways array
4.  Return the value at the `N`th position of the ways array.
 
## Biopython

Open this [Jupiter Notebook](https://drive.google.com/file/d/1R1pJfK2Lsw2JejsIQTg7dMPqVsemc32s/view?usp=drive_link) and let us execute the command together.

Then, let's do the exercise at the bottom of the notebook. 


