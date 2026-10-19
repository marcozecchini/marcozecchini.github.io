---
title: "Tutorial 3:  20-10-2025"
draft: false
tags:
  - teaching
---
# Recursion

> Recursion is a way of programming or coding a problem, in which a function calls itself one or more times in its body. Usually, it is returning the return value of this function call. If a function definition fulfils the condition of recursion, we call this function a recursive function. 

Remember, the termination condition: 
1. A recursive function has to terminate to be used in a program.
2. A base case is a case, where the problem can be solved without further recursion. **Tips: start by identifying the base case**.
3. A recursive function terminates, if with every recursive call the solution of the problem is downsized and moves towards a base case.

The pseudocode of the book may call itself, exactly like a Python function (Jones & Pevzner, Sections 2.5-2.6, pp. 24-33):

```
FACTORIAL(n)
1  if n = 1
2      return 1
3  return n · FACTORIAL(n - 1)
```
```python
def factorial(n):
    if n == 1:
        return 1
    return n * factorial(n - 1)
```

Line 1 is the base case; line 3 calls the algorithm on a smaller input. Without the base case the calls would go on forever and Python stops with `RecursionError: maximum recursion depth exceeded` (after about 1000 nested calls). Same error if the base case is never reached: try `factorial(0)`.

Let us solve the following exercises, following this approach:
1. Identify the **base case** and write it down.
2. Write the **recursive case**: the answer for the input in terms of the answer for a smaller input.
3. Write the **pseudocode** of the solving this exercise using a recursive approach, in the style of the book.
4. Implement the pseudocode in a **Python program** and test it on the examples.
5. (bonus) Write the **iterative** version with a loop and compare the two.

### Exercise 7: power
Write a recursive function that accepts two numbers as its argument and returns its power: `power(x, n)` returns x^n for an integer n ≥ 0, without using `**`.

For example, `power(2, 10)` returns `1024` and `power(5, 0)` returns `1`. Hint: x^n = x · x^(n-1). What is x^0?

### Exercise 8: sum of the first n natural numbers
Write a recursive function that calculate sum of first n natural numbers.

For example, `sum_to(10)` returns `55`. Hint: 1 + 2 + ... + n = n + (1 + 2 + ... + (n - 1)). Compare with `SUMINTEGERS` of Tutorial 1: same problem, iterative then and recursive now.

### Exercise 9: greatest common divisor
Write a program that reads two integers from keyboard and calculate the [greatest common divisor](https://en.wikipedia.org/wiki/Greatest_common_divisor) (gcd) using recursive function.

Euclid's observation: the gcd of a and b, with b > 0, is the same as the gcd of b and a mod b (the remainder, `a % b`); and gcd(a, 0) = a. For example, `gcd(48, 18)` returns `6`: the calls are (48, 18) → (18, 12) → (12, 6) → (6, 0). Read the two integers with `ask_integer` of Exercise 6. Question: does every call make the problem smaller? Which argument shrinks?

### Exercise 10: transcribing DNA into RNA
Exercise on [Rosalind](https://rosalind.info/problems/rna/) on RNA: given a DNA string, return its transcription, obtained by replacing every `T` with `U`. For example, `GATGGAACTTGACTACGTAAATT` becomes `GAUGGAACUUGACUACGUAAAUU`.

1. Write a recursive `transcribe(t)`: the base case is the empty string; otherwise transcribe the first character and append the transcription of the rest, `t[1:]`.
2. Download the dataset from Rosalind, read it from the file (Part 2), write the answer to a file and submit it.
3. Question: what happens with a string of 10 000 nucleotides? Try it, read the error, and write the iterative version (a loop, or `t.replace("T", "U")`).

## Sum of Digits of an Integer Using Recursion

Write a Python program to get the sum of the digits of a non-negative integer using recursion.

## Time and space complexity

**Exercise 1**

> What is the time and space complexity of the following code: 

```python
a = 0
b = 0
for i in range(N):
  a = a + random()

for i in range(M):
  b= b + random()
```

**Exercise 2**

> What is the time complexity of the following code: 

```python
a = 0;
for i in range(N):
  for j in reversed(range(i,N)):
    a = a + i + j;
```

**Exercise 3**

> What is the time complexity of the following code: 

```python
k = 0;
for i in range(n//2,n):
  for j in range(2,n,pow(2,j)):
        k = k + n / 2;
```

# Counting sort

Do the following exercises: 
1. https://www.hackerrank.com/challenges/countingsort1/problem
2. https://www.hackerrank.com/challenges/countingsort2/problem

Then, compute the time complexity and space complexity of counting sort.