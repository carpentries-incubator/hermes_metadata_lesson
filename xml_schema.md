---
title: "XML Schema"
teaching: 60
exercises: 30
---

::: questions 

- What is an XML schema? 
- What are the basic elements of an XML schema? 
- What is an XML Schema used for?
:::

::: objectives

- Learn the basic elements and structure of an XML Schema.
- Understand simple XML Schemas.
:::

As you have learned there are standards for annotating data in the Humanities. To ensure that data is properly standardized and interoperable — allowing it to be imported into, for example, cultural heritage databases — technical schemas are used. In the humanities and cultural studies, the XML Schema is a common choice. The XML Schema can be expressed through different syntaxes. The XML Schema Definition (XSD) is widely used to define the structure, elements, and technical rules of an XML document, thereby establishing consistent annotation guidelines. The filename extension is .xsd. 

## XSD (XML Schema Definition) 

By using the XML-based XML Schema Definition you can define:  

* the elements and attributes of an XML document  
* the number and order of child elements  
* data types and default or fixed values for elements and attributes  


It is characterised by the use of a schema tag as the container element for the whole document: 

```xsd
<xs:schema>

</xs:schema>
<!-- or e.g., -->
<xsd:schema>

</xsd:schema>
```

The prefix „xs“ or "xsd" indicates the namespace for the schema. Remember not to use : in XML tags. Since the colon is a meta character with a reserved meaning, do not use it anywhere except when referencing namespaces.

### Namespaces

::: callout
A namespace contains a set of rules and is defined in the xsd file. Other, existing namespaces can also be included in a certain namespace. The rules defined by existing namespaces are also referenced in the XML document.
::: 

The namespace mechanism for XML data has been developed by the W3 Consortium[1]. A namespace is a set of rules that provides specifications for XML elements and attributes. For example, it describes how elements and attributes are named or used. A namespace can be technically stored in the form of an xsd file or in the form of theoretical documentation. Technical specifications can be requirements for data types or minimum or maximum values. Documentation usually describes contextual relationships or rules for using controlled vocabularies or thesauri. Specifications from the documentation may be technically incorporated into the schema. Otherwise, they may be found as comments in the file. 

Example from LIDO Schema[2] for the gender of an actor with additional human-readable notes: 

```xsd
<xsd:element name="genderActor" type="lido:textComplexType" minOccurs="0" maxOccurs="unbounded">
  <xsd:annotation>
    <xsd:documentation>Definition: The sex of the individual.</xsd:documentation>
    <xsd:documentation>How to record: Data values: male, female, unknown, not applicable. Repeat this element for language variants only.</xsd:documentation>
    <xsd:documentation>Notes: Not applicable for corporate bodies.</xsd:documentation>
  </xsd:annotation>
</xsd:element>
```

The xs:annotation is a container in which additional information can be embedded. When xs:documentation is used within the container, the information is processed in a human readable way. If xs:appinfo is used within it, it means that information is now also machine-readable.

Namespaces are specifically useful in two cases: 

First, they define elements and attributes more precisely, especially when they have different meanings in different sources and specifications from different standards need to be combined. 
Consider the problem of dates and names: these are very common elements and should be defined precisely. How should the date be recorded? 
As a period of time or as an ISO value? Are first and last names recorded separately? Since there may be different rules in each standard, 
but they may refer to the same field name, namely "date" or "name", it is important to specify the source of the rules.

Second, they group all the elements and attributes of an XML document together so that software can easily recognise them.

A namespace is assigned in the header of the file by using xmlns as an attribute and a URI as the content. 

```xsd
<xs:schema xmlns="http://www.w3.org/2001/XMLSchema">
```

The xmlns specification and the URI behind it refer to the W3 consortium namespace for an XML schema as the standard for the entire document. All elements and attributes are defined according to this namespace. The URI (Uniform Resource Identifier) serves as a unique identifier to reference the specifications, it is usually a web address (URL).  

Where multiple standards are used, or parts of other schemas are adopted, the namespaces should be prefixed in order to identify which elements or attributes belong to which standard:

```xsd
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
	xmlns:xlink="http://www.w3.org/1999/xlink">
```

In the file, the prefix refers to the standard used for that element or attribute. The example above also uses the xlink namespace. This specification defines the XML Linking Language (XLink) version 1.1, which allows elements to be inserted into XML documents to create and describe links between resources.

