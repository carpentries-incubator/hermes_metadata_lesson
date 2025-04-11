---
title: "XML"
teaching: 25
exercises: 15
---

::: questions 

- What is XML? 
- How do you annotate data in XML?

:::

::: objectives

- Knowledge of XML format for storing and processing metadata. 
- Familiar with the structure of a simple XML file. 
- Able to write extracted metadata in a simple XML format.

:::

One of the most widely used file formats in the cultural sector is XML (eXtensible Markup Language). It is used to describe, structure, store and transport data. XML refers to the file format as well as to the structure in which data is recorded: the markup language. 


## XML Elements

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

You may be familiar with this structure. The HTML language, which is used to organise web pages, has a similar structure. It is also based on SGML. HTML makes it possible to mark up the typical elements of a text-based document - such as headings, paragraphs, lists or tables - as such on a web page and to structure the page semantically. Unlike HTML, where there are rules for naming tags - such as \<h1\>\</h1\> for headings - XML tags can be named freely, subject to a few technical rules. This makes it particularly interesting for use in the development of metadata standards and ontologies.  
  
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

XML also provides the ability to have comments that are not automatically read:

```xml
<!-- Here is the content of the comment, there is no closing tag -->
```

In XML, all elements must be properly nested, which means that an element opened inside another element must also be closed inside it:

```xml
<collection><name>MET</name><place>New York</place></collection>
```  
An indentation can be used to make the structure more human-readable:

```xml
<collection>
  <name>MET</name>
  <place>collection of the MET in New York</place>
</collection>
```

There are some rules for characters used in XML for syntax structure. These are replaced by a special string so that it won't cause problems if, for example, you want to use a < in the content. This would cause an error because XML expects a closing tag. To avoid errors, the character is replaced with an entity reference:
  
| string | character | meaning | 
| ---- | ---- | ---- | ----|
| \&lt; | < | less than |
| \&gt; | > | greater than |
| \&amp; | & | ampersand |
| \&apos; | ' | apostrophe |
| \&quot; | " | quotation mark |  
  
```xml
<photographer>Bernd &amp; Hilla Becher</photographer>
```
  
## Attributes    

In XML, as in HTML, tags can also have attributes, which define the content of the tags in more detail like separate metadata. They are named and the content is assigned to them with a = and enclosed in quotes:

```xml
<title lang="author's original language">Always give the title in the author's language</title>

<commonTitle lang="title as commonly known">Always give the title as it is commonly known</commonTitle>
```      
Attributes are also often used in a hierarchy to record information that applies to all the underlying data:

```xml
<collection name="Modern Art" place="New York">
  <item1/>
  <item2/>
</collection>
```
The slash here at the end of the tag (self-closing tag) means that the element is currently empty and self-contained. It is not necessary to write an opening and closing tag if there are no other elements between them. You often see this in XML output when the metadata field is empty. 

At the top of an XML document you will often find something called a prolog or declaration:

```xml
<?xml version="1.0" encoding="UTF-8"?>
```
It is optional, but provides information about the version and encoding used, and must be at the top if included.   

::: callout
XML documents that conform to all this rules are said to be "Well Formed" XML documents.
:::   
  
::: challenge

### Exercise

