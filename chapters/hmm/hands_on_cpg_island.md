# Hands-on Activity: Identifying CpG islands in long stretch of DNA 

## Objectives
- Implement an HMM to identify CpG islands
- Compare the obtained CpG islands against other functional annotations


## Background
In the previous hands-on activity, we found that the CpG dinucleotides (we write ''CpG'' to emphasize that the C and G are on the same strand connected at the **p**hospate backbone) are rare in the human genome. How about their positional distribution? Are CpGs rare throughout ? 

One theory for why CpG is rare is that cytosines in CpG sites are easily methylated (a methyl group attaches at one of the carbons) and methylated cytosines turn into thymines at a high rate. Over evolutionary time scale, many CpGs are lost. There are however regions of non-methylated CpGs. These regions are known to coincide with promoter regions upstream of genes.

Let's use an HMM to annotate a given DNA string with CpG islands.

## Method
- Specify a model. Use the one in Fig 3.3 of Biological Sequence Analysis by Durbin et al. 
- Download training data from https://genome.ucsc.edu/cgi-bin/hgIntegrator. Choose a stretch of chr17 avoiding telomeric and centromeric regions. Choose Regulation track group and CpG Islands track to get CpG island annotation.
- Compute parameters of the model based on training data.
- Download a stretch of chr18 to run your HMM against.
- Download gene annotation. 
- Are regions upstream of gene enriched in CpG islands?




