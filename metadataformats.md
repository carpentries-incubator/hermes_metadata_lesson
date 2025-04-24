---
title: "Collecting, Storing, Processing"
teaching: 20
exercises: 10
---

::: questions 

- In which formats can data and metadata be stored in a structured way?
- What is a CSV file and how is its content structured?

:::

::: objectives

- Knowledge of basics of CSV format for storing and processing metadata. 
- Familiar with the structure of a simple CSV file.
- Knowledge of the main difference between an xslx and a csv format.
   
:::

## Introduction to metadata file formats


::: challenge

### Question: 
Do you know formats in which data can be stored in a structured way? 

::: solution

### Show me the solution
An easy way to store data in a structured way is to use a spreadsheet such as Excel.

:::
:::


In order to store metadata and make it usable in other contexts, appropriate formats are required. The most common file formats used to store metadata are XML and JSON. A lot of data is also stored in the more familiar CSV format, as a real-world example will show later.


#### Interoperability


The advantage of using such a format is the interoperability of the data. This means that the data is collected and stored by one person and can be opened and processed elsewhere, e.g. extended or integrated into another system, i.e. it can be worked with. Data from different sources can also be merged.



::: challenge

### Challenge

Open the [artworksShort.csv file](https://github.com/HERMES-DKZ/metadata_lesson/blob/main/episodes/data/artworksShort.csv) and the [artworksShort.xslx file](https://github.com/HERMES-DKZ/metadata_lesson/blob/main/episodes/data/artworksShort.xlsx) in your favorite spreadsheet application. 

- What do you notice?    
- What form does the data take?    
- What are the advantages of recording data in tabular form?    
- Why is this data operable? 
    
::: solution

### Show me the solution

- Several parameters are queried when the csv file is opened.
- Some data in the xslx file is formatted with colours and bold and italic text. You won't find this in the csv file. 
- The data is in tabular form in a spreadsheet.
- The data is broken down into individual fields.
- Contents are named, data is labelled.
- The data is in a digital file format that can be edited and shared.
    
:::
:::

::: instructor
One possible source of errors and problems that may occur and should be discussed is the delimiters. A title with commas has been deliberately included in the file so that this title can be displayed across several fields if different separators are selected.
:::



## CSV files



The CSV (comma-separated values) format in this example is usually opened as a table in a spreadsheet so that it can be read by humans in a structured way. If you open the format in a text editor, you can see the structure of the file. 

```
ID;artist;title;date
1;Salvador Dalí;The persistence of memory;1931
2;Walker Evans;Allie Mae Burroughs, Wife of a Cotton Sharecropper, Hale County, Alabama;1936
3;Frida Kahlo;Roots;1943
4;Käthe Kollwitz;Mother with Child over her Shoulder;Before 1917
5;Berthe Morisot;The psyche mirror;1876
1;Georgia O’Keeffe;Sky above clouds IV;1965
3;Banksy;Girl with Ballon;2002
```

When you opened the csv file in a spreadsheet program, some parameters were queried before you could even open it. Here we can see why:

The data is separated by semicolons - the delimiters. Delimiter-separated files are often given a *.csv* extension, even if the field separator is not a comma, as the example shows. In many files you will find the contents of the data fields enclosed in quotation marks. Records are separated by a line break. The first line often defines the column headers. If these parameters are entered correctly when the file is opened, the data will be transferred to the appropriate fields in the spreadsheet.



## Difference between csv and xslx files



An xslx format allows you to store, format and apply formulas to data in multiple spreadsheets in a single file. Data is organised into cells, which are arranged in rows and columns. Both the cells and the data values can be formatted, including fonts, colours and borders. The data can be manipulated using built-in functions, e.g. for calculation or analysis. It is also possible to visualise the analysed data in spreadsheet software such as Excel. 

One of the disadvantages is the limited number of rows and columns (depending on the version, e.g. 1,048,576 rows and 16,385 columns per worksheet). Some features depend on the version of the software. Older tables may not always display correctly with the latest version due to lack of feature compatibility. 

The CSV (comma-separated values) format stores tabular data in plain text that can be opened in spreadsheet software. It is therefore both human and machine readable. There is always only one table. However, the plain text format allows more data to be stored, making it particularly efficient as it does not store superfluous data such as formatting data. It is therefore suitable for storing and exchanging data between applications or databases. 

One of its disadvantages is that it can only store simple tabular data, not more complex structures. As the example above shows, certain characters need to be escaped, making it sensitive to errors.



#### Data Organization



When entering data into spreadsheets, there are a number of issues that need to be considered to ensure that the data can be processed correctly. In addition to the comma-separated fields mentioned above, which can cause problems, there are many other issues. Dates or names are a major source of error. Different spellings can lead to misinterpretation. How do you interpret the date 25-01-11 if it is written in a single field? Which part of a name is the first name and which part is the surname of a person?

::: callout

### Find out more on Data Organization

For further reading see e.g., [Data Organization in Spreadsheets for Social Scientists](https://datacarpentry.github.io/spreadsheets-socialsci/)

:::


An important part of recording metadata is annotating the data. Labelling categories for people, such as artist or photographer for Walker Evans, helps to understand the content. This tagging allows the data to be interpreted and is used differently depending on the format. In the spreadsheet example, it is the column heading. If you are using a spreadsheet to annotate dates, it may be worth splitting the year, month and day into separate fields to avoid the problems described above. Later you will learn about other ways to display dates correctly.  

Choosing a different format can help avoid some of these difficulties. One way is to use a markup language. Based on the SGML meta-language, which contains the basic concepts of markup languages, such as elements and attributes, and the rules for using them, markup languages are used to structure and format text and data in a machine-readable way.  

::: keypoints

* Use an xslx format to store and analyse the data and if you need to format the data and spreadsheet.
* Use an interoperable format such as csv to store or share data and if you don't need to analyse or visualise the data with the application.
* Marking up the data with headers, for example, is helpful.
* Be aware of the problems that data and metadata can cause when you annotate them, for example with dates or names.

:::