When specifying multiple standards, if no prefix is specified for a standard, that standard is the default specification for the entire document and all elements without a prefix refer to that standard. 

In addition, when creating an xsd file for a specially developed standard, a targetNamespace is specified. This is the name of the namespace the technical details of which are defined in this xsd file and which is then referenced in the XML document. 

```xsd
<xs:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  targetNamespace="lbacao"
  xmlns:lc="lbacao"
  elementFormDefault="qualified"
  attributeFormDefault="unqualified">
```

The default namespace in this example is the xsd namespace. This file creates a new namespace: the lbacao namespace. All elements that do not refer to the xsd namespace would be prefixed with lc. 

Other namespaces can also be imported into the schema with the following specification, allowing additional software (validators) to check compliance with this standard:

```xsd
<xs:import namespace="http://www.w3.org/XML/1998/namespace" schemaLocation="http://www.w3.org/2001/03/xml.xsd">
```

The schemaLocation refers directly to the associated schema - the xsd file - the specifications of which are adopted for the document. Special software (validators) can be used to check whether an XML document conforms to the technical rules specified in an xsd file. 

### Simple Element 

A simple XML element is defined in the schema by the specification xs:element and the attributes name and type at least. 

```xsd
<xs:element name="descriptive name" type="string"></xs:element>
```

For example, we can specify that a place is always called "place" and that the character type of the content is a string. This specification prevents the tag from sometimes being called "place", sometimes "location" or even "city":

```xsd
<xs:element name="place" type="string"/>
```

This defines the \<place\> XML tag such as \<place\>New York\</place\>. 

### Content restrictions

Content restrictions for a simple element can be set using so called facets. They are used to define acceptable values for XML elements or attributes:

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

With these restrictions for a datafield "age", only values from 0 to 120 are allowed in the XML. 

You can also use an enumeration constraint to limit the content to a set of values:

```xsd
<xs:element name="color">
  <xs:simpleType>
    <xs:restriction base="xs:string">
      <xs:enumeration value="blue"/>
      <xs:enumeration value="red"/>
      <xs:enumeration value="green"/>	      
    </xs:restriction>
  </xs:simpleType>
</xs:element>
```

Using xs:pattern you can set restrictions on a series of numbers or letters. There are other constraints for values in XML, e.g., whiteSpace or length:

#### Restrictions for Datatypes

| Constraint | Description |
| ----- | ------ |
| enumeration | 	Defines a list of acceptable values | 
| fractionDigits |  	Specifies the maximum number of decimal places allowed. Must be equal to or greater than zero |
| length 	| Specifies the exact number of characters or list items allowed. Must be equal to or greater than zero | 
| maxExclusive 	| Specifies the upper bounds for numeric values (the value must be less than this value) |
| maxInclusive 	| Specifies the upper bounds for numeric values (the value must be less than or equal to this value) |
| maxLength 	| Specifies the maximum number of characters or list items allowed. Must be equal to or greater than zero |
| minExclusive 	| Specifies the lower bounds for numeric values (the value must be greater than this value) |
| minInclusive 	| Specifies the lower bounds for numeric values (the value must be greater than or equal to this value) |
| minLength 	| Specifies the minimum number of characters or list items allowed. Must be equal to or greater than zero |
| pattern 	| Defines the exact sequence of characters that are acceptable |
| totalDigits 	| Specifies the exact number of digits allowed. Must be greater than zero |
| whiteSpace 	| Specifies how white space (line feeds, tabs, spaces, and carriage returns) is handled |

A simple element contains only one piece of information. No other elements can be nested within it, nor can content information be stored in additional attributes. 

### ComplexType

You will often encounter complexType in metadata schemas. This allows the element (later data field) to be defined much more precisely. Using this type, it is possible, for example, to create a group with child elements and to assign attributes to elements.

```xsd
<xs:element name="object">
  <xs:complexType name="objectType" abstract="true"> 
    <xs:sequence> 
      <xs:element name="creator" type="xs:string" minOccurs="1"/> 
      <xs:element name="title" type="xs:string"/> 
      <xs:element name="date" type="xs:date"/>
      <xs:element name="medium" type="xs:string"/>
    </xs:sequence> 
  </xs:complexType> 
  <xs:complexType name="creator" abstract="true"> 
    <xs:sequence> 
      <xs:element name="name" type="xs:string" maxOccurs="1"/> 
      <xs:element name="dateOfBirth" type="xs:date"/>
      <xs:element name="dateOfDeath" type="xs:date"/>
    </xs:sequence> 
  </xs:complexType> 
</xs:element>
```

