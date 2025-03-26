---
title: "XML Schema"
teaching: 60
exercises: 30
---

::: questions 

- What is a XML schema? 
- What are the basic elements of a XML schema? 
- What is a XML Schema used for?
:::

::: objectives

- Knowledge of basic elements of a XML Schema.
- Familiar with the basic structure.
- Ability to understand simple XML Schemas.
:::

As you have learned there are standards for annotating data in the Humanities. To ensure that the data is properly standardized and interoperable so it can be imported in for example databases for the cultural heritage, technical schemas are used. In the field of humanities and cultural studies, this is often done by using a XML Schema. This is not the only option, but it is the most common. It describes the structure and technical rules of an XML document as well as its elements and therefore establishes rules for annotating its content. The syntax is XML. A XML Schema is stored in the .xsd (XML Schema Definition) file format. 

It is characterised by the use of a schema tag as the container element for the whole document: 

```xsd
<xs:schema>

</xs:schema>

<xsd:schema>

</xsd:schema>
```

The prefix „xs“ or "xsd" denotes the namespace for the Schema (remember not to use : in XML tags, it is reserved for that!). 

### Namespaces

::: callout
A namespace contains a set of rules and is defined in the xsd file. Existing namespaces can also be integrated there and these rules are also referenced in an XML document. 
::: 

The namespace mechanism for XML data was developed by the W3 Consortium[1]. A namespace is a set of rules and therefore provides specifications of XML elements and attributes. It describes, for example, how elements and attributes are named or used. A namespace can be stored technically in the form of an xsd file or in the form of theoretical documentation. Technical specifications can be requirements for data types or minimum or maximum values. Documentation usually describes contextual relationships or rules for the use of controlled vocabularies or thesauri. Specifications from the documentation may be technically incorporated into the schema. Otherwise, they can be found in the file as comments. 

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

The xs:annotation is a container in which additional information can be embedded. If xs:documentation is used within the container, the information is processed in a human-readable way. If xs:appinfo is used within it, these are additional machine-readable notes. 


Namespaces are specified for two reasons: First, they define elements and attributes more precisely, especially when they have different meanings in different sources and specifications from different standards need to be combined. Remember the problem with dates and names. They are a very common element and should be defined precisely. How should the date be recorded? As a time span or as an ISO value? Are first and last names recorded separately? Since there may be different rules in each standard, but they may refer to the same field name, namely "date" or "name," it is important to specify the source of the rules.  

Second, they group together all the elements and attributes of an XML application so that software can easily recognize them.

A namespace is assigned in the header of the file by specifying a URI. 

```xsd
<xs:schema xmlns="http://www.w3.org/2001/XMLSchema">
```

The xmlns specification and the URI behind it refer to the W3 consortium namespace for an XML Schema as the standard for the entire document. All elements and attributes are defined according to this namespace. The URI (Uniform Resource Identifier) serves as a unique identifier as a reference to the specifications, but does not have to be a web address. Ideally, a web address is used that points to the underlying standard in the form of the xsd file and/or its documentation. 

If multiple standards are used, or parts of other Schemas are adopted, a prefix should be assigned to the namespaces in order to know which elements or attributes belong to which standard:

```xsd
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
	xmlns:xlink="http://www.w3.org/1999/xlink">
```

In the file, the prefix refers to the standard used for that element or attribute. In the example above, the xlink namespace is also used. This specification defines the XML Linking Language (XLink) version 1.1, which allows elements to be inserted into XML documents to create and describe links between resources.

When specifying multiple standards, if no prefix is specified for a standard, that standard is the default specification for the entire document and all elements without a prefix refer to that standard. 

In addition, when creating an xsd file for a specially developed standard, a targetNamespace is specified. This is the name of the namespace whose technical details are defined in this xsd file and which is then referenced in the XML document. 

```xsd
<xs:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  targetNamespace="lbacao"
  xmlns:lc="lbacao"
  elementFormDefault="qualified"
  attributeFormDefault="unqualified">
```

