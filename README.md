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

2.  What is known about the **consequence** of the variation in the region of interest?

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

## 2. Known variant consequences?

Many SNPs in the human genome have confirmed or hypothesized functions. There are several resources we can turn to to find these confirmed or known consequences.

**NIH dbSNP** <https://www.ncbi.nlm.nih.gov/snp/>

![](images/snpdb.png){width="516"}

In dbSNP we can see that this variant rs7650602 is in the **intron of the gene ZBTB38**

**Ensembl** snp data ( <https://useast.ensembl.org/index.html> )

![](images/ensembl.png){width="444"}

The Ensembl data agrees with the data in the dbSNP. You can also see there is a link to "See all predicted consequences". This link will take you to see all the predicted consequences if there is more than one.

## Expression Consequences

Many common variants in the human genome have a regulatory function. If we were to find variants that result in non-synonymous changes (aka change amino acid sequences) we would turn to predictions of protein structure. These variants, however, often have severe consequences and are more likely to result in Mendelian disorders.

Determining the regulatory function of a region in the human genome is challenging! But there are several databases that can help us understand which genes may be affected by variation at our SNP.

**RegulomeDB** (<https://regulomedb.org/> )

RegulomeDB has *a lot* of information. You can find information about the various sections here (<https://regulomedb.org/regulome-help/#FAQ>)

Let's walk through it.

![](images/rdb1.png){width="456"}

First you will see the coordinates of the genome (in HG38 if you used the default). In this section the most important thing to look at is the **rank**

The ranks range from 1 (most evidence) to 7 (least evidence) for data indicating that this variant is found in a regulatory region.

![](images/dbrank.png){width="463"}

Our SNP has a score of 1f which indicates that there is an eQTL (more to come on this) and either TF binding or a chromatin accessibility peak there.

So, **we have good evidence that our SNP is in a regulatory region**

### ChIP data

ChIP stands for Chromatin immunoprecipitation

You can learn more here: <https://www.youtube.com/watch?v=7_-Or4ARyH0> and <https://en.wikipedia.org/wiki/Chromatin_immunoprecipitation>

The premise of ChIP is that you are able to **sequence the DNA bound to specific proteins**. You tightly bind (cross-link) DNA to Proteins and then selectively isolate the proteins (immunoprecipitation). Then sequence *only* the DNA bound to your protein. You can then generate a map of *where* your protein was bound to the genome.

Our SNP has no ChIP data but I will use a **different SNP** to demonstrate what the results would look like.

Results for SNP rs1316379

![](images/CHIP.png){width="149"}

![](images/chip_table.png)

From this data we can see that two proteins ZFP82 and CEBPA are bound to our region of interest and in which organ this was detected. There is very good evidence that these two proteins can bind to our region.

### Chromatin State

DNA is not floating around our cells as double-stranded DNA. Instead DNA is highly organized into three-dimensional structures. The basic structure of DNA is the nucleosome where DNA wraps around histones (euchromatin). These histones then wrap into a fiber (heterochromatin).

When DNA is wrapped up into chromatin, it cannot be expressed. (see more here: <https://www.khanacademy.org/science/ap-biology/gene-expression-and-regulation/regulation-of-gene-expression-and-cell-specialization/v/dna-and-chromatin-regulation> )

By looking to see if our DNA if interest is exposed (not wrapped up in chromatin) we can ask if this region is transcriptionally active in particular tissues.

The chromatin state provided in regulomeDB is often the result of an analysis conducted in chromHMM ( <https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3577932/> )

The various chromatin states predicted are summarized below

![](images/chrom_state.png)

For our region the chromatin state has been found to be associated most frequently with weak transcription or active enhancer activity.

![](images/chromatin.png){width="367"}

From the summary figure we can see that

### Genome Browser 

You **must click on the link** to see your region in the genome browser. (the snapshot is not of our region)

![](images/genome_Browserdb-01.png)

The genome browser gives us an overview of the location of our SNP (yellow line). There are over 422 tracks (data sets) that you can view on the genome browser.