This format is suggested for the definition of an object, e.g. in cultural heritage. Data fields are defined for the object itself, such as title and creator or medium. At least one creator must be specified in the block for the object. The xs:sequence element (called "indicator") specifies that the child elements must appear in the specified order. Each child element can occur from 0 to any number of times. In addition, the creator's details are recorded in the second block, together with the life data. Only one creator's name may be entered in this block. So, if there are multiple creators, each will have their own details in a separate block. 

Xsd provides more indicators to order the elements or to define the occurrence of elements:

**Order indicators**, used to define the order of the elements, treated as tags:

-  All - The all indicator specifies that the child elements can appear in any order, and that each child element must occur only once. 
-  Choice - The choice indicator specifies that one of the child elements of choice can occur.
-  Sequence - The sequence indicator specifies that the child elements must appear in a specific order.

```xsd
<xs:element name="artist">
  <xs:complexType>
    <xs:all>
      <xs:element name="firstname" type="xs:string"/>
      <xs:element name="lastname" type="xs:string"/>
    </xs:all>
  </xs:complexType>
</xs:element>
``` 

**Occurrence indicators**, used to define how often an element can occur, treated like attributes:

- maxOccurs
- minOccurs

```xsd
<xs:element name=“object“>
  <xs:complexType name="objectType" abstract="true"> 
    <xs:sequence> 
      <xs:element name="creator" type="xs:string" minOccurs="1" maxOccurs="3"/>
      <!-- minimum one creator has to be added, maximum three can be added -->
      <xs:element name="title" type="xs:string" maxOccurs="1"/>
      <!-- only one title can be added -->
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

**Group indicators**, used to define related sets of elements, treated as tags:

- Group name
- attributeGroup name

```xsd
<xs:group name="artistgroup">
  <xs:sequence>
    <xs:element name="firstname" type="xs:string"/>
    <xs:element name="lastname" type="xs:string"/>
    <xs:element name="nationality" type="xs:string"/>
  </xs:sequence>
</xs:group> 
``` 

It is also possible to assign further attributes to the elements of a complexType. To do this, the attribute itself is created in the form of a simple element and assigned to the corresponding element to which it is to be applied. 

```xsd
<!-- attribute covers the object element -->
<xs:element name="object" type="string">
  <xs:complexType name="objectType" abstract="true">
    <xs:element name="title" type="string" maxOccurs="1"/> 
    <xs:attribute name="lang" type="string" default="EN"/>
  </xs:complexType>
</xs:element>

<!-- attribute only for the place element within the archiv element -->
<xsd:complexType name="archiv">
  <xsd:sequence>
    <xsd:element name="aufbewahrungsort" type="xsd:string" /><!-- depository -->
    <xsd:element name="ort"><!-- place -->
      <xsd:complexType>
        <xsd:attribute name="gndid" type="lc:GNDID" />
      </xsd:complexType> 
    </xsd:element>
  </xsd:sequence>
</xsd:complexType>
```

In the first example above, a language attribute is defined that is applied to the entire element. If the language is not specified, the default value is 'English'. In the second example, the attribute is defined as a child of the "place" element, and is therefore only valid for that element.

Instead of a default value, the value can also be fixed:

```xsd
<xs:attribute name="lang" type="string" fixed="EN"/>
```

It should be noted that all attributes are optional by default when creating the XML element, unless the use of the attribute is specified as required:

```xsd
 <xs:attribute name="name" use="required"/>
```

If an attribute is allowed but should not be specified in more detail, the anyAttribute element is used: 

```xsd
<xs:element name="creator">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="firstname" type="xs:string"/>
      <xs:element name="lastname" type="xs:string"/>
    </xs:sequence>
    <xs:anyAttribute/>
  </xs:complexType>
</xs:element>
```

Now the creator can have any attribute in the XML, like e.g. an identifier or an alternative name. 

### Creating a customized type

You can also create an individual type for elements and attributes:

```xsd
<xsd:simpleType name="tGNDID"><!-- GND identifier -->
  <xsd:restriction base="xsd:string">
  </xsd:restriction>
</xsd:simpleType>

