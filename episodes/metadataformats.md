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



## 3 XML Schema

In the humanities in particular, there are standards for annotating data in XML. This ensures that data is available in a standardised form and is therefore interoperable. In XML, this is done by creating a schema. An XML Schema describes the structure of an XML document and establishes rules for annotating its content. The structure is essentially the same as XML. A schema is stored in the .xsd (XML Schema Definition) file format. It is characterised by the use of xs:schema as the container element for the whole document. Xs denotes the namespace for the schema (remember not to use : in XML tags, it is reserved for that!) 

```xsd
<xs:schema>

</xs:schema>
```
A simple XML element is defined in the schema by the specification xs:element and the attributes name and type. Additional attributes may be set.

```xsd
<xs:element name=“descriptive name“ type=“string“>
```
For example, we can specify that a place is always called place and that the character type of the content is a string. This specification prevents the tag from being sometimes called place, sometimes location or even city: 
```xsd
<xs:element name=“place“ type=“string“/>
```
This defines the \<place\> XML tag such as \<place\>New York\</place\>. 

::: callout

## String

In computing, a string is a data type that contains a string of characters of fixed or variable length. It is mainly used to store words, sentences and whole texts. Other data types, for example for numbers, are integer or float. This specifies whether whole numbers or floating point numbers are allowed. 
:::

Content restrictions can be set using facets:
```xsd
<xs:element name="age">
  <xs:simpleType>
    <xs:restriction base="xs:integer">
      <xs:minInclusive value="0"/>
      <xs:maxInclusive value="120"/>
    </xs:restriction>
  </xs:simpleType>
</xs:element>
```
With these restrictions, only values from 0 to 120 are allowed in the XML. 

A simple element contains only one piece of information. No other elements can be nested within it, nor can content information be stored in attributes. To assign attributes to a tag in XML, this is also defined in the schema:
```xsd
<xs:attribute name="lang" type="string" default=“EN“/>
```
In the example above an attribute for the language is defined. In the absence of a specified language, 'English' is assumed as the default value. The attribute is specified with a fixed value, thus allowing for the specification of 'English' as the only permitted language. It should be noted that all attributes are optional by default when creating the XML element, unless the attribute is specified as \<tag use=“required“\>. 

A complexType is used to provide further information and specifications for the definition of a content:
``` xsd
<xs:element name=“employee“>
	<xsd:complexType name="PersonTyp" abstract="true"> 
		<xsd:sequence> 
			<xsd:element name="Vorname" type="xsd:string" maxOccurs="3"/> 
			<xsd:element name="Name" type="xsd:string"/> 
			<xsd:element name="Geburtsdatum" type="xsd:date"/> 
		</xsd:sequence> 
	</xsd:complexType> 
</xsd:element>
```
This schema is proposed for the definition of an employee. It is imperative that the XML data comprises the subject's first name, name and date of birth. The employment of the \<xsd:sequence\> element stipulates that the data must be entered in the sequence delineated herein. This particular tag is designated as an 'indicator'. Note that there are other indicators that regulate various aspects, including the number of occurrences permitted for elements, the designation of elements as mandatory, and other related parameters. Other forms of elements are available to regulate the structure of an XML schema. An XML that conforms to a schema is called valid. 

::: callout

## Reference

You can find tutorials on XML and XSD as well as the follwing topic on the webdevelopment portal [W3Schools](https://www.w3schools.com/). The tutorials have a built-in text editor, and people can try out the examples directly on the web page.
:::

## 4 JSON

Another format in which metadata can be stored, annotated and exchanged is JSON (JavaScript Object Notation). Its syntax is inspired by JavaScript object notation. 

::: keypoints

## JSON keypoints

* (Meta)data elements are defined in key/value pairs.
* Keys are of data type string (in quotes).
* Values must be of data type string, number (float or integer), boolean, array or object.
* Elements are separated by commas.
* Curly braces hold objects.
* Square brackets hold arrays.
* In-line commenting is not supported.
:::

#### JSON Data

JSON data is written as key/value pairs. A key/value pair consists of a key, followed by a colon, followed by a value. The key is the name – the label – for the content in the value field. Keys are always written in double quotes. The indication of the value depends on its data type. The entire content is enclosed in curly brackets. 

```JSON
{„name“ : „Kim Sneider“,
„age“ : 39,
„children“ : [„Ben“, „Tove“, „Nina“]
}
```

#### JSON vs XML

* Both are human and machine readable.
* Both can be structured hierarchical (values within values).
* Both can be parsed and used by lots of programming languages.

**But**
JSON is shorter than XML and in data processing easier to use. JSON can use arrays, so that a set of multiple values can be stored and processed easily within one key but interpreted as multiple values. Whereas in XML multiple values can be written in one tag, but they will not be processed like that as the content of a tag is not interpreted as multiple values even if the data is separated with a comma or other characters. 

#### Values

Values cannot be one of the following data types:

* a function
* a date (dates are written as strings in double quotes – so be aware of problems that may cause) 
* undefined

::: callout 

### Boolean

Boolean is the data type for truth values in programming languages. The Boolean data type can be either true (the binary equivalent of 1) or false (the binary equivalent of 0). Programmers use Booleans to test conditions.
::: 

| data type | explanation | example as JSON value |
| ---- | ---- | ---- | ---- |
| string | set of character | „Can be a sentence or a name or a date and is written in double quotes“ |
| integer | whole number | 12 |
| float | floating-point number | 3.5 |
| boolean | truth value | true/false |
| array | collection of values | [„Didi“, 35, „Whatever“, true] |
| JSON object | a set of JSON data | {„name“ : „Kim“, „age“ : 39} |


