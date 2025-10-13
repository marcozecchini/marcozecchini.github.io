---
title: "Tutorial 2:  13-10-2025"
draft: false
tags:
  - teaching
---
# Jupyter Notebook 

Look at minute [2:29](https://youtu.be/D2cwvpJSBX4?si=f-UQPaFNuXKlfwTm&t=149) of the following video to understand what Virtual Env is.

![venv](https://youtu.be/D2cwvpJSBX4?si=f-UQPaFNuXKlfwTm&t=149)

Let us create a Virtual Environment following the steps in the video! Now watch this second video on Jupyter Notebook:

![jupyter](https://www.youtube.com/watch?v=suAkMeWJ1yE)

# Pandas
A smarter and more abstract tool to handle `.csv` files is another Python tool named [Pandas](https://pandas.pydata.org/)

We use Pandas to:
1. **Manipulate** data. 
2. **Visualize and plot** data combined with [matplotlib](https://matplotlib.org/) library
## Install Pandas and Matplotlib
Install pandas in the virtual environment following the instruction available at this [web page](https://pandas.pydata.org/docs/getting_started/install.html#installing-from-pypi).

Install matplotlib in the virtual environment  following the instruction available at this [web page](https://matplotlib.org/stable/users/getting_started/). 
## Manipulate data
Let us take a look at this [presentation](https://docs.google.com/presentation/d/182TDzx4_aH5FOQfr2fP3j4N5dYejSLbo/edit?usp=sharing&ouid=115823646834530022478&rtpof=true&sd=true).

**Keeping Pandas API Documentation at hand with this [link](https://pandas.pydata.org/docs/reference/index.html)**, let us see Pandas in action now:
1. Create a file named `ManipulateVisualize.ipynb`
2. Run the Jupiter Notebook in Visual Studio Code ([more details here](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)) on the `.csv` dataset [Salary Data.csv](https://drive.google.com/file/d/1jxSWVRcQ4MC_rHYZFEYnjmei9Fe9p4w2/view?usp=sharing)
3. Follow and repeat my instructions on your Jupiter!
## Exercise Data Manipulation

Given [Salary Data.csv](https://drive.google.com/file/d/1jxSWVRcQ4MC_rHYZFEYnjmei9Fe9p4w2/view?usp=sharing):
- **Find the average salary by education level.**
- **Find the person(s) with the highest salary** and display their `Job Title` and `Years of Experience`

# Recursion 

> Recursion is a way of programming or coding a problem, in which a function calls itself one or more times in its body. Usually, it is returning the return value of this function call. If a function definition fulfils the condition of recursion, we call this function a recursive function. 

Remember, the termination condition: 
1. A recursive function has to terminate to be used in a program.
2. A base case is a case, where the problem can be solved without further recursion. **Tips: start by identifying the base case**.
3. A recursive function terminates, if with every recursive call the solution of the problem is downsized and moves towards a base case.

Let us solve the following exercises, following this approach:
1. Write the **pseudocode** of the solving this exercise using a recursive approach
2. Implement the pseudocode in a **Python program**

### Exercise 1
Write a recursive function that accepts two numbers as its argument and returns its power.

### Exercise 2
Write a recursive function that calculate sum of first n natural numbers.

### Exercise 3

Write a program that reads two integers from keyboard and calculate the [greatest common divisor](https://en.wikipedia.org/wiki/Greatest_common_divisor) (gcd) using recursive function

### Exercise 4

Exercise on [Rosalind](https://rosalind.info/problems/rna/) on RNA.