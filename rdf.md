---
title: "Resource Description Framework (RDF)"
teaching: 20
exercises: 15
---

::: questions 

- What is the Resource Description Framework (RDF)?
:::

::: objectives

- Knowledge of the basics of the Resource Description Framework (RDF). 
:::


RDF was originally conceived by the World Wide Web Consortium (W3C) as a standard for describing metadata. 
It is now considered a fundamental building block of the Semantic Web and is similar to the classical methods 
for modeling concepts, such as the Entity-Relationship Model mentioned in the introduction.

Data in RDF are statements about resources. These statements are modeled as triples. The set of triples forms a 
(mathematical) graph and is called an RDF model.  

The model has features that facilitate data merging even if the underlying schemas differ, and it specifically 
supports the evolution of schemas over time without requiring all the data consumers to be changed:

The subject and predicate are always resources. The object can be either a resource or a literal. Literals are 
strings that can be interpreted using a specified data type and can be specified as boolean values, numbers, or 
dates, for example. Unique identifiers (URIs) are used to identify resources. A Uniform Resource Identifier is an 
identifier consisting of a string of characters used to identify an abstract or physical resource. They are built 
in a similar way to a web address (URL). The aforementioned GND or Wikidata IDs are examples. Different sources can 
be linked together using the URIs. Remember the graphic in the introduction. 
The predicate is also defined by a URI. This is possible, for example, when the relationship is defined by a metadata 
standard. The metadata fields of the standards have their own URIs. The relationship between author and book can be 
modeled using the Dublin Core elements. The data format for RDF is typically XML. 

Grafik einbinden

More content to be added!
