---
title: Home page
---
--- start-multi-column: ExampleRegion1  
```column-settings  
number of columns: 2  
Border: disabled
Shadow: disabled
largest column: right
```

![[Pasted image 20240927161403.png]] 

--- end-column ---

Hi all, I am Marco Zecchini.

I am a Research Assistant [Department of Computer, Control and Management Engineering (DIAG)](https://www.dis.uniroma1.it/) of [Sapienza University of Rome](https://www.uniroma1.it/it/pagina-strutturale/home).

My research interests are Cryptography and Blockchain technology.

--- end-multi-column
# Publications


```dataviewjs
for (let group of dv.pages("#book").where(p => p["time-read"].year == 2021).groupBy(p => p.genre)) {
	dv.header(3, group.key);
	dv.table(["Name", "Time Read", "Rating"],
		group.rows
			.sort(k => k.rating, 'desc')
			.map(k => [k.file.link, k["time-read"], k.rating]))
}
```



# Prior Roles

* [01/2023 - 08/2024] **PostDoc Researcher** at University of Salerno under the supervision of Prof. Ivan Visconti.

* [04/2022 - 09/2022] **Visitor Researcher at TUHH** at the CDL-BOT laboratory ran by Prof. Stefan Schulte.

- [11/2019 - 01/2023] **Ph.D. Candidate in Data Science** at the Department of Computer, Control, and Management Engineering of Sapienza University of Rome under the supervision of Prof. Andrea Vitaletti.

# Education

* [11/2019 - 01/2023] **PhD In Data Science** at the Department of Computer, Control, and Management Engineering of Sapienza University of Rome 

- [09/2016 - 10/2018] **MSc in Computer Engineering** at Sapienza University of Rome.
    
- [09/2013 - 10/2016] **BSc in Computer Engineering** at Sapienza University of Rome.
    
- [09/2008 - 07/2013] **Scientific High School** at Liceo Scientifico Talete.