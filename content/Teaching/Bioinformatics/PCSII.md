---
title: Principles of Computer Science II
draft: false
tags:
  - teaching
---
# Objective

The course aim to introduce the algorithmic approach to solving problems correctly and efficiently. Algorithms are ubiquitous in bioinformatics and are often at the interface of computer science and biology. Well established algorithmic techniques will be studied as well as ways to encode them in a computer program using python.

# Program

The course aim to introduce computational thinking and the algorithmic approach to solving problems correctly and efficiently. Algorithms are ubiquitous in bioinformatics and are often at the interface of computer science and biology. We will introduce the algorithmic approach and the theory of algorithms for studying correctness and efficiency, understanding what makes a good algorithm and how to classify them.  
  
We will study characteristic algorithmic techniques and the related computational ideas that are relevant to the field of biology and how to select the most suitable to solve a given task. Topics covered include  
- Searching algorithms  
- Greedy Algorithms
- Dynamic programming algorithms  
- Graph-based algorithms  
- Divide-and-Conquer algorithms  
- Clustering and Tree-based algorithms  
  
We will work with Python and how to write a computer program encoding a given algorithm. 

## Reference book and material

* [@jonasBionformatics](https://eclass.uoa.gr/modules/document/file.php/NURS565/BioinformaticsAlgsBook.pdf): NEIL C. JONES AND PAVEL A. PEVZNER: ***An Introduction to Bioinformatics Algorithms***, A Bradford Book, The MIT Press, Cambridge, Massachusetts, London, England, 2004.

## Contact and discussion

All announcements and discussions will be carried out through [Google Classroom a2xnabfa](https://classroom.google.com/c/ODg3NzEwNzkxNTI5?cjc=a2xnabfa). 
## Tentative detailed program

| Theoretical lecture (usually Thursday)                                                     | Date       | Material                                                                                                                                                                                                                                                                                                                                                                                                                   | Practical Lecture<br>(usually Monday)                                                                               | Date       | Material                                                                                                          |
| ------------------------------------------------------------------------------------------ | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ---------- | ----------------------------------------------------------------------------------------------------------------- |
| **L1**: Computational Thinking                                                             | 1/10/2026  | [[talk1.pdf]]                                                                                                                                                                                                                                                                                                                                                                                                              | **T1**:  Visual Studio, Jupiter notebook and Revisiting python<br>                                                  | 5/10/2026  | [[tutorial1.pdf]]<br><br>[[Tutorial 1]]                                                                           |
| **L2**: Algorithms for Bioinformatics, Complexity of Algorithms, Recursion                 | 8/10/2026  | Chapter 1 and 2 of [jonesBionformatics](https://eclass.uoa.gr/modules/document/file.php/NURS565/BioinformaticsAlgsBook.pdf)                                                                                                                                                                                                                                                                                                | **T2**: Using LLM in code development <br><br>Recursion<br>                                                         | 12/10/2026 |                                                                                                                   |
| **L3**: Sorting Problem                                                                    | 15/10/2026 | Selection Sort Chapter 2.6 of [jonesBionformatics](https://eclass.uoa.gr/modules/document/file.php/NURS565/BioinformaticsAlgsBook.pdf)<br><br>Merge Sort Chapter 7.1 of [jonesBionformatics](https://eclass.uoa.gr/modules/document/file.php/NURS565/BioinformaticsAlgsBook.pdf)<br><br>QuickSort Chapter 12.1 of [jonesBionformatics](https://eclass.uoa.gr/modules/document/file.php/NURS565/BioinformaticsAlgsBook.pdf) | **T3:** Complexity analysis calculation<br><br>Sorting exercises in Python<br><br>                                  | 19/10/2026 |                                                                                                                   |
| **L4**: Greedy Algorithms                                                                  | 22/10/2026 | Chapter 5 of [jonesBionformatics](https://eclass.uoa.gr/modules/document/file.php/NURS565/BioinformaticsAlgsBook.pdf)                                                                                                                                                                                                                                                                                                      | **T4**: Biopython on Google Colab <br><br>Exercises on Greedy Algorithms                                            | 26/10/2026 |                                                                                                                   |
| **L5**: Dynamic Programming Algorithms                                                     | 29/10/2026 | Chapter 6.1, 6.2, 6.3 of [jonesBionformatics](https://eclass.uoa.gr/modules/document/file.php/NURS565/BioinformaticsAlgsBook.pdf)<br>                                                                                                                                                                                                                                                                                      | **S1**: Exercises on Recursion, Greedy algorithms and Sorting<br>                                                   | 2/11/2026  |                                                                                                                   |
| **L6:** Divide and conquer algorithms:<br>Binary search, Merge Sort (again) and Map Reduce | 5/11/2026  | Chapter 7.1 of [jonesBionformatics](https://eclass.uoa.gr/modules/document/file.php/NURS565/BioinformaticsAlgsBook.pdf)<br>                                                                                                                                                                                                                                                                                                | **T5**: <br>Exercises on Dynamic Programming and Map Reduce                                                         | 9/11/2026  |                                                                                                                   |
| **L7:** Advanced Data Structure                                                            | 12/11/2026 |                                                                                                                                                                                                                                                                                                                                                                                                                            | **T6**: Exercises on Dynamic Programming and Divide-and-Conquer<br><br>Biopython for sequence alignment             | 16/11/2026 | Useful resources to solve exercises about DP available on this [blog](https://skerritt.blog/dynamic-programming/) |
| **L8**: Graph Algorithms<br><br>Intro to NetworkX                                          | 19/11/2026 | [[graphs.pdf]]<br><br>Chapter 8.1 of [jonesBionformatics](https://eclass.uoa.gr/modules/document/file.php/NURS565/BioinformaticsAlgsBook.pdf)                                                                                                                                                                                                                                                                              | **T7**: Graph Algorithms on NetworkX and exercises                                                                  | 23/11/2026 | <br>                                                                                                              |
| **L9:** Clustering algorithms                                                              | 26/11/2026 | Chapter 10.1, 10.2, 10.3 of [jonesBionformatics](https://eclass.uoa.gr/modules/document/file.php/NURS565/BioinformaticsAlgsBook.pdf)                                                                                                                                                                                                                                                                                       | **T8:**  Pandas for data manipulation and visualization.<br><br>Exploratory Data Analysis and Clustering Algorithms | 30/11/2026 | <br><br>                                                                                                          |
| **T9:** Exercises on Graphs                                                                | 10/12/2026 |                                                                                                                                                                                                                                                                                                                                                                                                                            | **S2:** Exam Simulation                                                                                             | 14/12/2026 |                                                                                                                   |

# Exercises

At this [page](https://marcozecchini.github.io/Teaching/Bioinformatics/Tutorial/Exercises/), there is a list of exercises we have seen during the semester or that has been left as homework.

If you want to further train yourself with other exercises you can use [Rosalind "Algorithmic Heights"](https://rosalind.info/problems/tree-view/?location=algorithmic-heights), [Rosalind "Bioinformatics Stronghold"](https://rosalind.info/problems/tree-view/) and [Hackerrank](https://www.hackerrank.com/domains/algorithms).

To train on python other exercises are available at [Rosalind "Python Village"](https://rosalind.info/problems/tree-view/?location=python-village)

## Exam dates

| Date       | Note | Location |
| ---------- | ---- | -------- |
| XX/01/2027 |      | TBD      |
| XX/02/2027 |      | TBD      |
| XX/04/2027 |      | TBD      |
| XX/06/2027 |      | TBD      |
| XX/07/2027 |      | TBD      |
| XX/09/2027 |      | TBD      |
| XX/10/2027 |      | TBD      |
### Past editions
More information on the past editions of the course are available at this page: [[(2025-2026) PCSII]]