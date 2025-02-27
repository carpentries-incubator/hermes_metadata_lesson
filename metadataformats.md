---
title: "Introduction to Metadata File Formats"
teaching: 20
exercises: 1
---

::: questions 

- In which formats can data and metadata be stored in a structured way?
- What is a CSV file and how is its content structured?

:::

::: objectives

- Knowledge of basics of CSV format for storing and processing metadata. 
- Familiar with the structure of a simple CSV file.
- Knowledge of the main difference between a xslx and a csv format.
   
:::

## Introduction

::: challenge

### Question: 
Do you know formats in which data can be stored in a structured way? 

::: solution

### Show me the solution
A simple way to store data in a structured way is using a spreadsheet like Excel. 

:::
:::

In order to store metadata and make it usable in other contexts, appropriate formats are required. The most common file formats in which metadata is stored include XML and JSON. A lot of data is also stored in the more familiar CSV format as a real-life example will show later.

The advantage of using such a format is the interoperability of the data. This means that the data is recorded and stored by one person and can be opened and processed elsewhere, for example extended or integrated into another system, i.e. it can be operated with. Data from different sources can also be merged. 

::: challenge

## Challenge

Open the artworks.csv file in your favorite spreadsheet application. 
    * What do you notice?    
    * What form does the data take?    
    * What are the advantages of recording data in tabular form?    
    * Why is this data operable? 
    
::: solution

## Show me the solution

    * Various parameters are queried when opening.
    * The data is in a tabular form in a spreadsheet available.
    * The data is structured into individual fields.
    * Content is named, data is labled/marked up.
    * The data is available in a digital file format that can be processed and shared.
    
:::
:::

::: instructor
Possible sources of error and problems that can occur and should be discussed are the separators. A title with commas was intentionally built into the file so that this title can be displayed across several fields when different separators are selected. There may also be some discussion about whether the names should be in two separate fields. 
:::

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

Whereas with an xslx format, data can be saved, formatted and provided with formulas in several spreadsheets, the CSV (comma-separated values) format stores tabular data in plain text. 

When you opened the file in the last exercise, some parameters were queried before you could even open it. Here we can see why:

The data is separated by semicolons - the delimiters. Delimiter-separated files are often given a *.csv* extension even when the field separator is not a comma as the example demonstrate. In many files you may find the contents of the data fields enclosed in quotes. Individual records are separated by a line break. The first line often defines the column headings. If these parameters are entered correctly when the file is opened, the data is transferred to the appropriate fields in the spreadsheet. 

When entering data into spreadsheets, there are a number of issues to consider to ensure that the data can be processed correctly. In addition to the comma-separated fields mentioned above, which can cause problems, there are many more aspects. Dates are a major source of error. Different spellings can lead to misinterpretation. How do you interpret the date 25-01-11 when it is written in a single field?

::: callout

## Find out more on Data Organization

For further reading see e.g., [Data Organization in Spreadsheets for Social Scientists](https://datacarpentry.github.io/spreadsheets-socialsci/)

:::

An important part of recording metadata is annotating the data. Labelling categories for people, such as artist or photographer for Walker Evans, helps to understand the content. This marking allows the data to be interpreted and is used differently depending on the format. In the spreadsheet example it is the column heading. When using a spreadsheet to annotate, for dates, it can be worth splitting the year, month and day into separate fields to avoid the problems described above. Later, you will learn about other ways to display dates correctly.  

Choosing a different format can help to avoid some of these difficulties. One option is to use a markup language. Based on the SGML meta-language, which contains the basic concepts of markup languages, such as elements and attributes, and the rules for their use, the various markup languages are used to structure and format text and data in a machine-readable way.

::: keypoints

To annotate data and metadata is it best to:

* mark up the data with for exmaple headers
* use a format which is interoperable like csv
* be aware of the problems the data and metadata can cause when annotating them, e.g., the dates or labels

:::


