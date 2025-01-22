---
title: "Metadata formats"
teaching: 120
exercises: 5
---

:::::::::::::::::::::::::::::::::::::: questions 

- In which formats can data and metadata be stored in a structured way?
- How do you annotate data in XML and JSON?
- What is a schema for XML or JSON?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Knowledge of CSV, XML & JSON formats for storing and processing metadata. 
- Familiar with the structure of a simple CSV, XML and JSON file. 
- Able to write extracted metadata in a simple XML and JSON format. 
::::::::::::::::::::::::::::::::::::::::::::::::

## 1 Introduction

:::::::::::::::::::::::::::::::::::::: questions 

- What is a CSV file and how is its content structured? 

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Familiar with a simple way of structured recording and storage of data and metadata.
::::::::::::::::::::::::::::::::::::::::::::::::

::: challenge

### Question: Do you know formats in which data can be stored in a structured way? 

::: solution

### Show me the solution
A simple way to store data in a structured way is using a spreadsheet like Excel. 
:::
:::

In order to store metadata and make it usable in other contexts, appropriate formats are required. The most common file formats in which metadata is stored include XML and JSON. A lot of data is also stored in the more familiar CSV format. 

The advantage of using such a format is the interoperability of the data. This means that the data is recorded and stored by one person and can be opened and processed elsewhere, for example extended or integrated into another system, i.e. it can be operated with. Data from different sources can also be merged. 

::: challenge

## Challenge

Open the artworks.csv file. 
    - What do you notice? 
    - What form does the data take? 
    - What are the advantages of recording data in tabular form? 
    - Why is this data operable? 
::: solution

## Show me the solution

    - Various parameters are queried when opening.
    - The data is in a tabular form in a spreadsheet available.
    - The data is structured into individual fields.
    - Content is named, data is labled/marked up.
    - The data is available in a digital file format that can be processed and shared.
:::
:::

::: instructor
Possible sources of error and problems that can occur and should be discussed are the separators. A title with commas was intentionally built into the file so that this title can be displayed across several fields when different separators are selected. There may also be some discussion about whether the names should be in two separate fields. 
:::

The CSV (comma-separated values) format in this example is usually opened as a table in a spreadsheet so that it can be read by humans in a structured way. If you open the format in a text editor, you can see the structure of the file. 

'''
ID;artist;title;date
1;Salvador Dalí;The persistence of memory;1931
2;Walker Evans;Allie Mae Burroughs, Wife of a Cotton Sharecropper, Hale County, Alabama;1936
3;Frida Kahlo;Roots;1943
4;Käthe Kollwitz;Mother with Child over her Shoulder;Before 1917
5;Berthe Morisot;The psyche mirror;1876
1;Georgia O’Keeffe;Sky above clouds IV;1965
3;Banksy;Girl with Ballon;2002
'''

When you opened the file in the last exercise, some parameters were queried before you could even open it. Here we can see why:

The data is separated by delimiters - usually commas or semicolons. The contents of the data fields can be enclosed in quotes. If these parameters are entered correctly when the file is opened, the data is transferred to the appropriate fields in the spreadsheet. The first line often defines the column headings. Individual records are separated by a line break.

When entering data into spreadsheets, there are a number of issues to consider to ensure that the data can be processed correctly. In addition to the comma-separated fields mentioned above, which can cause problems, there are many more aspects. Another source of error can be unintentional blank characters, usually at the end of an entry. These need to be considered separately during automated processing. Dates are another major source of error. Different spellings can lead to misinterpretation. How do you interpret the date 25-01-11 when it is written in a single field?

::: information
For further reading see e.g., [Data Organization in Spreadsheets for Social Scientists[(https://datacarpentry.github.io/spreadsheets-socialsci/)
:::

An important part of recording metadata is annotating the data. Labelling categories for people, such as artist or photographer for Walker Evans, helps to understand the content. This marking allows the data to be interpreted and is used differently depending on the format. In the spreadsheet example it is the column heading. For dates, it is worth splitting the year, month and day into separate fields to avoid the problems described above. 

Choosing a different format can help to avoid some of these difficulties. One option is to use a markup language. Based on the SGML meta-language, which contains the basic concepts of markup languages, such as elements and attributes, and the rules for their use, the various markup languages are used to structure and format text and data in a machine-readable way.


## 2 XML

One of the most widely used metadata formats in the cultural sector is XML (eXtensible Markup Language). It is used to describe, structure, hierarchise (if desired), store and transport data. XML refers to the file format and structure in which data is recorded. 

#### XML elements

An XML document contains XML elements to structure the data. They are formed using angle brackets and are divided into an opening tag and a closing tag, indicated by a leading slash. The content is placed in between. 

'''
<tag>element</tag>
'''
The tags are given a name that describes the content:
'''
<photographer>Walker Evans</photographer> 
<name>Walker Evans</name>
<artist>Walker Evans</artist>
'''
You may be familiar with this structure. The HTML language, which is used to organize web pages, has a similar structure. It is also based on SGML. HTML makes it possible to mark up the typical elements of a text-oriented document - such as headings, paragraphs, lists, or tables - as such on a web page and to structure the page semantically. 

## 3 XML Schema
