---
title: "Clustering"
teaching: 10
exercises: 10
questions:
- "What is Clustering in OpenRefine and when would you use it?"
- "How does clustering work in OpenRefine?"
objectives:
- "Explain what clustering is in OpenRefine"
- "Use clustering to identify and fix replace varying forms of the same data with a single consistent value"
keypoints:
- "Clustering is a way of finding variant forms of the same piece of data within a dataset (e.g. different spellings of a name)"
- "There are a number of different Clustering algorithms that work in different ways and will produce different results"
- "The best clustering algorithm to use will depend on the data"
- "Using clustering you can replace varying forms of the same data with a single consistent value"
---

## Clustering
The Cluster function groups together similar, but inconsistent values in a given column and lets you merge these inconsistent values into a single value you choose.

This is very effective where you have data with minor variations in data values, e.g. names of people, organisations, places, classification terms.

To use the 'Cluster' function, click on the `Edit Cells` menu option in the relevant column and choose `Cluster and edit...`

The 'Clusters' are created automatically according to an algorithm. OpenRefine supports a number of different clustering algorithms - some experimentation may be required to see which clustering algorithm works best with any particular set of data, and you may find that using different algorithms highlights different clusters.

For more information on the methods used to create Clusters, see [https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth](https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth)

For each cluster, you have the option of 'merging' the values together - that is, replace the various inconsistent values with a single consistent value. By default, OpenRefine uses the most common value in the cluster as the new value, but you can select another value by clicking the value itself, or you can simply type the desired value into the 'New Cell Value' box.

>## Use Clustering to clean up author data
>
>1. Split out the author names into individual cells using `Edit cells -> Split multi-valued cells`, using the pipe ( \| ) character as the separator
>2. Choose `Edit cells -> Cluster and edit` from the 'author' column.
>3. Using the `key collision` method with the `fingerprint` Keying Function, work through the clusters of values, merging them to a single value where appropriate
>4. Try changing the clustering method being used - which ones work well?
{: .challenge}

>## Challenge: Clean up 2 variables
>
> Let's clean up our new, larger DOAJ file.
> There are several publishers that appear to be the same organization. Combine them.
> * How many publishers did you start with? How many are left after cleaning?
> * You can also eliminate redundant values in the 'Permanent article identifiers' column.
> How few of these values can you get to?
>
> > ## Solution
> >
> > ### Combine publishers.
> > When you start, you should see 6,983 distinct publishers.
> > Click the 'Cluster' button, and you will see several publishers that appear to be
> > duplicates.  Let's paint with a broad brush, and assume that we can lump in the
> > Ljubljana filozoske fakulty with their arts faculty. We will accept all of OpenRefine's
> > other suggestions.
> >
> > If there were fuzzier matches, you could adjust the sliders on each cluster to exclude outlyers.
> > 
> > After accepting the Cluster recommendations, there should now be 6,853 distinct publishers.
> >
> > ### Combine persistant identifiers
> > 
> > Slide over to 'Permanent article identifiers' column, and create a text facet.  
> > 
> > You could try to Cluster these, but they are too self-similar. You will need to edit the values.
> > If you scroll
> > through the 35 choices, you should see at least 3 that you can safely combine. Update those 
> > by editing one of the facets to match another. (DOI, PMCID, PMID; the two UDC's;). You should 
> > get down to 32 choices at the most.  You could go lower if you have the domain knowledge necessary 
> > to combine more of the values.
> >
> {: .solution}
{: .challenge}


>## Shrink this dataset
> 15,403 records is a pretty good number to work with, but let's 
> simplify our work and filter this dataset down to just journals
> published in the United States.
>
> How many are left?
>
> > ## Solution
> >
> > After adding a text facet and including only US journals, we have 838 records.
> {: .solution}
{: .challenge}
