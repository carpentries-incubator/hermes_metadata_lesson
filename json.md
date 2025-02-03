---
title: "JSON"
teaching: 20
exercises: 1
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

::: callout 

### Boolean

Boolean is the data type for truth values in programming languages. The Boolean data type can be either true (the binary equivalent of 1) or false (the binary equivalent of 0). Programmers use Booleans to test conditions.
::: 

| data type | explanation | example as JSON value |
| ---- | ---- | ---- | ---- |
| string | set of character | "string" : „Can be a sentence or a name or a date and is written in double quotes“ |
| integer | whole number | "integer" : 12 |
| float | floating-point number | "float" :  3.5 |
| boolean | truth value | "boolean" : true/false |
| array | collection of values | "array" : [„Didi“, 35, „Whatever“, true] |
| JSON object | a set of JSON data | "object" : {„name“ : „Kim“, „age“ : 39} |


