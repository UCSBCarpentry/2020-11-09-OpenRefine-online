---
title: "Introduction to Transformations"
teaching: 5
exercises: 5
questions:
- "How do I use transformations to programmatically edit my data?"
- "What are the kind of transformations Open Refine supports?"
- "What is GREL?"
objectives:
- "Describe common transformations"
- "Explain GREL, the General Refine Expression Language"
keypoints:
- "Common transformations are available through the Menu option"
---

## Introducing Transformations

Through facets, filters and clusters OpenRefine offers relatively straightforward ways of getting an overview of your data, and making changes where you want to standardise terms used to a common set of values.

However, sometimes there will be changes you want to make to the data that cannot be achieved in this way. Such types of changes include:

* Splitting data that is in a single column into multiple columns (e.g. splitting an address into multiple parts)
* Standardising the format of data in a column without changing the values (e.g. removing punctuation or standardising a date format)
* Extracting a particular type of data from a longer text string (e.g. finding ISBNs in a bibliographic citation)

To support this type of activity OpenRefine supports 'Transformations' which are ways of manipulating data in columns. Transformations are normally written in a special language called 'GREL' (General Refine Expression Language). To some extent GREL expressions are similar to Excel Formula, although they tend to focus on text manipulations rather than numeric functions.

Full documentation for the GREL is available at [https://github.com/OpenRefine/OpenRefine/wiki/General-Refine-Expression-Language](https://github.com/OpenRefine/OpenRefine/wiki/General-Refine-Expression-Language). This tutorial covers only a small subset of the commands available.

### Common transformations
OpenRefine features several functions for performing commonly needed transformations to your data. Many of these transformations are intended for data cleaning purposes and can also be done by using regular expressions. Some transformations are used regularly and are accessible directly through menu options, without having to type them directly. To locate these transformations:

1. Go to the column you would like to make edits to and click the arrow button on the column header
2. Select the “Edit cells” and then “Common transforms” options

Examples of some of these common transformations are given in the table below:

| Transformation 	| Function 	|
|-	|-	|
| Trim leading and trailing whitespace 	| Removes extra spaces before and after the value in each cell in   the selected column. 	|
| Collapse consecutive whitespace 	| Removes extra spaces between   individual strings within a cell value in the selected column. 	|
| Unescape HTML entities 	| Removes HTML strings indicating particular characters (e.g.,   “&” vs “&amp;amp;”). 	|
| Replace Smart quotes with ascii 	| Replaces Smart quotes to their   ASCII (e.g. ' and ") 	|
| To titlecase 	| Changes the first letter of all words within a cell value to an   uppercase letter. 	|
| To uppercase 	| Changes all letters of all words   within a cell value to uppercase letters. 	|
| To lowercase 	| Changes all letters of all words within a cell value to   lowercase letters. 	|
| To number 	| Changes the cell format to number. 	|
| To date 	| Changes the cell format to date. 	|
| To text 	| Changes the cell format to text. 	|
| To null 	| Changes the cell format to null. 	|
| To empty string 	| Changes the cell format to empty string. 	|


>## Removing Unnecessary Spaces Without Inspecting All Facet Choices
>1. Create a text facet on the "Society or Institution" Column
>2. Note that you have over 300 choices listed and would take too much time to inspect each of them
>3. On the column use the dropdown menu to select ```Edit cells->Common transforms->Trim leading and trailing whitespace```
>4. Note the message that appears on the top and the expression
>5. Then, ```Edit cells>Common transforms>Collapse consecutive whitespace```. Pay attention to the message again.
>6. Look at the facet now - has it changed at all or the number remains the same? Do you know why?
{: .checklist}

>## Transforming Text Facet into Dates
>By default, in `OpenRefine` all columns are identified as text. So if you want to create a date facet you will have to first transform those values into 'dates'. 
>1. Click on the column `Added on Date` dropdown menu, then `Edit Cells>Common Transforms>To Date`
>2. Now, perform a `Timeline Facet`
>3. Can you spot a time period when there was a large number of journals added to DOAJ?
{: .checklist}

>## Challenge
>Now, try the same process with the `Most Recent Article` column. What is the peak timeline for this variable? How many cases fall under this peak?
>>## Solution 
>>``The peak time was in between October 28, 2019 and Octover 27, 2020`` and ``291 cases according to row numbers``
>{: .solution}
{: .challenge}
