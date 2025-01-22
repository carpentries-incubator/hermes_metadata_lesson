---
title: "Metadata formats"
teaching: 120
exercises: 5
---

::: questions 

- In which formats can data and metadata be stored in a structured way?
- What is a CSV file and how is its content structured?
- How do you annotate data in XML and JSON?
- What is a schema and why is it helpful?

:::

::: objectives

- Knowledge of CSV, XML & JSON formats for storing and processing metadata. 
- Familiar with the structure of a simple CSV, XML and JSON file. 
- Able to write extracted metadata in a simple XML and JSON format. 
:::

## 1 Introduction

::: challenge

### Question: 
Do you know formats in which data can be stored in a structured way? 

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

When you opened the file in the last exercise, some parameters were queried before you could even open it. Here we can see why:

The data is separated by delimiters - usually commas or semicolons. The contents of the data fields can be enclosed in quotes. If these parameters are entered correctly when the file is opened, the data is transferred to the appropriate fields in the spreadsheet. The first line often defines the column headings. Individual records are separated by a line break.

When entering data into spreadsheets, there are a number of issues to consider to ensure that the data can be processed correctly. In addition to the comma-separated fields mentioned above, which can cause problems, there are many more aspects. Another source of error can be unintentional blank characters, usually at the end of an entry. These need to be considered separately during automated processing. Dates are another major source of error. Different spellings can lead to misinterpretation. How do you interpret the date 25-01-11 when it is written in a single field?

::: callout

## Find out more on Data Organization

