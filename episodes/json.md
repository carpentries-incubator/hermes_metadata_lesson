---
title: "JSON"
teaching: 25
exercises: 20
---

::: questions 

- What is JSON?
- How do you annotate data in JSON?
:::

::: objectives

- Knowledge of JSON format for storing and processing metadata. 
- Familiar with the structure of a simple JSON file. 
:::

## JSON

Another format in which metadata can be stored, annotated and exchanged is JSON (JavaScript Object Notation). Its syntax is inspired by JavaScript object notation. 

::: keypoints

## JSON keypoints

* (Meta)data elements are defined in key/value pairs.
* Keys are of data type string (in quotes).
* Values must be of data type string, number (float or integer), boolean, array or object.
* Elements are separated by commas.
* Curly braces hold objects.
* Square brackets hold arrays.
* In-line commenting is not supported.
:::

#### JSON Data

JSON data is written as key/value pairs. A key/value pair consists of a key, followed by a colon, followed by a value. The key is the name – the label – for the content in the value field. Keys are always written in double quotes. The indication of the value depends on its data type. The entire content is enclosed in curly brackets. 

```JSON
{„name“ : „Kim Sneider“,
„age“ : 39,
„children“ : [„Ben“, „Tove“, „Nina“]
}
```

#### JSON vs XML

* Both are human and machine readable.
* Both can be structured hierarchical (values within values).
* Both can be parsed and used by lots of programming languages.

**But**
JSON is shorter than XML and in data processing easier to use. JSON can use arrays, so that a set of multiple values can be stored and processed easily within one key but interpreted as multiple values. Whereas in XML multiple values can be written in one tag, but they will not be processed like that as the content of a tag is not interpreted as multiple values even if the data is separated with a comma or other characters. 

#### Values

Values cannot be one of the following data types:

* a function
* a date (dates are written as strings in double quotes – so be aware of problems that may cause) 
* undefined


| data type | explanation | example as JSON value |
| ---- | ---- | ---- | ---- |
| string | set of character | "string" : „Can be a sentence or a name or a date and is written in double quotes“ |
| integer | whole number | "integer" : 12 |
| float | floating-point number | "float" :  3.5 |
| boolean | truth value | "boolean" : true/false |
| array | collection of values | "array" : [„Didi“, 35, „Whatever“, true] |
| JSON object | a set of JSON data | "object" : {„name“ : „Kim“, „age“ : 39} |

::: exercise
### Exercise

Use the artwork from the last exercise, which you have chosen from the moma_artwork.csv and write the data into a json format. 

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
This is not the only correct way to annotate the data in a json file. You can freely decide whether you want to name the keys according to the headings from the csv or whether you want to enter the information of the individual data records one-to-one as values. 

You can use a validator to check that a json file is correct. This checks the syntax of the json for formal errors, e.g., [Json Formatter & Validator](https://jsonformatter.curiousconcept.com/). 
:::


::: discussion
### Question

What do you think? Why are the values, which contain the information about the artist, created as arrays (recognizable by the square brackets), although they only contain one value? 

::: solution

Of course, there are works of art and objects made by several artists. As this is a case that certainly occurs more frequently, the data field for the value is defined directly in advance as an array in order to be able to map this case and not have to query it separately for each data record. 
:::
:::



