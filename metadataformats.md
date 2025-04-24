---
title: "Collecting, Storing and Processing Metadata"
teaching: 20
exercises: 10
---

::: questions 

- In which formats can data and metadata be stored in a structured way?
- What is a CSV file and how is its content structured?

:::

::: objectives

- Learn basics of the CSV format for storing and processing metadata. 
- Get familiar with the structure of a simple CSV file.
- Learn the main difference between the XSLX and CSV formats.
   
:::

## Introduction to metadata file formats


::: challenge

### Question: 
Do you know the formats in which data can be stored in a structured way? 

::: solution

### Show me the solution
An easy way to store data in a structured way is to use a spreadsheet such as Excel.

:::
:::


In order to store metadata and make it usable in other contexts, appropriate formats are required. The most common file formats used to store metadata are XML and JSON. A lot of data is also stored in the more familiar CSV format, as a real-world example will show later.


#### Interoperability


The advantage of using such a format is the interoperability of the data. This means that the data is collected and stored by one person, but can be opened, processed or merged with other data elsewhere. 



::: challenge

### Challenge

Open the [artworksShort.csv file](https://github.com/HERMES-DKZ/metadata_lesson/blob/main/episodes/data/artworksShort.csv) and the [artworksShort.xslx file](https://github.com/HERMES-DKZ/metadata_lesson/blob/main/episodes/data/artworksShort.xlsx) in your favorite spreadsheet application. 

- What do you notice?    
- What form does the data have?    
- What are the advantages of recording data in tabular format?    
- Why is this data ineroperable? 
    
::: solution

- Several parameters are queried when the CSV file is opened.
- Some data in the XSLX file is formatted with colours and bold and italic text. You won't find this in the CSV file. 
- The data in a spreadsheet is in tabular form.
- The data is broken down into individual fields.
- Contents are named and labelled through the column names. 
- The data is in a digital file format that can be edited and shared.
    
:::
:::

::: instructor
One possible source of errors and problems that may occur and should be discussed is the delimiters. A title with commas has been deliberately included in the file so that this title can be displayed across several fields if different separators are selected.
:::



## CSV files



The CSV (comma-separated values) format in this example is usually opened as a table in a spreadsheet so that it can be read by humans in a structured way. If you open the format in a text editor, you can see the structure of the file: 

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

As you opened the CSV file in a spreadsheet program, some parameters were queried before you could open it. Here's the reason why:

The data in this particular CSV file is separated by semicolons - the delimiters. Delimiter-separated files are often given a *.csv* extension, even if the field separator is not a comma, as the example shows. In many files you will find the contents of the data fields enclosed in quotation marks. Records are separated by a line break. The first line often defines the column headers. If these parameters are entered correctly when the file is opened, the data will be transferred to the appropriate fields in the spreadsheet.



## The Difference between CSV and XSLX files



An XSLX format allows you to store, format and apply formulas to data in multiple spreadsheets that are stored in a single file. Data is organised into cells, which are arranged in rows and columns. Both the cells and the data values within them can be formatted, including fonts, colours and borders. The data can be manipulated using built-in functions, e.g. for calculation or analysis. It is also possible to visualise the analysed data in spreadsheet software such as Excel. 

One of the disadvantages is the limited number of rows and columns - for example 1,048,576 rows and 16,385 columns per worksheet depending on your software version. Other features can depend on the software version as well. Older tables may not always display correctly with the latest version due to a lack of feature compatibility. 

The CSV (comma-separated values) format stores tabular data in plain text that can be opened in spreadsheet software. It is therefore readable by both humans and machines. There is always only one table stored in a single file. However, the plain text format allows more data to be stored in a file, making it particularly efficient as it does not store superfluous data such as formatting data. It is therefore suitable for storing and exchanging data between applications or databases. 

One of its disadvantages is that it can only store simple tabular data, and not data with more complex structures. As the example above shows, **certain characters need to be escaped** <span style="color:red">what do you mean? </span>, making it sensitive to errors.



#### Data Organization



When entering data into spreadsheets, there are a number of issues that need to be considered to ensure that the data can be processed correctly. In addition to the comma-separated fields mentioned above, which can cause problems, there are many other issues. Dates or names are a major source of error. Different spellings can lead to misinterpretation. For example, how do you interpret the date 25-01-11 if it is written in a single field? Or: Which part of a person's name is the first name and which part is the surname?

::: callout

### Learn more about Data Organization

For further reading see [Data Organization in Spreadsheets for Social Scientists](https://datacarpentry.github.io/spreadsheets-socialsci/).

:::


An important part of recording metadata is annotating the data. Take *Walker Evans* as an example: Annotating - i.e. tagging - him as "artist" or "photographer" allows users to understand the role of this entry in the context of the dataset. In the spreadsheet example, "artist" is one of the column headings. 

If you are using a spreadsheet to annotate dates, it may be worth splitting the year, month and day into separate fields to avoid the problem described above. Later you will learn about other ways to display dates correctly.  

There are certain data formats that solve some of the problems mentioned here - for example data created with a markup language. Markup languages are used to structure and format text and data in a machine-readable way. They are based on a meta-language called SGML. SGML is a standard for markup languages. It specifies how to define the syntax (rules) for elements, attributes, and document structure in a markup language.

::: keypoints

* If you need to format the data and spreadsheet, use the XSLX format to store and analyse the data.
* If you don't need to analyse or visualise the data using the software that opens it, use an interoperable format such as CSV to store or share the data.
* It is helpful to annotate the data - for example with headers.
* Be aware of the problems that can occur when annotating data and metadata with, for example, dates or names.

:::
