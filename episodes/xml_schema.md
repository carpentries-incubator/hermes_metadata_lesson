---
title: "XML Schema"
teaching: 30
exercises: 15
---

::: questions 

- What is a XML schema? 
- What are the basic elements of a XML schema? 
- What is a schema used for?

:::

::: objectives

- Knowledge of basic elements of a XML schema.
- Familiar with the basics structure.
- 
:::

As you have learned there are standards for annotating data in the Humanities. To ensure that the data is properly standardized and interoperable so it can be imported in for example databases for the cultural heritage, technical schemas are used. In the field of humanities and cultural studies, this is often done by using a XML Schema. This is not the only option, but it is the most common. It describes the structure and technical rules of an XML document as well as its elements and therefore establishes rules for annotating its content. The structure is essentially the same as XML. A schema is stored in the .xsd (XML Schema Definition) file format. It is characterised by the use of a schema tag as the container element for the whole document. 

```xsd
<xs:schema>

</xs:schema>
```
The prefix „Xs“ denotes the namespace for the schema (remember not to use : in XML tags, it is reserved for that!). 

### Namespaces

An important part of a schema is the namespace. It contains a set of rules and is defined in the xsd file. Existing namespaces can also be integrated there and these rules are also referenced in an XML document. 

The namespace mechanism for XML data was developed by the W3 Consortium[1]. A namespace is a set of rules and therefore provides specifications of XML elements and attributes. It describes, for example, how elements and attributes are named or used. A namespace can be stored technically in the form of an xsd file or in the form of theoretical documentation. Technical specifications can be requirements for data types or minimum or maximum values. Documentation usually describes contextual relationships or rules for the use of controlled vocabularies or thesauri. Specifications from the documentation may be technically incorporated into the schema. Otherwise, they can be found in the file as comments. 

Namespaces are specified for two reasons: First, they define elements and attributes more precisely, especially when they have different meanings in different sources and specifications from different standards need to be combined. Remember the problem with dates and names. They are a very common element and should be defined precisely. How should the date be recorded? As a time span or as an ISO value? Are first and last names recorded separately? Since there may be different rules in each standard, but they may refer to the same field name, namely "date" or "name," it is important to specify the source of the rules.  

Second, they group together all the elements and attributes of an XML application so that software can easily recognize them.

A namespace is assigned in the header of the file by specifying a URI. 

```xsd
<xs:schema xmlns="http://www.w3.org/2001/XMLSchema">
```

The xmlns specification and the URI behind it refer to the W3 consortium namespace for an XML Schema as the standard for the entire document. All elements and attributes are defined according to this namespace. The URI (Uniform Resource Identifier) serves as a unique identifier as a reference to the specifications, but does not have to be a web address. Ideally, a web address is used that points to the underlying standard in the form of the xsd file and/or its documentation. 

If multiple standards are used, or parts of other schemas are adopted, a prefix should be assigned to the namespaces in order to know which elements or attributes belong to which standard:


```xsd
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
	xmlns:xlink="http://www.w3.org/1999/xlink">
```

In the file, the prefix refers to the standard used for that element or attribute. In the example above, the xlink namespace is also used. This specification defines the XML Linking Language (XLink) version 1.1, which allows elements to be inserted into XML documents to create and describe links between resources.

When specifying multiple standards, if no prefix is specified for a standard, that standard is the default specification for the entire document and all elements without a prefix refer to that standard. 

In addition, when creating an xsd file for a specially developed standard, a targetNamespace is specified. This is the name of the namespace whose technical details are defined in this xsd file and which is then referenced in the XML document. 

```xsd
<xs:schema targetNamespace="http://www.lido-schema.org" elementFormDefault="qualified" attributeFormDefault="qualified">
```

Other namespaces can also be imported into the schema with the following specification, allowing additional software (validators) to check compliance with this standard:

```xsd
<xs:import namespace="http://www.w3.org/XML/1998/namespace" schemaLocation="http://www.w3.org/2001/03/xml.xsd">
```

The schemaLocation refers directly to the associated schema - the xsd file - whose specifications are adopted for the document. 

Special software (validators) can be used to check whether an XML document conforms to the technical rules specified in an xsd file. 

### Simple Element 

A simple XML element is defined in the schema by the specification xs:element and minimum the attributes name and type. 

```xsd
<xs:element name=“descriptive name“ type=“string“>
```

For example, we can specify that a place is always called place and that the character type of the content is a string. This specification prevents the tag from being sometimes called place, sometimes location or even city:

```xsd
<xs:element name=“place“ type=“string“/>
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

With these restrictions for a datafield „age“, only values from 0 to 120 are allowed in the XML. 

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

Restrictions for Datatypes

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

### Complex Type

What you will see more often in metadata schemas is the so-called complexType. This allows the element (later data field) to be defined much more precisely. Using this type it is possible to create for example a group with child elements and assign attributes to elements. 

``` xsd
<xs:element name=“object“>
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

This simple schema is proposed for the definition of an object, e.g., of the cultural heritage. Data fields are defined for the object itself, such as a title and creator or medium. At least one creator must be entered in the block for the object. The /<xs:sequence/> element (called „indicator“) specifies that the child elements must appear in the given sequence. Each child element can occur from 0 to any number of times. In addition, the creator's details are recorded in the second block, along with the life data. Only one creator's name may be entered in this block, so if there are multiple, each will receive its own details in a separate block. 
Xsd provides more indicators to order the elements or to define occurrence of elements. 


Of course, it is also possible to assign further attributes to the elements of a complex type. To do this, the attribute itself is created in the form of a simple element and assigned to the corresponding element to which it is to apply. 

```xsd
<xs:attribute name="lang" type="string" default=“EN“/>
```

In the example above an attribute for the language is defined. In the absence of a specified language, 'English' is assumed as the default value. The attribute is specified with a fixed value, thus allowing for the specification of 'English' as the only permitted language:

```xsd
<xs:attribute name="lang" type="string" fixed=“EN“/>
```

It should be noted that all attributes are optional by default when creating the XML element, unless the attribute is specified as

```xsd
 <xs:attribute name=“name“ use=“required“/>
```

An XML that conforms to a schema is called valid.

:::

### Exercise

Use your example from the xml exercise. Write a short schema for the artist's data. Integrate the following conditions: 

- 

::: solution

```xml

```

:::
:::

----
[1]: [The World Wide Web Consortium (W3C)](https://www.w3schools.com/xml/xml_elements.asp>](https://www.w3.org/)  
 The consortium develops standards and guidelines for World Wide Web technologies. There you can find all the specifications for XML and XML schema as well as many more. 
