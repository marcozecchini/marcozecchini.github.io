---
title: "Tutorial 2:  12-10-2025"
draft: false
tags:
  - python
  - teaching
---
# Plan of the tutorial

Same recipe as in Tutorial 1: for each topic, a short reminder of the concept and then an exercise. Four parts:

1. **Warm-up**: Python exercises one notch harder than last time (strings, lists, dictionaries, user input).
2. **Files**: reading and writing text and CSV files, where the data of bioinformatics lives.
3. **Errors**: how to read an error message, and how to handle errors with `try`/`except`.
4. **Recursion**: the exercises of Lecture 2, pseudocode first, then Python.

Open the Google Colab notebook of the tutorial at this [link](https://drive.google.com/file/d/1ptRH7Uc9zFp9PFtmfX988d0lGKpeyRWI/view?usp=sharing) (you need a Google account): it contains the reminders, the exercises and a cell of **tests** for each exercise. As in Tutorial 1: **File > Save a copy in Drive**, run the cells in order with **Shift + Enter**. Today we also create files: in Colab, the folder icon on the left shows the files of the session. They are **deleted when the session ends**, so download what you want to keep. If you prefer to work on your computer, Visual Studio Code with the Python extension works as well.

When something breaks, **read the error message** before asking for help: Part 3 shows how.

# Part 1: Python warm-up

Reminders: a string is a sequence of characters (`len(s)`, `s[0]`, `for c in s:`), `+` concatenates and `*` repeats (`"*" * 3` is `"***"`), `print()` alone prints an empty line. `input()` always returns a string. To change the elements of a list you need their index (`a[i] = ...`); `for x in a: x = x + 1` does **not** change `a`. A dictionary maps keys to values: `d["A"]`, `d["N"] = "N"`, `for key in d:`, `d.values()`, `"X" in d`.

## Exercise 1: histogram
Write a simple function that, given a list of numbers, outputs a histogram based on these numbers, using asterisks to draw it.

For example, given the list [3, 7, 9, 5], the function should produce this sequence:
```
***

*******

*********

*****
```
Hint: one `for` loop and the repetition `"*" * n`.

**Bonus:** `histogram(count_nucleotides(dna))`, with the function of Tutorial 1, draws the composition of a DNA string.

## Exercise 2: rövarspråket
In Sweden, children often play using a somewhat peculiar language called *rövarspråket*: it consists of doubling every consonant in a word and inserting an "o" in the middle. For example, the word 'mangiare' (to eat) becomes "momanongogiarore."

Write a function that can translate a word or phrase passed as input into *rövarspråket*. After translating a phrase, the program should ask the user if they want to translate another one, and if so, it should wait for the user to enter a new word.

Hint: for each character decide whether it is a consonant (a letter that is not a vowel) and append either `c + "o" + c` or `c` to the result; vowels and spaces are left alone. For the "another one?" part, use a `while` loop as in the bonus of Exercise 4 of Tutorial 1.

## Exercise 3: decrement a list
You are given a list that contains integers. You need to write a **function** that decrement each element of the list by 1 and return the list.

For example, `decrement([5, 3, 8])` returns `[4, 2, 7]`.

Write it twice: once modifying the list in place with `for i in range(len(a))`, once building a new list with `append`. Question: after `b = decrement(a)`, what is `a` in the two versions? Check with `print`.

## Exercise 4: sum of the values of a dictionary
The task of finding the sum of all items in a [dictionary](https://www.geeksforgeeks.org/python/python-dictionary/) in Python involves calculating the total of all values stored in a dictionary. **For example,** given a dictionary {'a': 100, 'b': 200, 'c': 300}, the sum of values would be 100 + 200 + 300 = 600.

Do it with a `for` loop, without calling `sum()`.

**Bonus:** rewrite `count_nucleotides(dna)` of Tutorial 1 so that it returns a dictionary, `{'A': 1, 'C': 2, 'G': 2, 'T': 1}` for `"ATGCGC"`; then the sum of its values must be `len(dna)`.

# Part 2: Files

So far the input of our programs was typed in the code or by the user. Real data comes in **files**: a genome in FASTA format, a table of measurements, the dataset of a Rosalind problem. A program reads its input from a file, computes, and writes the result to another file.

```python
with open("seqs.txt", "w") as f:   # "w": write (overwrites the file!)
    f.write("ATGCGC\n")
    f.write("GGATTA\n")

with open("seqs.txt", "r") as f:   # "r": read
    for line in f:                 # one line at a time
        dna = line.strip()         # remove the final "\n"
        print(dna, len(dna))
```

- `open(name, mode)` with mode `"r"` (read), `"w"` (write from scratch) or `"a"` (append at the end); `with ... as f:` closes the file automatically at the end of the block.
- A file is a sequence of lines, each ending with `"\n"`; `f.read()` gives the whole content as one string.
- A name like `"seqs.txt"` is looked up in the **current folder**: in Colab, the folder shown by the folder icon on the left (`/content`); on your computer, the folder from which you run the script.
- In Colab you can create a file directly from a cell: write `%%writefile film.csv` as the first line of the cell and the content of the file below it. Or use the upload button of the folder panel.

A **CSV** file (Comma-Separated Values) is a table as text: one row per line, columns separated by commas, usually a first line with the column names (the *header*). You could split each line on the commas yourself, but a value containing a comma would break everything: the `csv` module of the standard library handles those details.

## Exercise 5: CSV files in Python

In this tutorial, we see how to use Python to manage CSV files following an online tutorial.
1. Copy and save this snippet of code in a `.csv` file:
```csv
Title,Release Date,Director
And Now For Something Completely Different,1971,Ian MacNaughton
Monty Python And The Holy Grail,1975,Terry Gilliam and Terry Jones
Monty Python's Life Of Brian,1979,Terry Jones
Monty Python Live At The Hollywood Bowl,1982,Terry Hughes
Monty Python's The Meaning Of Life,1983,Terry Jones
```
2. Run the following examples on this newly saved `.csv` file (taken from this [tutorial](https://www.geeksforgeeks.org/working-csv-files-python/)) :

	a. Run this example reading the previous `.csv` file (`csv.reader`: every row is a **list** of strings)

```python
import csv

filename = "film.csv"

fields = []
rows = []


with open(filename, 'r') as csvfile:
    csvreader = csv.reader(csvfile)
    fields = next(csvreader)
    for row in csvreader:
        rows.append(row)
    print("Total no. of rows: %d" % (csvreader.line_num))

print('Field names are:' + ', '.join(field for field in fields))

print('\nFirst 5 rows are:\n')
for row in rows[:5]:
    for col in row:
        print("%10s" % col, end=" "),
    print('\n')
```

   b.  Run this other example reading the same `.csv` file (`csv.DictReader`: every row is a **dictionary** whose keys are the names in the header)
	
```python
import csv

with open('film.csv', mode='r') as file:
    csv_reader = csv.DictReader(file)
    data_list = []
    for row in csv_reader:
        data_list.append(row)

for data in data_list:
    print(data)

```

   c.  Run this example **writing** a `.csv` file (`csv.writer`: `writerow` takes a list and writes one line)

```python
import csv
fields = ['Name', 'Branch', 'Year', 'CGPA']
rows = [['Nikhil', 'COE', '2', '9.0'],
        ['Sanchit', 'COE', '2', '9.1'],
        ['Aditya', 'IT', '2', '9.3'],
        ['Sagar', 'SE', '1', '9.5'],
        ['Prateek', 'MCE', '3', '7.8'],
        ['Sahil', 'EP', '2', '9.1']]

filename = "university_records.csv"

with open(filename, 'w') as csvfile:
    csvwriter = csv.writer(csvfile)
    csvwriter.writerow(fields)
    csvwriter.writerows(rows)

``` 

   d. Create a Python script that reads from the previous `.csv` file and create a new one with the content below and create a third `.csv` file with the content of both the files, header included once (choose on the reading/writing technique from this tutorial)
	 
```csv
Title,Release Date,Director
Monty Python's Flying Circus - Series 1,1969-1970,Various Directors
Monty Python's Flying Circus - Series 2,1970-1971,Various Directors
Monty Python's Flying Circus - Series 3,1972-1973,Various Directors
Monty Python's Flying Circus - Series 4,1974,Various Directors
Monty Python Conquers America,2003,Frank Cvitanovich
Monty Python Live (Mostly),2014,Eric Idle
```

**Bonus:** with `DictReader`, print only the films whose director includes Terry Jones.

# Part 3: Errors and exceptions

When a program fails, Python prints a **traceback**:

```
Traceback (most recent call last):
  File "tb.py", line 5, in <module>
    print(third(F))
  File "tb.py", line 2, in third
    return F[3]
IndexError: list index out of range
```

Read it **from the bottom**: the last line says *what* went wrong (the type of error and a message); the lines above say *where* (the chain of calls, from the cell you ran down to the line that failed). The error is not always where the fix is: here `F` has 3 elements, so the bug may be in who called `third`.

The usual suspects:

| Error | Typical cause |
|---|---|
| `SyntaxError`, `IndentationError` | missing colon or bracket, wrong indentation (the program does not even start) |
| `NameError: name 'lenght' is not defined` | typo, or variable not yet assigned |
| `TypeError: can only concatenate str (not "int") to str` | mixing types, e.g. `"A" + 1` |
| `ValueError: invalid literal for int()` | `int("abc")` |
| `IndexError: list index out of range` | `a[len(a)]` |
| `KeyError: 'X'` | `d["X"]` when `"X"` is not a key of the dictionary |
| `ZeroDivisionError` | `x / 0` |
| `FileNotFoundError: No such file or directory` | wrong file name or wrong folder |
| `RecursionError: maximum recursion depth exceeded` | a recursive function with no base case (Part 4) |

An error is an **exception**: it is *raised* where it happens and travels up the chain of calls until someone *handles* it; if nobody does, the program stops with the traceback. To handle it, put the risky instructions in a `try` block and the recovery in an `except` block, one per type of error:

```python
try:
    n = int(input("How many? "))
    print(100 / n)
except ValueError:
    print("That is not an integer")
except ZeroDivisionError:
    print("n must be different from 0")
print("Done")        # reached in all three cases
```

With files, the most common error is a missing file: report it and go on, instead of crashing the whole analysis.

```python
def read_sequences(filename):
    seqs = []
    try:
        with open(filename, "r") as f:
            for line in f:
                seqs.append(line.strip())
    except FileNotFoundError:
        print("Cannot find", filename)
    return seqs            # [] if the file is missing
```

Handle only the errors you expect and let the others show the traceback: `except Exception as e: print(e)` catches everything, but hiding an error is worse than seeing it. You can also raise your own: `raise ValueError("not a nucleotide")`.

## Exercise 6: robust input and output
1. Write `ask_integer(prompt)` that asks the user for an integer and, until the user types a valid one, prints a message and asks again (catch `ValueError`). It returns the integer.
2. Write `load_rows(filename)` that returns the rows of a CSV file as a list of lists; if the file does not exist, print a message and return an empty list. Try it with `"film.csv"` and with a wrong name.
3. **Bonus:** `complement(base)` of Tutorial 1 with a dictionary `{"A": "T", "C": "G", "G": "C", "T": "A"}`: look up the base and return `"?"` when a `KeyError` is raised.

# Part 4: Recursion

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

# What's next

- Rosalind: solve a couple more problems from the first page (*Counting DNA Nucleotides*, *Complementing a Strand of DNA*). You already have the functions from Tutorial 1: now read the dataset from the file.
- Keep the cheat sheet of Tutorial 1 at hand and add to it: `with open(...)`, `csv.reader` / `csv.DictReader` / `csv.writer`, `try` / `except`, and the recipe for recursion (base case first, then the call on a smaller input).
