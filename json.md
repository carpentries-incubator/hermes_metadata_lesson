---
title: "JSON"
teaching: 15
exercises: 20
---

::: questions 

- What is JSON?
- How do you annotate data in JSON?
:::

::: objectives

- Understand the JSON format for storing and processing metadata. 
- Learn the structure of a simple JSON file. 
:::


Another file format in which metadata can be stored, annotated and exchanged is JSON (JavaScript Object Notation). Its syntax is inspired by JavaScript object notation. 

## JSON Data

JSON data is written as key/value pairs. A key/value pair consists of a key, followed by a colon, followed by a value. The key is the name - the label - for the content in the value field. Keys are always written in quotation marks. How the value is marked depends on its data type. The entire content is enclosed in curly brackets. 


```JSON
[{
"name" : "Kim Sneider",
"age" : 39,
"children" : ["Ben", "Tove", "Nina"]
}]
```

## Values  

Value in a JSON file cannot be:

* a function
* a date (dates are written as strings in double quotes – so be aware of problems that might cause) 
* undefined   

#### Different Data Types as Values

| data type | explanation | example as key/value pair |
| ---- | ---- | ------ | 
| string | set of characters | "string" : „Can be a sentence or a name or a date and is written in double quotes“ |
| integer | whole number | "integer" : 12 |
| float | floating-point number | "float" :  3.5 |
| boolean | truth value | "boolean" : true/false |
| array | collection of values | "array" : [„Didi“, 35, „Whatever“, true] |
| JSON object | a set of JSON data | "object" : {„name“ : „Kim“, „age“ : 39} |                           
  
  
## JSON vs XML

* Both are human and machine readable.
* Both can be structured hierarchically (values within values).
* Both can be parsed and used by many programming languages.

**But**
JSON is shorter than XML and easier to use in data processing. JSON can use arrays, so a set of multiple values can be stored and easily processed within a key, but interpreted as multiple values. XML, on the other hand, allows multiple values to be written in a tag, but they are not processed as such because the contents of a tag are not interpreted as multiple values, even if the data is separated by a comma or other character.
  

::: challenge
### Exercise

Use the artwork that you chose from moma_artwork.csv in the previous exercise and write the data in JSON format this time. 

::: solution