Open the [moma_artworks.csv file](https://github.com/HERMES-DKZ/metadata_lesson/blob/main/episodes/data/moma_artworks.csv). Use the given data of one artwork and write it in an XML format. 

::: hint

* Think about the headings in the table. Do you agree with this labelling? 
*  You can use tabs to create a hierarchy.

:::
  
::: solution

```xml
<?xml version="1.0" encoding="UTF-8"?>
<artworks>
  <artwork>
    <title>Green-Blue-Red (for Parkett no. 35)</title>
    <artist>
      <name>Gerhard Richter</name>
    </artist>
    <constituentID>4907</constituentID>
    <artistBio>
      <bio>German, born 1932</bio>
    </artistBio>
    <nationality>German</nationality>
    <beginDate>1932</beginDate>
    <endDate>0</endDate>
    <gender>male</gender>
    <date>1993</date>
    <medium>Multiple of oil on canvas</medium>
    <dimensions>composition: 11 7/16 × 15 3/4&quot; (29 × 40 cm); sheet: 11 3/4 × 15 3/4&quot; (29.9 × 40 cm)</dimensions>
    <creditLine>Riva Castleman Endowment Fund, Lily Auchincloss Fund, and Gift of Parkett</creditLine>
    <accessionNumber>110.1998.1</accessionNumber>
    <classification>Multiple</classification>
    <department>Drawings &amp; Prints</department>
    <dateAcquired>1998-03-05</dateAcquired>
    <cataloged>Y</cataloged>
    <objectID>61953</objectID>
    <url>https://www.moma.org/collection/works/61953</url>
    <imageURL></imageURL>
    <onView></onView>
    <height>29.0</height>
    <width>40.0</width>
  </artwork>
  <artwork>
    <title>Untitled</title>
    <artist>
      <name>Blinky Palermo</name>
    </artist>
    <constituentID>4474</constituentID>
    <artistBio>
      <bio>German, 1943–1977</bio>
    </artistBio>
    <nationality>German</nationality>
    <beginDate>1943</beginDate>
    <endDate>1977</endDate>
    <gender>male</gender>
    <date>1970</date>
    <medium>Dyed cotton mounted on muslin</medium>
    <dimensions>6' 6 3/4\" x 6' 6 3/4\" (200 x 200 cm)</dimensions>
    <creditLine>Gift of Jo Carole and Ronald S. Lauder</creditLine>
    <accessionNumber>650.1997</accessionNumber>
    <classification>Painting</classification>
    <department>Painting &amp; Sculpture</department>
    <dateAcquired>1997-06-02</dateAcquired>
    <cataloged>Y</cataloged>
    <objectID>78283</objectID>
    <url>https://www.moma.org/collection/works/78283</url>
    <imageURL>https://www.moma.org/media/W1siZiIsIjE1MTQ0MCJdLFsicCIsImNvbnZlcnQiLCItcmVzaXplIDEwMjR4MTAyNFx1MDAzZSJdXQ.jpg?sha=c54d00f27ed284be</imageURL>
    <onView></onView>
    <height>200.0</height>
    <width>200.0</width>
  </artwork>
  <artwork>
    <title>Daylight Savings Time</title>
    <artist>
      <name>Pierre Roy</name>
    </artist>
    <constituentID>5065</constituentID>
    <artistBio>
      <bio>French, 1880–1950</bio>
    </artistBio>
    <nationality>French</nationality>
    <beginDate>1880</beginDate>
    <endDate>1950</endDate>
    <gender>male</gender>
    <date>1929</date>
    <medium>Oil on canvas</medium>
    <dimensions>21 1/2 x 15&quot; (54.6 x 38.1 cm)</dimensions>
    <creditLine>Gift of Mrs. Ray Slater Murphy</creditLine>
    <accessionNumber>1.1931</accessionNumber>
    <classification>Painting</classification>
    <department>Painting &amp; Sculpture</department>
    <dateAcquired>1931-01-19</dateAcquired>
    <cataloged>Y</cataloged>
    <objectID>78294</objectID>
    <url>https://www.moma.org/collection/works/78294</url>
    <imageURL>https://www.moma.org/media/W1siZiIsIjIzMzkzNyJdLFsicCIsImNvbnZlcnQiLCItcmVzaXplIDEwMjR4MTAyNFx1MDAzZSJdXQ.jpg?sha=74825d4c62cd5a8a</imageURL>
    <onView></onView>
    <height>54.6</height>
    <width>38.1</width>
  </artwork>
  <artwork>
    <title>The Bather</title>
    <artist>
      <name>Paul Cézanne</name>
    </artist>
    <constituentID>1053</constituentID>
    <artistBio>
      <bio>French, 1839–1906</bio>
    </artistBio>
    <nationality>French</nationality>
    <beginDate>1839</beginDate>
    <endDate>1906</endDate>
    <gender>male</gender>
    <date>c. 1885</date>
    <medium>Oil on canvas</medium>
    <dimensions>50 x 38 1/8&quot; (127 x 96.8 cm)</dimensions>
    <creditLine>Lillie P. Bliss Collection</creditLine>
    <accessionNumber>1.1934</accessionNumber>
    <classification>Painting</classification>
    <department>Painting &amp; Sculpture</department>
    <dateAcquired>1934-09-23</dateAcquired>
    <cataloged>Y</cataloged>
    <objectID>78296</objectID>
    <url>https://www.moma.org/collection/works/78296</url>
    <imageURL>https://www.moma.org/media/W1siZiIsIjQ0NjA2NyJdLFsicCIsImNvbnZlcnQiLCItcmVzaXplIDEwMjR4MTAyNFx1MDAzZSJdXQ.jpg?sha=c6bd692fa0fe0685</imageURL>
    <onView>&quot;MoMA, Floor 2, 2 South&quot;</onView>
    <height>127.0</height>
    <width>96.8</width>
  </artwork>
  <artwork>
    <title>Syntheses of Naples</title>
    <artist>
      <name>Enrico Prampolini</name>
    </artist>
    <constituentID>4720</constituentID>
    <artistBio>
      <bio>Italian, 1894–1956</bio>
    </artistBio>
    <nationality>Italian</nationality>
    <beginDate>1894</beginDate>
    <endDate>1956</endDate>
    <gender>male</gender>
    <date>before 1930</date>
    <medium>Oil on canvas</medium>
    <dimensions>39 3/8 x 39 1/2&quot; (100 x 100.3 cm)</dimensions>
    <creditLine>Gift of Dr. Julius Spitzer</creditLine>
    <accessionNumber>1.1942</accessionNumber>
    <classification>Painting</classification>
    <department>Painting &amp; Sculpture</department>
    <dateAcquired>1941-12-10</dateAcquired>
    <cataloged>Y</cataloged>
    <objectID>78299</objectID>
    <url>https://www.moma.org/collection/works/78299</url>
    <imageURL>https://www.moma.org/media/W1siZiIsIjE4NjgzNSJdLFsicCIsImNvbnZlcnQiLCItcmVzaXplIDEwMjR4MTAyNFx1MDAzZSJdXQ.jpg?sha=9740d0c731c867c2</imageURL>
    <onView></onView>
    <height>100.0</height>
    <width>100.3</width>
  </artwork>
</artworks>
```
:::
:::  
  
::: instructor
It is likely that not all participants will complete the exercise in the time allotted, as the notation of XML is very complex. This is part of the learning process and can be discussed afterwards. Alternatively, more time can be allocated to the exercise.
:::   
  
::: discussion

### Discussion

Compare your XML with the other participants' documents. What do you notice?

:::

::: instructor
The exercise can be done in groups if there are many participants. Otherwise, someone can present their solution at the end and discuss it together. Discussion points should include the two ways of writing empty elements and making sure that special characters such as & are caught. There can also be a general discussion about the headings or naming of the tags, or what certain tags mean, e.g. onView means 'on view' in the current exhibition.
:::  

::: keypoints
- XML is one of the most widely used metadata formats.
- An XML document contains XML elements to structure the data.
- Attributes provide additional information about elements or groups of elements.
:::
______________________________________________
[1]: [w3school XML elements](https://www.w3schools.com/xml/xml_elements.asp>)  
