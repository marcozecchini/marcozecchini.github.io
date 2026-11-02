---
title: Tutorial 5  2-11-2026
draft: false
tags:
  - teaching
---
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

# Greedy Algorithms

Solve the challenges in this [Colab notebook](https://drive.google.com/file/d/1WKJQLPOxtBURKUPIH_2FUajUZrvLq4T7/view?usp=sharing) (open it with Google Colaboratory and save a copy in your Drive).

Complete the following **challenges**:
1. [[Minimum Absolute Difference in an Array]]
2. [[Mark's cakewalk]]
3. [[Lina’s Training Challenge]]