<xsd:complexType name="tHistoricalPerson">
  <xsd:all>
    <xsd:element name="typ" type="xsd:string" /> 
    <xsd:element name="name" type="xsd:string" />
  </xsd:all>
  <xsd:attribute name="gndid" type="lc:tGNDID" />
</xsd:complexType>

<xsd:complexType name="tUrkunde">
  <xsd:sequence>

    <xsd:element name="aussteller" type="lc:tHistoricalPerson" /><!-- author/creator of charter →

  </xsd:sequence>
</xsd:complexType>
```

In the simpleType the requirement for a GND identifier is set as a string. The defined type "tGNDID" is used as an attribute in the complexType for the historical personality. The complexType for the historical personality is then used again as a type for the element "aussteller" in the complexType "rUrkunde".


The XML output would look like this:

```xml
<urkunde> 
  <aussteller gndid="https://d-nb.info/gnd/2001630-X">
    <typ>corporation</typ>
    <name>University of Marburg</name>
  </aussteller> 
</urkunde> 
``` 

The methods presented can also be nested in each other: 

```xsd
<xsd:complexType name="tArchiv">
  <xsd:sequence>
    <xsd:element name="aufbewahrungsort" type="xsd:string" /><!-- depository -->
    <xsd:element name="ort"><!-- place -->
      <xsd:complexType>
        <xsd:attribute name="gndid" type="lc:tGNDID" />
      </xsd:complexType> 
    </xsd:element>
  </xsd:sequence>

</xsd:complexType>
```

The element "ort" itself is another complexType nested within the complexType "tArchiv". This is done to assign a special attribute only to this element. 

::: callout
An XML that conforms to a schema is called valid. It should not be confused with well-formed, which refers to compliance with fundamental XML rules.
:::

::: challenge

### Exercise

The example below shows the complexType from a real draft xsd for a charter collection. Add the indents so that the elements are nested correctly as shown in the examples.

```xsd
<xsd:complexType name="tUrkunde">
<xsd:sequence>
<xsd:element name="id" type="xsd:string" /> <!-- identifier -->
<xsd:element name="ausstellungsdatum" type="xsd:string" /><!-- date of issue -->
<xsd:element name="datierung"> <!-- dating --><!-- format: yyyy-mm-dd:yyyy-mm-dd -->
<xsd:complexType> 
<xsd:attribute name="von" type="xsd:date" /> 
<xsd:attribute name="bis" type="xsd:date" /> 
</xsd:complexType> 
</xsd:element> 
<xsd:element name="aussteller" type="lc:tHistoricalPerson" /><!-- author/creator of charter -->
<xsd:element name="mitsiegler" type="lc:tSimpleHistoricalPerson" minOccurs="0" maxOccurs="unbounded" /><!-- sealer-->
<xsd:element name="ausstellungsort" type="lc:tOrt" /><!-- place of issue -->
<xsd:element name="archiv" type="lc:tArchiv" />
<xsd:element name="siegel"> <!-- seal -->
<xsd:complexType>
<xsd:attribute name="urspr" type="xsd:nonNegativeInteger" /><!-- number of original seals -->
<xsd:attribute name="erha" type="xsd:nonNegativeInteger" /><!-- number of preserved seals -->
</xsd:complexType>
</xsd:element> 
</xsd:sequence>
</xsd:complexType>
```
::: solution
```xsd
<xsd:complexType name="tUrkunde">
  <xsd:sequence>
    <xsd:element name="id" type="xsd:string" /> <!-- identifier -->
    <xsd:element name="ausstellungsdatum" type="xsd:string" /><!-- date of issue -->
    <xsd:element name="datierung"> <!-- dating --><!-- format: yyyy-mm-dd:yyyy-mm-dd -->
      <xsd:complexType> 
        <xsd:attribute name="von" type="xsd:date" /> 
        <xsd:attribute name="bis" type="xsd:date" /> 
      </xsd:complexType> 
    </xsd:element> 
    <xsd:element name="aussteller" type="lc:tHistoricalPerson" /><!-- author/creator of charter -->
    <xsd:element name="mitsiegler" type="lc:tSimpleHistoricalPerson" minOccurs="0" maxOccurs="unbounded" /><!-- sealer-->
    <xsd:element name="ausstellungsort" type="lc:tOrt" /><!-- place of issue -->
    <xsd:element name="archiv" type="lc:tArchiv" />
    <xsd:element name="siegel"> <!-- seal -->
      <xsd:complexType>
        <xsd:attribute name="urspr" type="xsd:nonNegativeInteger" /><!-- number of original seals -->
        <xsd:attribute name="erha" type="xsd:nonNegativeInteger" /><!-- number of preserved seals -->
      </xsd:complexType>
    </xsd:element> 
   </xsd:sequence>
