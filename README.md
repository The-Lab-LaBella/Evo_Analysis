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

To illustrate these analyses I will provide an example analysis. I recently conducted an evolutionary analysis for a GWAS conducted on preterm birth and gestational age. (<https://www.nature.com/articles/s41588-023-01343-9>)

One of the leading SNPs is rs7650602

***NOTE on RS numbers**:* each variant in the human genome is assigned an "rs" number. This number will reference the same position in the human genome regardless of the version of the genome. Be sure to double and triple check which version of the genome you are using if you are identifying a SNP by the chromosome and position.

### 1. Risk allele

There is no standardized way to report which SNP allele increases or decreases disease risk. You will likely need to go into the reporting to identify the risk allele.

***Example:*** The GWAS used in this analysis reported the summary statistics as below:

|       |              |       |       |               |            |            |             |            |              |
|--------|---------|-----|-----|----------|----------|-------|--------|-------|--------|
| CHR   | POS          | EFF   | REF   | RSID          | SAMPLESIZE | EAF        | BETA        | SE         | pvalue       |
| **3** | **1.41E+08** | **T** | **C** | **rs7650602** | **192643** | **0.5233** | **-0.3122** | **0.0447** | **3.01E-12** |
| 3     | 1.41E+08     | T     | G     | rs145418929   | 171646     | 0.9736     | -0.2752     | 0.2375     | 0.2467       |
| 3     | 1.41E+08     | C     | A     | rs115605995   | 172653     | 0.9614     | 0.142       | 0.1156     | 0.2192       |

From this you can see they report an effect (EFF) and reference (REF) allele. To understand the effect the alleles have on the trait (risk of preterm birth/PTB) we need to look at the beta value

The beta value reports the per unit increase or decrease in the outcome. So for our SNP the beta value is -0.3122. Therefore there is a **decrease** in the risk of PTB associated with the effect allele (T)

Effect Allele = T = decrease risk = protective allele

Reference Allele = C = increased risk = risk allele
