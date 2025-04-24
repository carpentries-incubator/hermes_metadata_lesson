---
title: "Resource Description Framework (RDF)"
teaching: 20
exercises: 10
---

::: questions 

- What is the Resource Description Framework (RDF)?
- How can pieces of information be linked using triples and URI? 
:::

::: objectives

- Learn the basics of the Resource Description Framework (RDF)
- Learn how to use URIs for linking data in the RDF
:::


RDF was originally conceived by the World Wide Web Consortium (W3C) as a standard for describing metadata. 
It is now considered a fundamental building block of the Semantic Web and is similar to the classical methods 
for modeling concepts, such as the Entity-Relationship Model mentioned in the introduction.

Data in RDF are statements about resources. These statements are modeled as triples. The set of triples forms a 
(mathematical) graph and is called an RDF model. 

```xml
<subject/><predicate/><object/>
<painter>Frida Kahlo></painter><creator>is creator of</creator><painting>The two fridas</painting>
```

The subject and predicate are always resources. This means that they are entities with an extended set of information. The object can be either a resource or a literal. Literals are strings that can be interpreted using a specified data type like boolean values, numbers, or dates. Unique identifiers (e.g. URIs) are used to identify resources. 

A Uniform Resource Identifier (URI) is an identifier consisting of a string of characters used to identify an abstract or physical resource. They are built in a similar way as a web address (URL). The aforementioned GND or Wikidata IDs are examples. Different sources can be linked together using the URIs. Remember the graphic in the introduction. 

The predicate is also defined by a URI. This is possible, for example, when the relationship is defined by a metadata 
standard. The metadata fields of the standards have their own URIs. The relationship between author and book can be 
modeled using the Dublin Core element "creator". 
```
<https://www.wikidata.org/wiki/Q5588><http://purl.org/dc/terms/creator><https://www.wikidata.org/wiki/Q3232010>
```
The two examples above use the identifiers of Wikidata and Dublin Core to represent the same information: Frida Kahlo is the creator of "The two Fridas". 

Technically, RDF can be implemented in several formats, including JSON-LD and RDF/XML - two special formats of JSON and XML for RDF.


::: challenge

### Exercise

Take a closer look at the [Wikidata resource of Frida Kahlos painting "The two Fridas"](https://www.wikidata.org/wiki/Q3232010). Can you find an alternative way of describing the predicate instead of using Dublin Core?

::: solution

### Solution

[creator property](https://www.wikidata.org/wiki/Property:P170):  
The information listed in Wikidata for an entity is all labeled with properties such as location, genre, creator etc. These properties themselves have an identifier and are therefore standardized. All paintings can be modeled in a consistent way. The creator property can be used similiar to the Dublin Core element of creator. 
:::
:::

::: challenge

### Exercise

Use wikidata to create a triple for the following statements:  
1) Michelangelo is the creator of the Pietà.  
2) Michelangelo was born in Caprese Michelangelo.  
3) The Pietà is located in the St. Peter's Basilica.   

::: solution

### Solution

```
<https://www.wikidata.org/wiki/Q5592><https://www.wikidata.org/wiki/Property:P170><https://www.wikidata.org/wiki/Q235242>
<https://www.wikidata.org/wiki/Q5592><https://www.wikidata.org/wiki/Property:P19><https://www.wikidata.org/wiki/Q52069>
<https://www.wikidata.org/wiki/Q235242><https://www.wikidata.org/wiki/Property:P276h><ttps://www.wikidata.org/wiki/Q12512>
```
:::
:::
   

::: callout 
For more information on RDF and Linked Open Data, refer to [this lesson](LOD link to be added).
:::   
  
::: keypoints
- RDF is a standard model for data interchange on the Web.  
- Statements are modeled as triples. Using URIs, these triples link datapoints together and form a (mathematical) graph.
:::