The default namespace in this example is the xsd namespace. A new namespace is created with this file: the lbacao namespace. All elements which does not refer to the xsd namespace would be marked with the prefix lc. 

Other namespaces can also be imported into the schema with the following specification, allowing additional software (validators) to check compliance with this standard:

```xsd
<xs:import namespace="http://www.w3.org/XML/1998/namespace" schemaLocation="http://www.w3.org/2001/03/xml.xsd">
```

The schemaLocation refers directly to the associated Schema - the xsd file - whose specifications are adopted for the document. Special software (validators) can be used to check whether an XML document conforms to the technical rules specified in an xsd file. 

### Simple Element 

A simple XML element is defined in the Schema by the specification xs:element and minimum the attributes name and type. 

```xsd
<xs:element name="descriptive name" type="string"></xs:element>
```

For example, we can specify that a place is always called place and that the character type of the content is a string. This specification prevents the tag from being sometimes called place, sometimes location or even city:

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

Using xs:pattern you can set restriction on a series of numbers or letters. There are other constraints for values in XML, e.g., whiteSpace or length:

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

What you will see more often in metadata schemas is the so-called complexType. This allows the element (later data field) to be defined much more precisely. Using this type it is possible to create for example a group with child elements and assign attributes to elements. 

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

This is proposed for the definition of an object, e.g., of the cultural heritage. Data fields are defined for the object itself, such as a title and creator or medium. At least one creator must be entered in the block for the object. The xs:sequence element (called "indicator") specifies that the child elements must appear in the given sequence. Each child element can occur from 0 to any number of times. In addition, the creator's details are recorded in the second block, along with the life data. Only one creator's name may be entered in this block, so if there are multiple, each will receive its own details in a separate block. 

Xsd provides more indicators to order the elements or to define occurrence of elements:

**Order indicators**, used to define the order of the elements, treated as tags:

-  All - The all indicator specifies that the child elements can appear in any order, and that each child element must occur only once. 
-  Choice - The choice indicator specifies that either one child element or another can occur.
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

Of course, it is also possible to assign further attributes to the elements of a complexType. To do this, the attribute itself is created in the form of a simple element and assigned to the corresponding element to which it is to apply. 

```xsd
<!-- attribute covers the object element -->
<xs:element name"object" type="string">
  <xs:complexType name="objectType" abstract="true">
    <xs:element name="title" type="string" maxOccurs="1/> 
    <xs:attribute name="lang" type="string" default=“EN“/>
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

In the first example above an attribute for the language is defined which is valid for the entire element. In the absence of a specified language, 'English' is assumed as the default value. In the second example the attribute is defined as a child element of the element "place" and therefore only valid for this element. 

Instead of a default value, the value can also be fixed:

```xsd
<xs:attribute name="lang" type="string" fixed="EN"/>
```

It should be noted that all attributes are optional by default when creating the XML element, unless the use of the attribute is specified as

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

In the simpleType the requirement for a GND identifier as a string data type is set. This defined "tGNDID" type is used as an attribute in the complexType for the historical person. The complexType for the historical person is then again used as a type for the element "aussteller" in the complexType "rUrkunde". 


The XML output would look like that:

```xml
<urkunde> 
  <aussteller gndid="https://d-nb.info/gnd/2001630-X">
    <typ>corporation</typ>
    <name>University of Marburg</name>
  </aussteller> 
</urkunde> 
``` 

The methods presented can also be nested within one another: 

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



----
[1]: [The World Wide Web Consortium (W3C)](https://www.w3schools.com/xml/xml_elements.asp>](https://www.w3.org/)  
 The consortium develops standards and guidelines for World Wide Web technologies. There you can find all the specifications for XML and XML schema as well as many more. 
[2]: LIDO – Lightweight Information Describing Objects is an XML harvesting schema. The LIDO schema is intended for delivering metadata, for use in a variety of online services, from an organization’s online collections database to portals of aggregated resources, as well as exposing, sharing, and connecting data on the web, [LIDO schema](http://www.lido-schema.org).  
