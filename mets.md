---
title: "Metadata Encoding & Transmission Standard (METS)"
teaching: 15
exercises: 20
---

::: questions 

- What is the Metadata Encoding & Transmission Standard?
- What are its important elements? 

:::

::: objectives

- Learn the basics of the Metadata Encoding & Transmission Standard
- Learn to structure data in METS
:::

## METS Metadata Encoding & Transmission Standard

Provided by the Library of Congress, METS is an XML format defined by XML Schema for describing digital collections of objects with metadata. The standard does not specify a name or order for the metadata fields themselves, but serves to structure them in a standardised way. It is often used for long-term preservation. Metadata is added in one of seven domains:  

1. METS Header: Metadata describing the METS document itself, including such information as creator, editor, etc.
2. Descriptive Metadata Section: The section may point to descriptive metadata external to the METS document, or contain internally embedded descriptive metadata, or both. 
3. Administrative Metadata Section: provides information regarding how the files were created and stored, intellectual property rights, metadata regarding the original source object from which the digital library object derives, and information regarding the provenance of the files comprising the digital library object 
4. File Section: lists all files containing content which comprise the electronic versions of the digital object. 
5. Structural Map: It outlines a hierarchical structure for the digital library object, and links the elements of that structure to content files and metadata that pertain to each element.
6. Structural Links: to record the existence of hyperlinks between nodes in the hierarchy outlined in the Structural Map.
7. Behavioral Section: can be used to associate executable behaviors with content in the METS object.

XML syntax:   

```XML
<mets>
 <metsHdr/><!-- METS Header -->
 <dmdSec/><!-- Descriptive Metadata Section -->
 <amdSec/><!-- Administrative Metadata Section -->
 <fileSec/><!-- File Section -->
 <structMap/><!-- Structural Map -->
 <structLink/><!-- Structural Links -->
 <behaviorSec/><!-- Behavioral Section -->
</mets>
```
  
::: challenge

### Exercise Part I

Use the example from the XML exercise and assign the metadata elements to the structure of the METS standard. 

::: solution 

### Solution


```XML
<mets>
 <metsHdr>
  <creator>Moma</creator>
  <editor>me</editor>
  <creationdate>today</creationdate>
 </metsHdr>

 <dmdSec>
  <artwork>
    <title>Green-Blue-Red (for Parkett no. 35)</title>
    <date>1993</date>
    <medium>Multiple of oil on canvas</medium>
    <dimensions>composition: 11 7/16 × 15 3/4&quot; (29 × 40 cm); sheet: 11 3/4 × 15 3/4&quot; (29.9 × 40 cm)</dimensions>
    <department>Drawings &amp; Prints</department>
  <artist>
    <name>Gerhard Richter</name>
    <constituentID>4907</constituentID>
    <artistBio>
      <bio>German, born 1932</bio>
    </artistBio>
    <nationality>German</nationality>
    <beginDate>1932</beginDate>
    <endDate>0</endDate>
    <gender>male</gender>
  </artist>
 </dmdSec>   
    
 <amdSec>
  <creditLine>Lillie P. Bliss Collection</creditLine>
  <accessionNumber>1.1934</accessionNumber>
  <dateAcquired>1998-03-05</dateAcquired>
  <cataloged>Y</cataloged>
  <objectID>61953</objectID>
 </amdSec>

 <fileSec>
  <url>https://www.moma.org/collection/works/78296</url>
  <imageURL>https://www.moma.org/media/W1siZiIsIjQ0NjA2NyJdLFsicCIsImNvbnZlcnQiLCItcmVzaXplIDEwMjR4MTAyNFx1MDAzZSJdXQ.jpg?sha=c6bd692fa0fe0685</imageURL>
  <onView>&quot;MoMA, Floor 2, 2 South&quot;</onView>
 </fileSec>

 <structMap/>

 <structLink/>

 <behaviorSec/>
  <onView></onView>

</mets>
```
:::
:::  

::: challenge

### Exercise Part II

You can find examples for structured data in the METS standard on the [website of the Library of Congress](https://www.loc.gov/standards/mets/mets-examples.html). What do you notice? 

::: solution

### Solution

You can figure out that:  
- In many examples the MODS standard is used within the METS structure.  
- The last sections are often missing or do not contain much data.  
- The amdSec contains technical information on the technical means of digitisation such as camera or scanner and their settings.   
- The amdSec is sometimes divided into further sections, e.g., rights and technical data.
:::
:::

::: keypoints
METS serves as a container for structuring metadata. The metadata fields are usually integrated into the METS structure in a specific standard for the individual fields and their order. These include standards such as Cublin Core, MODS, or MARC.
:::
