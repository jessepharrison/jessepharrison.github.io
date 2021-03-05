---
layout: post
title: "Microbial community analysis tools for Chipster"
date: 2021-03-05
---

During 2020, one of my tasks was to develop a set of semi-automated tools for analysing microbial community data sets using [Chipster](https://chipster.csc.fi/), an open-source platform hosted by [CSC](https://www.csc.fi/en/). By enabling easy-to-use bioinformatics workflows that require no programming experience, Chipster aims to make computational approaches more accessible to researchers working in diverse fields.

The new tool set for microbial community comparisons, which consists of 18 new tools, was recently made available to users. In this blog post, I will briefly discuss the features offered in the first iteration of this 'community analysis toolbox'. Hope you find the new features useful! Also, as there are quite a few abbreviations, you can find a short glossary at the end of the post.

![chipster splash]({{ site.url }}/assets/img/chipster.png)
The Chipster welcome screen - as you can see, many use cases are covered...

## What's included?

As of March 2021, the toolbox makes it possible to perform OTU-based comparisons of microbial community structure using amplicon sequencing data. Several types of data sets are catered for, including bacterial, eukaryotic and archaeal rRNA gene sequencing data, as well as fungal community data based on ITS sequencing.

Which new features are available? The tools span both data processing and statistical analyses, including functions for:

- Generating and importing phyloseq input files with [mothur](https://mothur.org/)
- Data inspection and tidying (e.g. prevalence filtering and removal of low-abundance OTUs) using [phyloseq](https://joey711.github.io/phyloseq/)
- Transformations for OTU abundance tables (CLR, % relative abundance, Hellinger transformation, DESeq2 format conversion and VST)
- Ordinations (nMDS, db-RDA) and distance matrix calculation (Euclidean and Hellinger distances) using [vegan](https://cran.r-project.org/web/packages/vegan/)
- Relative abundance bar plots
- Community comparisons using PERMANOVA, PERMDISP and post-hoc pairwise comparisons
- Differential OTU abundance analysis using [DESeq2](https://bioconductor.org/packages/release/bioc/html/DESeq2.html)

The tools link with wider features in Chipster, including options for taxonomic classification using SILVA and UNITE reference databases. It is also possible to use a reference of your own. Depending on the data set, taxonomic classifications can be performed at six or seven different taxonomic levels.

## What does it look like?

The toolbox comes with an example workflow for 16S rRNA gene sequencing data, on which I also base the following snapshots showing some of the tools in action. Here's just a handful of the things we can do (for the purposes of this text, I'm focusing on the pretty pictures!).

We can generate several useful images, such as prevalence plots that can help with data processing and tidying. That part of the tool set is based on [this excellent paper](https://f1000research.com/articles/5-1492/v2) by Callahan and co-workers. 

![prevalence plot]({{ site.url }}/assets/img/chipster-prev.png)

When we've tidied the data and are ready to examine some patterns, we can produce ordinations such as this one (either with or without sample labels appended to individual data points):

![prevalence plot]({{ site.url }}/assets/img/chipster-nmds.png)

Let's say that we'd like to analyse the data using [DESeq2](https://bioconductor.org/packages/release/bioc/html/DESeq2.html). Further to a table containing more detailed analysis output, we can also visualise log-fold changes:

![deseq2]({{ site.url }}/assets/img/chipster-deseq2.png)

If you've used Chipster before, you will be familiar with the workflow screen containing information on the individual steps you've taken within a particular session. In case you're new to the platform, here is a partial preview of a workflow: 

![chipster workflow]({{ site.url }}/assets/img/chipster-workflow.png)

... Essentially, the workflow screen contains a visual representation of your entire workflow (including all output files and analysis steps). We can see how the different files and analysis results relate to one another and the different tools used. Of course, all the files can be exported to your computer, for further use. Pretty neat!

## What's next?

With these tools freshly out of the oven, the Chipster team will carefully listen to any user feedback and suggestions. Any feedback on these new features is greatly appreciated! We are also in the process of assembling a manuscript that will take readers through some example use cases and showcase the tool set in more detail.

## Brief glossary

Microbiologists love their acronyms, so here's a small list:

- CLR (centered log-ratio)
- db-RDA (distance-based redundancy analysis)
- nMDS (non-metric multidimensional scaling)
- ITS (internal transcribed spacer)
- OTU (operational taxonomic unit)
- PERMANOVA (permutational multivariate analysis of variance)
- PERMDISP (permutational analysis of multivariate dispersions)
- VST (variance-stabilising transformation)

## Last but not least...

Like many of the tools on Chipster, these ones are largely based on [mothur](https://mothur.org/) and [R](https://www.r-project.org/) scripts. Without the people developing and maintaining these (and packages including [phyloseq](https://joey711.github.io/phyloseq/), [vegan](https://cran.r-project.org/web/packages/vegan/) and [DESeq2](https://bioconductor.org/packages/release/bioc/html/DESeq2.html)), creating something like this would be far more difficult. More information on the software and R packages used can be found in the Chipster documentation.

I've also had an amazing amount of help from fellow Chipster team members (including Eija Korpelainen, Petri Klemelä, Taavi Hupponen, Ari-Matti Saren and Maria Lehtivaara), to whom I owe my thanks.

