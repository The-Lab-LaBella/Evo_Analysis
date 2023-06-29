# Evo_Analysis

## What is Evolutionary Medicine?

A central question in evolutionary medicine is "why are disease risk genetic variants still around?"

This paper on the evolution of cancer is a great read for those new to the topic: <https://onlinelibrary.wiley.com/doi/full/10.1111/eva.12034>

My favorite line from the paper is "*It is disturbing to recognize that natural selection does not shape organisms directly for health or longevity.*"

The manuscript also breaks down the reasons for disease vulnerability into 5 theories

1.  Mismatch with the modern environment

2.  Co-evolution with pathogens

3.  Constraints on selection

4.  Trade-offs

5.  Reproduction at the cost of health

6.  Evolved capacities for defense and their costs

For a deeper look at the evolution of disease traits see our review: <https://www.nature.com/articles/s41576-020-00305-9>

## Evolution in the genome

One way we can try to understand the evolutionary processes that have shaped traits is to look for imprints in the genome left behind by selection.

Our group has developed a pipeline that will characterize enrichment or depletion of metrics that have been computed to identify regions of the genome that have been impacted by

-   Negative Selection (Substitution rate, sequence conservation)

-   Positive Selection (Substitution rate, sequence conservation, haplotype structure)

-   Balancing Selection (Balanced polymorphisms)

-   Local Adaptation (Population differentiation)

This analysis will identify regions of the genome (composed of 1 to may SNPs) that have signatures consistent with these evolutionary forces.

While this analysis is helpful, we may want to know more about these regions. We can then build a theory (or evolutionary story) about *why* this signature exists in this region.

This is not an exhaustive list of potential questions to answer! This will hopefully lead you to more analyses.

## Evolutionary Checklist

First I'll give an overview of the questions I go through when investigating the evolutionary history of a region (or even a gene). Then I will go into detail about what resources I use to answer these questions.

1.  If we are analyzing a region identified in a GWAS, which alleles (or haplotype) are the **risk** alleles?

2.  What is known about the **function** of the region of interest?

3.  Are the variants associated with any changes in **gene expression**?

4.  Are the variants associated with any other traits or disorders?

5.  How deeply is the region conserved or not conserved?

6.  Do human populations vary in this region?

7.  Do associated genes have any known functions?

## Example Region

To illustrate these analyses I will provide an example analysis.

### 1. Risk allele
