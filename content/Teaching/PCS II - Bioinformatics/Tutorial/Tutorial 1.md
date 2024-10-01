---
title: "Tutorial 1:  7-10-2024"
draft: true
---

# Visual Studio Code

The preliminary step of this tutorial requires to install [Visual Studio Code](https://code.visualstudio.com/docs).
1. We can install Visual Studio from this [web page](https://code.visualstudio.com/docs/setup/setup-overview)
2. We can handle `.py` files according to this [page](https://code.visualstudio.com/docs/languages/python). In this tutorial execute this [section](https://code.visualstudio.com/docs/languages/python#_run-python-code)
	1. Install [Jupyter Notebook](https://code.visualstudio.com/docs/languages/python#_jupyter-notebooks) plugin

Great! We are ready to move on to the next part of the tutorial.

# CSV files in Python

In this tutorial, we see how to use Python to manage CSV files following an online tutorial. 
1. Save this snippet of code in a `.csv` file:
```csv
Title,Release Date,Director
And Now For Something Completely Different,1971,Ian MacNaughton
Monty Python And The Holy Grail,1975,Terry Gilliam and Terry Jones
Monty Python's Life Of Brian,1979,Terry Jones
Monty Python Live At The Hollywood Bowl,1982,Terry Hughes
Monty Python's The Meaning Of Life,1983,Terry Jones
```
2. We execute part of this [tutorial](http://www.pythonforbeginners.com/systems-programming/using-the-csv-module-in-python/) on this newly saved `.csv` file:
	1. Run this example on reading a .csv file
		```python
import csv
 
ifile = open(‘test.csv’, “rb”)
reader = csv.reader(ifile)
 
rownum = 0
for row in reader:
# Save header row.
	if rownum ==0:
		header = row
	else:
		colnum = 0
	for col in row:
		print ‘%-8s: %s’ % (header[colnum], col)
	colnum + = 1
 
rownum + = 1
 
ifile.close()
```

	2. Run this example on writing a .csv file
		```python
import csv
 
ifile  = open('test.csv', "rb")
reader = csv.reader(ifile)
ofile  = open('ttest.csv', "wb")
writer = csv.writer(ofile, delimiter='', quotechar='"', quoting=csv.QUOTE_ALL)
 
for row in reader:
    writer.writerow(row)
 
ifile.close()
ofile.close()
``` 
# Pandas
