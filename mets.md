---
title: "Metadata Encoding & Transmission Standard (METS)"
teaching: 20
exercises: 1
---

::: questions 

- What is the Metadata Encoding & Transmission Standard?
- What are its important elements? 

:::

::: objectives

- Knowledge of the basics of the Metadata Encoding & Transmission Standard
- Familiar with the important elements for structuring data in METS
:::

## METS Metadata Encoding & Transmission Standard

The standard is overseen by the Library of Congress.

METS is an XML format defined by XML Schema for describing digital collections of objects with metadata. The standard does not specify a name or 
order for the metadata fields per se, but serves to structure them in a standardized way. It is often used for long-term archiving. The metadata are added in one of seven domains: 

1. METS Header: Metadata describing the METS document itself, including such information as creator, editor, etc.
2. Descriptive Metadata Section: The section may point to descriptive metadata external to the METS document, or contain internally embedded descriptive metadata, or both. 
3. Administrative Metadata Section: provides information regarding how the files were created and stored, intellectual property rights, metadata regarding the original source object from which the digital library object derives, and information regarding the provenance of the files comprising the digital library object 
4. File Section: lists all files containing content which comprise the electronic versions of the digital object. 
5. Structural Map: It outlines a hierarchical structure for the digital library object, and links the elements of that structure to content files and metadata that pertain to each element.
6. Structural Links: to record the existence of hyperlinks between nodes in the hierarchy outlined in the Structural Map.
7. Behavioral Section: can be used to associate executable behaviors with content in the METS object.

```XML
<mets>
 <metsHdr/>
 <dmdSec/>
 <amdSec/>
 <fileSec/>
 <structMap/>
 <structLink/>
 <behaviorSec/>
</mets>
``` 
METS serves as a container for structuring metadata. The metadata fields are usually integrated into the METS structure in a specific standard for the individual fields and their order. 
These include standards such as Cublin Core, MODS, or MARC.