```json
[{
  "Title": "Green-Blue-Red (for Parkett no. 35)",
  "Artist": [
    "Gerhard Richter"
  ],
  "ConstituentID": [
    4907
  ],
  "ArtistBio": [
    "German, born 1932"
  ],
  "Nationality": [
    "German"
  ],
  "BeginDate": [
    1932
  ],
  "EndDate": [
    0
  ],
  "Gender": [
    "male"
  ],
  "Date": "1993",
  "Medium": "Multiple of oil on canvas",
  "Dimensions": "composition: 11 7/16 × 15 3/4\" (29 × 40 cm); sheet: 11 3/4 × 15 3/4\" (29.9 × 40 cm)",
  "CreditLine": "Riva Castleman Endowment Fund, Lily Auchincloss Fund, and Gift of Parkett",
  "AccessionNumber": "110.1998.1",
  "Classification": "Multiple",
  "Department": "Drawings & Prints",
  "DateAcquired": "1998-03-05",
  "Cataloged": "Y",
  "ObjectID": 61953,
  "URL": "https://www.moma.org/collection/works/61953",
  "ImageURL": null,
  "OnView": "",
  "Height (cm)": 29.0,
  "Width (cm)": 40.0
},
{
  "Title": "Untitled",
  "Artist": [
    "Blinky Palermo"
  ],
  "ConstituentID": [
    4474
  ],
  "ArtistBio": [
    "German, 1943–1977"
  ],
  "Nationality": [
    "German"
  ],
  "BeginDate": [
    1943
  ],
  "EndDate": [
    1977
  ],
  "Gender": [
    "male"
  ],
  "Date": "1970",
  "Medium": "Dyed cotton mounted on muslin",
  "Dimensions": "6' 6 3/4\" x 6' 6 3/4\" (200 x 200 cm)",
  "CreditLine": "Gift of Jo Carole and Ronald S. Lauder",
  "AccessionNumber": "650.1997",
  "Classification": "Painting",
  "Department": "Painting & Sculpture",
  "DateAcquired": "1997-06-02",
  "Cataloged": "Y",
  "ObjectID": 78283,
  "URL": "https://www.moma.org/collection/works/78283",
  "ImageURL": "https://www.moma.org/media/W1siZiIsIjE1MTQ0MCJdLFsicCIsImNvbnZlcnQiLCItcmVzaXplIDEwMjR4MTAyNFx1MDAzZSJdXQ.jpg?sha=c54d00f27ed284be",
  "OnView": "",
  "Height (cm)": 200.0,
  "Width (cm)": 200.0
},
{
  "Title": "Daylight Savings Time",
  "Artist": [
    "Pierre Roy"
  ],
  "ConstituentID": [
    5065
  ],
  "ArtistBio": [
    "French, 1880–1950"
  ],
  "Nationality": [
    "French"
  ],
  "BeginDate": [
    1880
  ],
  "EndDate": [
    1950
  ],
  "Gender": [
    "male"
  ],
  "Date": "1929",
  "Medium": "Oil on canvas",
  "Dimensions": "21 1/2 x 15\" (54.6 x 38.1 cm)",
  "CreditLine": "Gift of Mrs. Ray Slater Murphy",
  "AccessionNumber": "1.1931",
  "Classification": "Painting",
  "Department": "Painting & Sculpture",
  "DateAcquired": "1931-01-19",
  "Cataloged": "Y",
  "ObjectID": 78294,
  "URL": "https://www.moma.org/collection/works/78294",
  "ImageURL": "https://www.moma.org/media/W1siZiIsIjIzMzkzNyJdLFsicCIsImNvbnZlcnQiLCItcmVzaXplIDEwMjR4MTAyNFx1MDAzZSJdXQ.jpg?sha=74825d4c62cd5a8a",
  "OnView": "",
  "Height (cm)": 54.6,
  "Width (cm)": 38.1
},
{
  "Title": "The Bather",
  "Artist": [
    "Paul Cézanne"
  ],
  "ConstituentID": [
    1053
  ],
  "ArtistBio": [
    "French, 1839–1906"
  ],
  "Nationality": [
    "French"
  ],
  "BeginDate": [
    1839
  ],
  "EndDate": [
    1906
  ],
  "Gender": [
    "male"
  ],
  "Date": "c. 1885",
  "Medium": "Oil on canvas",
  "Dimensions": "50 x 38 1/8\" (127 x 96.8 cm)",
  "CreditLine": "Lillie P. Bliss Collection",
  "AccessionNumber": "1.1934",
  "Classification": "Painting",
  "Department": "Painting & Sculpture",
  "DateAcquired": "1934-09-23",
  "Cataloged": "Y",
  "ObjectID": 78296,
  "URL": "https://www.moma.org/collection/works/78296",
  "ImageURL": "https://www.moma.org/media/W1siZiIsIjQ0NjA2NyJdLFsicCIsImNvbnZlcnQiLCItcmVzaXplIDEwMjR4MTAyNFx1MDAzZSJdXQ.jpg?sha=c6bd692fa0fe0685",
  "OnView": "\"MoMA, Floor 2, 2 South\"",
  "Height (cm)": 127.0,
  "Width (cm)": 96.8
},
{
  "Title": "Syntheses of Naples",
  "Artist": [
    "Enrico Prampolini"
  ],
  "ConstituentID": [
    4720
  ],
  "ArtistBio": [
    "Italian, 1894–1956"
  ],
  "Nationality": [
    "Italian"
  ],
  "BeginDate": [
    1894
  ],
  "EndDate": [
    1956
  ],
  "Gender": [
    "male"
  ],
  "Date": "before 1930",
  "Medium": "Oil on canvas",
  "Dimensions": "39 3/8 x 39 1/2\" (100 x 100.3 cm)",
  "CreditLine": "Gift of Dr. Julius Spitzer",
  "AccessionNumber": "1.1942",
  "Classification": "Painting",
  "Department": "Painting & Sculpture",
  "DateAcquired": "1941-12-10",
  "Cataloged": "Y",
  "ObjectID": 78299,
  "URL": "https://www.moma.org/collection/works/78299",
  "ImageURL": "https://www.moma.org/media/W1siZiIsIjE4NjgzNSJdLFsicCIsImNvbnZlcnQiLCItcmVzaXplIDEwMjR4MTAyNFx1MDAzZSJdXQ.jpg?sha=9740d0c731c867c2",
  "OnView": "",
  "Height (cm)": 100.0,
  "Width (cm)": 100.3
}]
```
This is not the only correct way to annotate the data in a JSON file. You are free to choose, e.g., whether you want to name the keys according to the headings in the CSV, or you want to enter the information from each record one-to-one as values. You can also choose other ways to structure the data, for example:

```json
[{
  "artwork" : {"separatePairs" : "containing all information only on the artwork as separate key/value pairs",
                "title" : "title",
                "artist" : "artist",
                "year" : 2025},
  "artist" : {"artistInformation" : "containing all information only on the artist",
                "ArtistBio": ["Nationality, Lifespan"],
                "Nationality": "Somewhere",
                "BeginDate": 1000,
                "EndDate": 2000,
                "Gender": "gender"},           
  "administrativeData" : {"informationAdData" : "containing all information only on the administrative data of the recording",
                "DateAcquired": "1941-12-10",
                "Cataloged": "Y", 
                "OnView": ""}
}]
```  

You can use a validator - such as [Json Formatter & Validator](https://jsonformatter.curiousconcept.com/) - to check whether a JSON file is formatted correctly.
:::
:::




::: challenge
### Question

Why are the values containing the artist information created as arrays (recognisable by the square brackets), even though they contain only one value?

::: solution


There are works of art and objects made by several artists. As this is a common case, the data field for the value is defined as an array in advance, to be able to handle this case and not have to query it separately for each record.
:::
:::  

::: keypoints

* (Meta)data elements are defined in key/value pairs.
* Keys are strings and appear in quotation marks.
* Values can be strings, numbers (float or integer), boolean, arrays or objects.
* Elements are separated by commas.
* Curly brackets contain objects.
* Square brackets contain arrays.
* In-line comments are not supported.
:::