For further reading see e.g., [Data Organization in Spreadsheets for Social Scientists](https://datacarpentry.github.io/spreadsheets-socialsci/)

:::

An important part of recording metadata is annotating the data. Labelling categories for people, such as artist or photographer for Walker Evans, helps to understand the content. This marking allows the data to be interpreted and is used differently depending on the format. In the spreadsheet example it is the column heading. For dates, it is worth splitting the year, month and day into separate fields to avoid the problems described above. 

Choosing a different format can help to avoid some of these difficulties. One option is to use a markup language. Based on the SGML meta-language, which contains the basic concepts of markup languages, such as elements and attributes, and the rules for their use, the various markup languages are used to structure and format text and data in a machine-readable way.


## 2 XML

One of the most widely used metadata formats in the cultural sector is XML (eXtensible Markup Language). It is used to describe, structure, hierarchise (if desired), store and transport data. XML refers to the file format and structure in which data is recorded. 

#### XML elements

An XML document contains XML elements to structure the data. They are formed using angle brackets and are divided into an opening tag and a closing tag, indicated by a leading slash. The content is placed in between. 

```xml
<tag>element</tag>
```

The tags are given a name that describes the content:

```xml
<photographer>Walker Evans</photographer> 
<name>Walker Evans</name>
<artist>Walker Evans</artist>
```

You may be familiar with this structure. The HTML language, which is used to organize web pages, has a similar structure. It is also based on SGML. HTML makes it possible to mark up the typical elements of a text-oriented document - such as headings, paragraphs, lists, or tables - as such on a web page and to structure the page semantically. 

::: callout

## Semantics

Semantics examines the meaning of characters such as words, phrases, or symbols. Semantically correct HTML gives meaning to content.
:::

Unlike HTML, where there are rules for naming tags - such as \<h1\>\</h1\> for heading - XML tags can be named freely, except for a few technical rules. This makes it particularly interesting for use in the development of metadata standards and ontologies.

::: callout

## Metadata Standards and Ontologies

Metadata standards are rules for how research data should be annotated, described, and stored in a format. For example, they specify the naming of tags if the data is stored in XML. They also govern the hierarchy of data or the relationships between data. More on this later. 

Ontologies are linguistically and formally organized representations of concepts and the relationships between them in a given domain. In the cultural heritage field in particular, they specify the presentation of object data so that it can be placed in larger contexts. Ontologies are used to model and standardize information. 
:::

XML also provides the ability to have comments that are not automatically read:

```xml
<!-- Here is the content of the comment, there is no closing tag -- >
```

#### Rules for naming tags^[1]

Names:

* Must start with a letter or underscore. 
* Cannot start with the letters xml (or XML, or Xml, etc). 
* Can contain letters, digits, hyphens, underscores, and periods. 
* Cannot contain spaces.

Best Naming Practices:

* Create descriptive names.
* Create short and simple names.
* Avoid - / . / : in the names, e.g. \<first-name\>, and be aware that : is reserved for namespaces which have a special function.

In XML, all elements must be properly nested within each other, which means that an element opened inside another element must be closed inside too:

```xml
<collection><place>collection of the MET in New York</place></collection>
```

#### Attributes

In XML, as in HTML, tags can also be assigned attributes, which define the content of the tags in more detail. They are named and the content is assigned to them with a = and enclosed in quotes:

```xml
<title lang="author's original language">Always give the title in the author's language</title>

<commonTitle lang="title as commonly known">Always give the title as it is commonly known</commonTitle>
```

There are some rules for characters used in XML for structure. They are replaced by a special character string, so that it won’t cause problems if, for example, you want to use a < in the content. This would cause an error because XML expects a closing tag. To avoid errors, the character is replaced with an entity reference: 

| string | character | meaning | 
| ---- | ---- | ---- | ----|
| \&lt; | < | less than |
| \&gt; | > | greater than |
| \&amp; | & | ampersand |
| \&apos; | ' | apostrophe |
| \&quot; | " | quotation mark |

Attributes are also frequently used in a hierarchy to record information that applies to all underlying data:

```xml
<items collection="archives_collection" place="location">
	<item1/>
	<item2/>
</items>
```

However, it should be noted that the information contained in the attributes is more likely to be seen as metadata related to the content. In this example, it may be worth creating the information about the collection and its location as separate tags above the items.

```xml
<collection place="New York">
	<item1/>
	<item2/>
</collection>

<place>
	<collection>
		<item1/>
		<item2/>
	</collection>
</place>
```

The indentation (using a tab) describes the hierarchy level. The collection is assigned to the location, and the items below it are on the same hierarchy level. The structure depends on the purpose of the collection and the data to be collected. 

The slash here at the end of the tag (self-closing tag) means that the element is empty and self-contained.

::: callout
In HTML, attributes often contain style information, such as the font color or the size and width of a section. This is also where the alt tag is created, which contains an alternative text to an image that is automatically read or displayed if the image cannot be retrieved:

```html
<p style="color:blue;" width="300" height="500">This is a blue paragraph.</p>
<img src="image.jpg" alt="a girl with a pearl earring is standing in front of a house"></image>
```
:::

At the top of an XML document you will often find something called a prolog:

```xml
<?xml version="1.0" encoding="UTF-8"?>
```

It is optional, but provides information about the version and encoding used, and must be at the top if included. 

::: callout
XML documents that conform to this syntax rules are said to be "Well Formed" XML documents.
::: 

::: callout

## Encoding

In data processing, characters are encoded with a numerical value for transmission or storage (!Remember the rules for character we have just learned). Character encoding allows characters and symbols to be uniquely assigned within a character set. There are different character encodings, so it is important to know which one is being used. For example, the German Ü may be encoded with the decimal value 220 in one character set, while the same value in another character set encodes the curly bracket. To ensure that the data is displayed correctly when used, the form of encoding has to be specified. UTF-8 and UTF-16 are among the most common character sets you may encounter when processing data.
:::

::: challenge

## Exercise

Open the xxxx.csv file. Use the given data and write it in an XML format. 

::: hint

* Think about the headings in the spreadsheet. Do you agree with this labelling? 
*  You can use tabs to create a hierarchy.
  
::: solution

Here to place a xml code block with 1 or 2 examples and the note that there is not one right solution

:::
:::
:::


::: discussion

## Discussion

Compare your XML with the documents of the other participants. What do you notice?

:::
 


## 3 XML Schema




[¹]: <https://www.w3schools.com/xml/xml_elements.asp>  
