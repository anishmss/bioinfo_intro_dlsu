# Hands-on Activity: Identifying CpG islands in long stretch of DNA 
Adapted from the CpG island detection example in Chapter 3 of Durbin et al. Biological Sequence Analysis.

## Objectives
- Implement an HMM to identify CpG islands in a stretch of human genome sequence
- Compare the obtained CpG islands against other functional annotations


## Background
In the previous hands-on activity, we found that the CpG dinucleotides (we write ''CpG'' to emphasize that the C and G are on the same strand connected at the **p**hospate backbone) are rare in the human genome. How about their positional distribution? Are CpGs uniformly rare throughout the genome? 

One theory for why CpG is rare is that cytosines in CpG sites are easily methylated (a methyl group attaches at one of the carbons) and methylated cytosines turn into thymines at a high rate, thus resulting in a global CpG-rareness. However, there are regions of that lack methylated CpGs and are not CpG deficient. These regions are called **CpG islands**, and they typically coincide with gene promoters. See figure below.
```{figure} ./images/Cpg_island_evolution.svg.png
---
width: 600px
name: cpg_island
---
CpG island\
Source: https://en.wikipedia.org/wiki/CpG_site
```

Let's use an HMM to annotate a given DNA string with CpG islands and check if gene promoter regions are enriched in CpG islands.

## Steps
- Specify the states of the HMM model. Use the one in Fig 3.3 of Biological Sequence Analysis by Durbin et al. 
- Download training data from https://genome.ucsc.edu/cgi-bin/hgIntegrator. Choose stretches of Chr18 avoiding telomeric and centromeric regions. Choose Regulation track group and CpG Islands track to get CpG island annotation. 
- Esimate the state transition probabilies of the model based on training data. Emission probabilities are all trivially set.
- For testing, download stretches of Chr19 and the corresponding gene annotation.  
- Run your HMM against the test sequences. Compute Viterbi decoding as well as posterior decoding.  
- Are regions ~500bp upstream of genes enriched in CpG islands? Compute statistical significance using https://bedtools.readthedocs.io/en/latest/content/tools/fisher.html or  https://doi.org/10.1093/bioinformatics/btac255. 


## References
-  https://doi.org/10.1016/j.febslet.2009.04.012








