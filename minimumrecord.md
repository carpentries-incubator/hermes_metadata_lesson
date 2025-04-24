---
title: "Minimum Record Recommendation"
teaching: 15
exercises: 10
---

::: questions 

- What is the Minimum Record Recommendation for Museums and Collections?

:::

::: objectives

- Learn the basics of the Minimum Record Recommendation for Museums and Collections  
:::

## Minimum Record Recommendation for Museums and Collections

The recommendation was formulated by the Minimum Record Working Group, which was established in 2022 by the Museum and Media Desks of the German Digital Library (DDB), the Working Group on Digitisation of the „Konferenz der Museumsberatungsstellen in den Ländern“  (KMBL) and digiS Berlin^[1]. 
The aim of the working group is to contribute the data to the German Digital Library^[2] and the Europeana online database^[3]. The German Digital Library online database, which aims to make cultural heritage in Germany digitally accessible at any time and free of charge, is an initiative of the German Digital Library. The database brings together the offerings of various museums, collections and archives in Germany through the submission of their data. The Europeana database is the digital cultural portal for Europe's cultural heritage.  

> The Minimum Record Recommendation [therefore] specifies the most important data elements for the online publication of object information from museums and collections and provides information on how these elements should be filled in. The "Minimum Record" is the smallest possible intersection of relevant data elements that ensures a minimum level of data quality across most disciplines and museum types. [...] The Minimum Record Recommendation is intended to pave the way for smaller and larger museums and collections to publish their data online and to communicate relevant standards in an easy-to-understand, low-threshold approach.^[4]

The Recommendation's development was based on a comprehensive set of principles and standards that are essential for the management of research data. First and foremost, it incorporates the FAIR principles (findable, accessible, interoperable, re-usable). It also incorporates the CARE principles (collective benefit, authority to control, responsibility, ethics), particularly in the context of colonial studies. The recommendation also takes into account the minimum information requirements of the LIDO standard:

> It has been shown that LIDO is not always easy to understand due to its language (XML-based) and structure (high degree of nesting, repeating element sets). In some cases, LIDO - a highly complex and flexible standard - exceeds the specific needs and capacities of museums and collections. The aim of the Minimum Record Recommendation is to take advantage of LIDO's benefits (structuring, controlled vocabulary integration, broad international acceptance) and to focus on the smallest possible intersection of data elements that are important for online publication across most disciplines and museum types.^[5]

This illustrates the strong correlation between many standards, which we will encounter again in the following chapters.

The record contains a number of mandatory fields. The use of other data fields, such as object description, material, dimensions and so on, is only recommended.  

Data elements that are usually populated during data entry:

* Object title or name (mandatory)
* Object type or designation (mandatory)
* Classification (recommended)
* Inventory number (mandatory)
* Object description (recommended)
* Materials (recommended)
* Techniques (recommended)
* Measurements (recommended)
* Event in object history [element set] (mandatory)
    * Event type (mandatory)
    * Person/corporate body (conditionally mandatory)
    * Date (conditionally mandatory)
    * Place (conditionally mandatory)
* Subject keyword (recommended)
* Media file [element set] (mandatory)
    * Link to media file (mandatory)
    * Usage rights of media file (mandatory)
    * Rights holder of media file (conditionally mandatory)
    * Alternative text (recommended)

Data fields that are usually populated during or after export from the local database system:

* Record ID (mandatory)
* Record language (mandatory)
* Record type (mandatory)
* Repository of object (mandatory)
* Institution providing record (mandatory)
* Media file: type of media file (mandatory)
* Usage rights of metadata record (mandatory)
* Link to published metadata record (recommended)
* Record date (recommended)  

::: discussion

### Discussion

What do you think about the Minimum Record Recommendation?
  
* Do you find it helpful?  
* Can you imagine filling in all the mandatory fields?  
* What might be a challenge?  

:::  

::: keypoints 
The Minimum Record Recommendation is an attempt to formulate a minimum set of data fields for the publication of museum collections.
:::  
__________________________________________________

[1]: [Minimum Record Recommendation](https://wiki.deutsche-digitale-bibliothek.de/pages/viewpage.action?pageId=218628097)  
[2]: [Deutsche Digitale Bibliothek](https://www.deutsche-digitale-bibliothek.de/?lang=en)  
[3]: [Europeana](https://www.europeana.eu/en)  
[4]: [Minimum Record Recommendation](https://wiki.deutsche-digitale-bibliothek.de/pages/viewpage.action?pageId=218628097)  
[5]: [Why is the Minimum Record Recommendation LIDO-compliant?](https://wiki.deutsche-digitale-bibliothek.de/pages/viewpage.action?pageId=218628162#FAQs(English)-WhatisthepurposeoftheLIDOsnippetsonthedataelementpages(%22ExpressioninLIDO%22)?)
