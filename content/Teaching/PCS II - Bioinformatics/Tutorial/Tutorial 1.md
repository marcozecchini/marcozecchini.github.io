---
title: "Tutorial 1:  7-10-2024"
draft: false
---
* Live notes about this first tutorial are available at this [link](https://docs.google.com/document/d/1MBCTsjYI_eCjCSZ8cmHlO3uz6LQUrWdAxeYsSKl18z0/edit?usp=sharing)
# Visual Studio Code

The preliminary step of this tutorial requires to install [Visual Studio Code](https://code.visualstudio.com/docs).
1. We can install Visual Studio from this [web page](https://code.visualstudio.com/docs/setup/setup-overview)
2. We can handle `.py` files according to this [page](https://code.visualstudio.com/docs/languages/python). In this tutorial execute this [section](https://code.visualstudio.com/docs/languages/python#_run-python-code)
	1. Install [Jupyter Notebook](https://code.visualstudio.com/docs/languages/python#_jupyter-notebooks) plugin
3. Create an empty folder for our exercises and open it with `File > Open File...` menu on Visual Studio

Great! We are ready to move on to the next part of the tutorial.

# CSV files in Python

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
2. Execute part of this [tutorial](https://www.geeksforgeeks.org/working-csv-files-python/) on this newly saved `.csv` file:

	a. Run this example reading the previous `.csv` file

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

   b.  Run this other example reading the same `.csv` file
	
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

   c.  Run this example **writing** a `.csv` file

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

   d. Create a Python script that reads from the previous `.csv` file and a new one with the content below and create a third `.csv` file with the content of both the files (choose on the reading/writing technique from this tutorial)
	 
```csv
Title,Release Date,Director
Monty Python's Flying Circus - Series 1,1969-1970,Various Directors
Monty Python's Flying Circus - Series 2,1970-1971,Various Directors
Monty Python's Flying Circus - Series 3,1972-1973,Various Directors
Monty Python's Flying Circus - Series 4,1974,Various Directors
Monty Python Conquers America,2003,Frank Cvitanovich
Monty Python Live (Mostly),2014,Eric Idle
```

# Pandas
A smarter and more abstract tool to handle `.csv` files is another Python tool named [Pandas](https://pandas.pydata.org/)

We use Pandas to:
1. **Manipulate** data. 
2. **Visualize and plot** data combined with [matplotlib](https://matplotlib.org/) library

## Install Pandas and Matplotlib
Install pandas following the instruction available at this [web page](https://pandas.pydata.org/docs/getting_started/install.html#installing-from-pypi).

Install matplotlib following the instruction available at this [web page](https://matplotlib.org/stable/users/getting_started/). 
## Manipulate and Visualize data
Let us take a look at this [presentation](https://docs.google.com/presentation/d/1qZ45rL9kzti_z2yL2EYs8TFFDsCBBY6V/edit?usp=sharing&ouid=113320648382378755454&rtpof=true&sd=true).

**Keeping Pandas API Documentation at hand with this [link](https://pandas.pydata.org/docs/reference/index.html)**, let us see Pandas in action now:
1. Create a file named `ManipulateVisualize.ipynb`
2. Run the Jupiter Notebook in Visual Studio Code ([more details here](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)) on the `.csv` dataset [Salary Data.csv](https://drive.google.com/file/d/1jxSWVRcQ4MC_rHYZFEYnjmei9Fe9p4w2/view?usp=sharing)
3. Follow and repeat my instructions on your Jupiter!

## Exercises

Complete this [exercise on Jupiter Notebook](https://drive.google.com/file/d/1P9mARbmxR9l9OwTwOUovRcLccQjnndYq/view?usp=drive_link) on the same dataset.