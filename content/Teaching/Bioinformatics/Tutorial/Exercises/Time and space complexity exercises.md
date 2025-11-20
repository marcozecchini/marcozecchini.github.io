---
title: Time and Space complexity exercises
tags:
  - teaching
---
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
