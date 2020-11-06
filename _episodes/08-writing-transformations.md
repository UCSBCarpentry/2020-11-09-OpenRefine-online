---
title: "Writing Transformations"
teaching: 5
exercises: 10
questions:
- "Where do I write GREL expressions in the OpenRefine interface?"
- "How do I write a valid GREL expression?"
objectives:
- "Explain how to write one's own transformations using GREL"
keypoints:
- "You can alter data in OpenRefine based on specific instructions"
- "You can preview the results of your GREL expression"
---

## Writing transformations

To start writing transformations, select the column on which you wish to perform a transformation and choose ```Edit cells->Transform…```. In the screen that displays you have a place to write a transformation (the 'Expression' box) and then the ability to Preview the effect the transformation would have on 10 rows of your data.

The transformation you type into the 'Expression' box has to be a valid GREL expression. The simplest expression is simply the word 'value' by itself - which simply means the value that is currently in the column - that is: make no change.

GREL functions are written by giving a value of some kind (a text string, a date, a number etc.) to a GREL function. Some GREL functions take additional parameters or options which control how the function works. GREL supports two types of syntax:

* ```value.function(options)```
* ```function(value, options)```

Either is valid, and which is used is completely down to personal preference. In these notes the first syntax is used.

Next to the 'Preview' option are options to view:

* 'History' - a list of transformations you've previously used with the option to reuse them immediately or to 'star' them for easy access
* 'Starred' - a list of transformations you've 'starred' via the 'History' view
* 'Help' - a list of all the GREL functions and brief information on how to use them

>## Changing Separators Between Values
>Let's create a text facet for the "Keywords" column 
>Use Facets and the GREL expression ```value.replace()``` to replace the commas by semi-colons
>1. Click the dropdown menu on the "Subject" column
>2. Choose ```Edit cells->Transform...```
>3. In the Expression box type ```value.replace(',',';')```
>4. In the Preview pane you can see what the effect of running this will be
>5. Click ```OK```
{: .checklist}

>## What is the most frequent individual `Subject` among the journals listed in the dataset?
> Use `facetting`, perform `transformation` and `common transformation`, as well as the `splitting` function to come up with a solution. Tip: we do not want to differentiate subject levels.
>>## Solution
>>1. Create a text facet for the 'Subject' column
>>2. Notice that top-level subjects are separated by vertical bars `|` and same level by periods `.`, and colons `:` for sub-topics
>>3. We will need to perform transformations to remove these different separators. We will separate all of them by semi-colons `;`
>>>3.1 value.replace('|', ';')
>>>3.2 value.replace('.', ';')
>>>3.3 value.replace(':', ';')
>>You can also combine the three separate steps above into one expression. Note that you don't have to type `value` multiple times:
>>value.replace('|', ';').replace.('.', ';').replace.(':', ';')
>>4. Apply the common transformation to remove unwanted spaces.
>>5. Use de function split multi-valued cells using the semi-colons `;` as the separator
>>6. Sort the facet by `count`
>>7. Which subject has more counts? Answer: **Medicine - 243**
>{: .solution}
{: .challenge}
