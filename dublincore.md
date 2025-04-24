---
title: "Dublin Core Metadata Element Set"
teaching: 30
exercises: 20
---

::: questions 

- What is the Dublin Core Metadata Element Set (DC)?
- What is the difference between simple and qualified Dublin Core? 

:::

::: objectives

- Learn the basics of the Dublin Core Metadata Element Set. 
- Differentiate between a simple Dublin Core Set and a qualified set.
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
  
All fields are optional, can appear multiple times, and, unlike other metadata standards or schemas, can appear in any order. 
Dublin Core defines the metadata fields themselves, but not the structure for them, which is why it is often coombined with structuring standards such as METS. 

::: challenge 

### Exercise

You have a photograph by Johan Hagemeyer. It is called "Albert Einstein, Pasadena". The photograph is of Albert Einstein. 
It was taken in 1931 and loaned to the Museum in 1962. It is from the photographer's estate. Albert Einstein lived from 1879 to 1955 and was 52 years old when the photograph was taken. The photographer, Johan Hagemeyer, lived from 1884 to 1962 and the photo was taken in Pasadena. The location is New York. The photograph measures 24.6 × 18.7 cm. The mount measures 45.6 × 35.4 cm. 

You can find the object in the [MET collection](https://www.metmuseum.org/art/collection/search/270713). View the specifications of the elements on the [website](https://www.dublincore.org/specifications/dublin-core/dces/) if you are unsure about how to annotate. 

What information would you include in each metadata field and why?   
Is there any information you are missing to fill in the fields? If so, which ones and why?  
  
Discuss in small groups.

::: solution

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

What did you discuss? What information in the data was unclear? 

:::

After all, how do we know which date is meant? The date of creation or submission? The original DC terms have been extended to make the information about the data more precise. 

## Qualified Dublin Core 

First, qualifiers were introduced. A qualifier describes an element more precisely. 

A simple Dublin Core element looks like this:

dc.date

*dc* describes the namespace (in this case Dublin Core - you can read more about namespaces in the XML Schema chapter) and *date* describes the element. Both can now be extended by a qualifier, which specifies the element, e.g.,:

dc.relation.hasversion or dc.relation.isversionof

::: challenge 

### Exercise

Take a closer look at the date element. You can find a list of all authorised qualifiers for date elements on the [Dublin Core Website](https://www.dublincore.org/specifications/dublin-core/usageguide/qualifiers/). What qualifiers would you use for the date elements for Johan Hagemeyer's photo of Albert Einstein?  

::: solution

### Examples

* dc.date.created: 1931
* dc.date.submitted: 1962
* dc.date.copyrighted: 2013
* dc.date.issued: date the image was digitaly issued on the web collection for example

:::
:::  

### DCMI Metadata Terms      

In 2022 the Dublin Core Metadata Initiative published an extended set of elements.   

> Included are the fifteen terms of the Dublin Core™ Metadata Element Set (also known as "the Dublin Core") plus several dozen properties, classes, datatypes, and vocabulary encoding schemes. The "Dublin Core" plus these extension vocabularies are collectively referred to as "DCMI metadata terms" ("Dublin Core terms" for short). These terms are intended to be used in combination with metadata terms from other, compatible vocabularies in the context of application profiles.^[1]

In addition, there are clarifications, e.g. for the date in the form of dcterms:dateAccepted, or new fields like dcterms:abstract. 

Terms:  
  
|      |      |      |      |      |  
|:----:|:----:|:----:|:----:|:----:|  
|abstract|accessRights|accrualMethod|accrualPeriodicity|accrualPolicy|  
|alternative|audience|available|bibliographicCitation|conformsTo|  
|contributor|coverage|created|creator|date|  
|dateAccepted|dateCopyrighted|dateSubmitted|description|educationLevel|  
|extent|format|hasFormat|hasPart|hasVersion|  
|identifier|instructionalMethod|isFormatOf|isPartOf|isReferencedBy|  
|isReplacedBy|isRequiredBy|issued|isVersionOf|language|  
|license|mediator|medium|modified|provenance|  
|publisher|references|relation|replaces|requires|  
|rights|rightsHolder|source|spatial|subject|  
|tableOfContents|temporal|title|type|valid|      


::: challenge

### Discussion

Take a look at the extended elements. You will find several date elements.

Do you agree with the mapping presented in the solution of the last exercise?  
Why not?   
Which element would you choose?   
You can find descriptions of the elements in the [User Guide](https://www.dublincore.org/resources/userguide/creating_metadata/). 

:::

When we talk or read about Dublin Core, we often notice that what used to be called a (metadata) field is now called an element in Dublin Core. 
You will often find that the definitions of terms overlap - as described above for standard, schema, and model. When you read the term element from now on, it refers to the data field to which content is assigned when data is captured. Think of XML. The element is identified by tags, with the value in between. This combination is used to describe an area of the ingested resource.  

::: keypoints
- The Dublin Core Standard provides a simple Set of 15 elements as well as an extended set with additional properties, classes, datatypes, and vocabulary encoding schemas.
- All fields are optional, can appear multiple times, and can appear in any order. Dublin Core defines the metadata fields themselves, but not the structure for them.
- The Dublin Core Standard is often used in combination with metadata terms. 
:::

_____________________________________________________  


[1]: [DCMI Metadata Terms](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/)

