---
title: "Minimum Record Recommendation"
teaching: 15
exercises: 10
---

::: questions 

- What is the Minimum Record Recommendation for Museums and Collections?

:::

::: objectives

- Knowledge of the basics of the Minimum Record Recommendation for Museums and Collections  
:::

## Minimum Record Recommendation for Museums and Collections

The recommendation was formulated by the Minimum Record Working Group, which was established in 2022 by the Museum and Media Desks of the German Digital Library (DDB), 
the Working Group on Digitisation of the „Konferenz der Museumsberatungsstellen in den Ländern“  (KMBL) and digiS Berlin. 
The objective of the Working Group is to submit the data to the German Digital Library, for example. This online database, which is intended to make cultural heritage 
in Germany accessible digitally, free of charge, and at any time, is an initiative of the German Digital Library. The database brings together the offerings of various museums, collections, and archives in Germany through the submission of their data. 

The development of the recommendation was grounded in a comprehensive set of principles and standards that are indispensable for the management of research data. 
Primarily, it incorporates the FAIR principles (findable, accessible, interoperable, re-usable). Additionally, it integrates the CARE principles (collective benefit, authority to control, responsibility, ethics), particularly within the context of colonial studies. Furthermore, the recommendation also takes into account the minimum information required for the LIDO standard:

> It has been shown that LIDO is not always easy to understand due to its language (XML-based) and structure (high degree of nesting, repeating element sets). In some cases, LIDO - a highly complex and flexible standard - exceeds the specific needs and capacities of museums and collections. The aim of the Minimum Record Recommendation is to take advantage of LIDO's benefits (structuring, controlled vocabulary integration, broad international acceptance) and to focus on the smallest possible intersection of data elements that are important for online publication across most disciplines and museum types."^[2]

This demonstrates the strong interlinking that underlies many standards. The minimal data set also incorporates other standards and their principles, 
as well as basic recommendations from the specialist community (museums) in order to increase compatibility. This also includes the Europeana Data Model, 
which can be used to enter data into the Europeana online database. The Europeana database is the digital cultural portal for Europe's cultural heritage.

It is imperative that the data record contain a number of mandatory fields, the entry and supply of which is obligatory. The use of other data fields is merely recommended, such as object description, material, dimensions, and so forth.   

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

The technical design of the data is carried out in accordance with existing standards. This is achieved 
by incorporating these standards into the mandatory fields. Various standards of the DDB (German Digital Library) 
are available for this purpose, and they can be saved in XML or RDF format, including DDB-METS/MODS.

::: challenge

### Discussion

* What do you think about the Minimum Record Recommendation?
* Do you find it helpful?
* Can you imagine to fill out all of the mandatory data fields?
* What could be challenging? 

:::




[2]: [FAQ Minimum Record Recommendation](https://wiki.deutsche-digitale-bibliothek.de/pages/viewpage.action?pageId=218628162#FAQs(English)-WhyistheMinimumRecordRecommendationLIDO-compliant?), further elaboration on LIDO will be provided subsequently.   