</xsd:complexType>
```
:::
:::

It is more difficult to create a valid XML from an xsd file:

::: challenge

### Advanced Exercise

Write an XML file that matches the [sample xsd file](https://github.com/HERMES-DKZ/metadata_lesson/blob/main/episodes/data/lba_cao_exercise.xsd). To validate the XML you can use the [validator](https://www.freeformatter.com/xml-validator-xsd.html). Of course, you can find another validator to check for differences. What validation score do you get if the XML is not valid? Are these evaluations helpful? 

::: solution
```xml
<?xml version="1.0" encoding="utf-8" ?>
<!-- Author: Mathias Gutenbrunner, University Library Marburg 
draft as part of the Marburger Urkundenrepositorium - Datenbank des CAO und LBA
https://urkundenrepositorium.uni-marburg.de/home
project website = https://www.uni-marburg.de/de/fb09/deutsche-philologie-des-mittelalters/forschung/marburger-urkundenrepositorium
August 2021
edited by Corinna Berg, Marburg Center for Digital Culture and Infrastructure, Philipps University of Marburg
as part of the HERMES project https://hermes-hub.de/; development of an introduction to metadata standards
March 2025 -->

<!-- Changes:-->
<!-- deleted original comments-->
<!-- added new comments with translations -->


<lba_cao xmlns="lbacao"
         xmlns:lc="lbacao">
  <urkunde> 
    <id/>
    <ausstellungsdatum/>
    <datierung von="1855-01-31" bis="1855-01-31"/>
    <aussteller gndid="">
      <typ/>
      <name/>
    </aussteller> 
    <mitsiegler gndid=""/>
    <ausstellungsort gndid=""/>
    <archiv>
      <aufbewahrungsort/>
      <ort gndid=""/>
      <institution gndid=""/>
      <signatur/>
      <vorbesitzer/>
    </archiv>
    <siegel urspr="3" erha="1"/>
  </urkunde>
</lba_cao>
```

As you can see, most of the fields are empty, but some data needs to be added. Since the xsd namespace is referenced, its rules should apply. The dating element has the "from" and "to" attributes which use xs:date as the type. xs:date is specified in the following form "YYYY-MM-DD" and all components are required. Therefore, any date in this format must be added in the XML. 
The element "seal", which annotates the number of original and preserved seals, has the type xs:nonNegativeInteger. This type is defined by a number equal to or greater than 0, so a number must be specified here as well.
:::
:::

There are other methods of defining conditions for an XML document in an XML Schema. You can find references to these in this lesson under "More" --> "References" at the top of the lesson.

::: challenge

### Question

Did you try to add content to the element "datierung"? If you do, the validator will not accept the XML as correct. Can you imagine why it is not correct to fill in a content like \<datierung\>2025-03-25:2025-04-01\</datierung\>? Did you get a validation score using the validator? 

::: solution
The feedback from the validator would look something like this:

> Cvc-complex-type.2.1: Element 'datierung' Must Have No Character Or Element Information Item [children], Because the Type's Content Type Is Empty.
 
The element "datierung" has no content. It is only defined by its attribute. It is called an empty element within a complexType.
:::
:::



  

::: keypoints
- The XML Schema is helpful to describe allowed document content. It is the "grammar" for XML. 
- It uses the XML syntax. 
- An XML that conforms to a schema is called valid.
- It is easy to validate the correctness of data of an XML by using a validator.
- Your schema can be reused in other schemas as well. 
- You can create your own data types derived from the standard types of xs:schema.
:::

----
[1]: [The World Wide Web Consortium (W3C)](https://www.w3schools.com/xml/xml_elements.asp>](https://www.w3.org/)  
 The consortium develops standards and guidelines for World Wide Web technologies. There you can find all the specifications for XML and XML schema as well as many more.   
[2]: LIDO – Lightweight Information Describing Objects is an XML harvesting schema. The LIDO schema is intended for delivering metadata, for use in a variety of online services, from an organization’s online collections database to portals of aggregated resources, as well as exposing, sharing, and connecting data on the web, [LIDO schema](http://www.lido-schema.org).  
