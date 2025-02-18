---
title: "XML and XML schema"
teaching: 60
exercises: 2
---

::: questions 

- What is XML? 
- How do you annotate data in XML?
- What is a XML schema?

:::

::: objectives

- Knowledge of XML format for storing and processing metadata. 
- Familiar with the structure of a simple XML file. 
- Able to write extracted metadata in a simple XML format.
- Knowledge of a XML schema ans its elements. 
:::

## XML

One of the most widely used metadata formats in the cultural sector is XML (eXtensible Markup Language). It is used to describe, structure, hierarchise (if desired), store and transport data. XML refers to the file format and structure in which data is recorded. 

### XML elements

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

### Rules for naming tags^[1]

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

### Attributes

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

:::
  
::: solution

Here to place a xml code block with 1 or 2 examples and the note that there is not one right solution

:::
:::


::: discussion

## Discussion

Compare your XML with the documents of the other participants. What do you notice?

:::
 
[1]: [w3school: XML elements](https://www.w3schools.com/xml/xml_elements.asp>)  

## XML Schema

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

You can find tutorials on XML and XSD as well as the follwing topic on the webdevelopment portal [W3Schools](https://www.w3schools.com/). 
:::

