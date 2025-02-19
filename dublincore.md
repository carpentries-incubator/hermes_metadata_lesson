---
title: "Dublin Core Metadata Element Set"
teaching: 30
exercises: 3
---

::: questions 

- What is the Dublin Core Metadata Element Set (DC)?
- What is the difference between simple and qualified Dublin Core? 

:::

::: objectives

- Knowledge of the basics of the Dublin Core Metadata Element Set. 
- Familiar with the difference between a simple Dublin Core Set and a qualified set.
:::


## Dublin Core Metadata Element Set

The Dublin Core is a simple metadata standard. First published as a standard by the Dublin Core Metadata Initiative in 1998, 
the simple version of the set consists of 15 core elements for describing a resource:

* Contributor
* Coverage
* Creator
* Date
* Description
* Format
* Identifier
* Language
* Publisher
* Relation
* Rights
* Subject
* Title
* Type
  
All fields are optional, not mandatory, can appear multiple times, and, unlike other metadata standards or schemas, can appear in any order. 
Dublin Core defines the metadata fields themselves, but not the structure for them, which is why it is often integrated with structuring standards such as METS. 

::: challenge 

### Exercise

View the specifications of the elements on the [website](https://www.dublincore.org/specifications/dublin-core/dces/).

You have a photograph by Johan Hagemeyer. It is called "Albert Einstein, Pasadena". The photograph is of Albert Einstein. 
It was taken in 1931 and loaned to the Museum in 1962. It is from the photographer's estate. Albert Einstein lived from 1879 to 1955 
and was 52 years old when the photograph was taken. The photographer, Johan Hagemeyer, lived from 1884 to 1962 and the photo was taken in Pasadena. 
The location is New York. The photograph measures 24.6 × 18.7 cm. The mount measures 45.6 × 35.4 cm. 

You can find the object in the [MET collection](https://www.metmuseum.org/art/collection/search/270713). What information would you include in each metadata 
field and why? Is there any information you are missing to fill in the fields? If so, which ones and why? Discuss in small groups.

::: solution

### Show me the solution

* contributor: MET (as a custodian and managing institution)
* coverage: New York (as place of the custodian and managing institution)
* creator: Johan Hagemeyer (as photographer)
* date: 1931 (as museum submission date or record entry date (unknown here))
* description: portrait of Albert Einstein
* format: 24.6 × 18.7 cm (foto) or 45.6 × 35.4 cm (full size with mount)
* identifier: missing information
* language: en (RFC 4646 standard)
* publisher: MET
* relation: other fotos of Johan Hagemeyer or images with similiar topic
* rights: © 2013 Jeanne Hagemeyer – All Rights Reserved
* source: missing information
* subject: portrait, Albert Einstein
* title:  Albert Einstein, Pasadena
* type: Gelatin silver print

This could be one of many possible solutions. 
:::
:::

::: discussion

### Discussion

What did you discuss? What data was unclear? 

:::



This initial simple indexing of data using Dublin Core can be extended to more precise information. After all, how do we know which date is meant? The date of creation? The date of submission? 

## Qualified Dublin Core 

A Dublin Core element looks like this:

dc.date

*dc* describes the namespace (in this case Dublin Core) and *date* describes the element. Both can now be extended by a so-called qualifier, which specifies the date:

dc.date.available or dc.date.issued 

::: challenge 

### Question

Which of the elements you have just worked on that you could not assign clearly or at all would you expand with a qualifier and how? 

::: solution

### Examples

* dc.date.created: 1931
* dc.date.submitted: 1962
* dc.date.copyrighted: 2013
* dc.date.issued: date the image was digitaly issued on the web collection for example
* dc.format.image: 24.6 × 18.7 cm
* dc.format.object: 45.6 × 35.4 cm

:::
:::

In addition, controlled vocabulary can be used via the use of attributes: 

name=“dc.date“ scheme=“ISO1863“ 

This assigns an attribute to the field, as already shown for XML. This attribute assigns the use of the ISO standard.

Under the dcterms namespace, we also find an extended set of elements that integrates the familiar 15 basic elements. 
In addition, there are clarifications, e.g. for the date in the form of dcterms:dateAccepted, or new fields like dcterms:abstract. 

This extension of the original elements is referred to as Qualified Dublin Core or DCMI metadata terms (“Dublin Core terms” for short). 

::: challenge

### Discussion

Take a look at the extended elements. You will find several date elements.

Do you agree with the mapping in the solution to the last exercise? Why not? Which element would you choose? 

:::

When we talk or read about Dublin Core, we often notice that what used to be called a (metadata) field is now called an element in Dublin Core. 
You will often encounter the mixing of different terms - as described above for standard, schema, and model. 
When you read the term element from now on, it refers to the data field to which content is assigned when data is captured. 
Think XML. The element is identified by tags, with the value in between. This combination is used to describe an area of the ingested resource. 


