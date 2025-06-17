# Hands-on: Global alignment and hierarchical clustering of ACE2 orthologs  

## Background
Remember few years ago when you got COVID-19 ?  And maybe your pets too?

ACE2 is a protein found in the surface of various kinds of human cells, including e.g. at the surface of lung and airway epithelial cells, leading to COVID-19 often manifesting as a respiratory illness. ACE2 serves as a receptor for SARS-Cov-2 and other related coronaviruses like MERS-Cov and SARS-Cov-1. The first step in the infection process involves a spike glycoprotein present on the viral envelope of a coronavirus binding with an ACE2 receptor on the host cell surface. See [here](https://commons.wikimedia.org/wiki/File:Microorganisms-08-01259-g001.webp) for a cartoon depiction. 

What got some many people worried in 2020 was that if dogs and cats could get COVID, what other animals that live in human proximity could get infected by or facilitate the transmission of SARS-Cov-2?
One clue is to study the ACE2 [orthologs](https://www.nlm.nih.gov/ncbi/workshops/2023-08_BLAST_evol/ortho_para.html) in those animals.
[This paper](https://www.pnas.org/doi/10.1073/pnas.2025373118) and [this one](https://journals.asm.org/doi/10.1128/jvi.01283-20) did just that and more. Let's do our own simple sequence analysis of the ACE2 ortholog sequences. 

## Objectives
To compare ACE2 orthologs by performing pairwise sequence alignments and computing a distance-based hierarchical clustering.

## Tasks

Perform the following tasks and discuss the results you obtain. 
You are free to choose your own parameters for the tools (e.g. pairwise aligner) that you use, but include in the discussion what choices you made and why.

- Download the ACE2 ortholog sequences of at least 10 vertebrates using the NCBI accessions provided in the papers above.
- Using an implementation of the Needleman Wunsch algorithm, compute pairwise global alignment of each of those sequences against the human ACE2. (What scoring scheme will you choose?)
- One of the papers above mentions that the amino acids in certain positions might be important in deducing host susceptibility. What do you observe?
- From each pairwise alignment, ignoring the gap columns, compute the **p-distance** (See e.g. Section 4.3 of https://www.megasoftware.net/mega1_manual/Distance.html).
- For each pairwise alignment, compute  also the Poisson corrected distance. (Why is the correction necessary?)
- Compute a hierarchical clustering/dendrogram of the sequences based on the pairwise distances. A popular choice is [the UPGMA method](https://en.wikipedia.org/wiki/UPGMA).


## Resources
- Biopython and scikit-bio have implementation of global alignment algorithms
- Biopython also has implementation of UPGMA. Multiple sequence aligners (more on this topic in the next module) like [MAFFT](https://mafft.cbrc.jp/alignment/server/index.html)) and [MEGA](https://www.megasoftware.net/) also provide implementation of UPGMA since it is often needed or multiple sequence alignment.