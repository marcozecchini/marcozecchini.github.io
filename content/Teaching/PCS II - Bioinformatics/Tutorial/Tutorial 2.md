---
title: "Tutorial 2:  10-10-2024"
draft: false
tags:
  - teaching
---
* Live notes about this tutorial are available at this [link](https://docs.google.com/document/d/1ombhMbTjcVoPJB_WtHQcYKxq0CFTs08ZrynRf43CWG4/edit?usp=sharing)

# Pandas
A smarter and more abstract tool to handle `.csv` files is another Python tool named [Pandas](https://pandas.pydata.org/)

We use Pandas to:
1. **Manipulate** data. 
2. **Visualize and plot** data combined with [matplotlib](https://matplotlib.org/) library

## Install Pandas and Matplotlib
Install pandas following the instruction available at this [web page](https://pandas.pydata.org/docs/getting_started/install.html#installing-from-pypi).

Install matplotlib following the instruction available at this [web page](https://matplotlib.org/stable/users/getting_started/). 
## Manipulate and Visualize data
Let us take a look at this [presentation](https://docs.google.com/presentation/d/182TDzx4_aH5FOQfr2fP3j4N5dYejSLbo/edit?usp=sharing&ouid=115823646834530022478&rtpof=true&sd=true).

**Keeping Pandas API Documentation at hand with this [link](https://pandas.pydata.org/docs/reference/index.html)**, let us see Pandas in action now:
1. Create a file named `ManipulateVisualize.ipynb`
2. Run the Jupiter Notebook in Visual Studio Code ([more details here](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)) on the `.csv` dataset [Salary Data.csv](https://drive.google.com/file/d/1jxSWVRcQ4MC_rHYZFEYnjmei9Fe9p4w2/view?usp=sharing)
3. Follow and repeat my instructions on your Jupiter!

## Exercises

Complete this [exercise on Jupiter Notebook](https://drive.google.com/file/d/1P9mARbmxR9l9OwTwOUovRcLccQjnndYq/view?usp=drive_link) on the same dataset.

# Recursion 

> Recursion is a way of programming or coding a problem, in which a function calls itself one or more times in its body. Usually, it is returning the return value of this function call. If a function definition fulfils the condition of recursion, we call this function a recursive function. 

Remember, the termination condition: 
1. A recursive function has to terminate to be used in a program.
2. A base case is a case, where the problem can be solved without further recursion. **Tips: start by identifying the base case**.
3. A recursive function terminates, if with every recursive call the solution of the problem is downsized and moves towards a base case.

Solve this exercise on [Rosalind](https://rosalind.info/problems/rna/) with a recursive approach.