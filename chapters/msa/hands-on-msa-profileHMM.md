# Hands-on: Building a profile HMM of the HIV pol region

## Background
We will build on our previous hands-on activity, in which we used aligned short reads from a patient to the HXB-2 reference sequence to determine the presence of mutations known to be associated with drug resistance. 

As HIV-1 is [highly genetically diverse](https://academic.oup.com/jid/article/228/11/1583/7244781), using a single sequence as reference is perhaps not a good idea. Instead a pHMM containing sequences from various subtypes would be a more suitable reference. 

Specifically we will build a pHMM of **gag-pol** polypeptide sequences.  
This is because ART drugs mainly target proteins encoded by the [*pol* region](https://www.hiv.lanl.gov/content/sequence/HIV/MAP/landmark.html), and the drug resistance databases mainly maintain information about amino acid changes in the proteins encoded in this region.
In HIV, the proteins in the pol region are not translated separately; but instead as a single, large poly-protein from an unspliced mRNA that contains the *gag* and *pol* regions. An interesting side note is that the *gag* and *pol* regions overlap, a **programmed frameshift** is needed during translation to synthesize the gap-pol poly-protein. Watch [this](https://www.youtube.com/watch?v=-sNjOZL_Sbg) for more.

## Objective
Identify and estimate the prevalence of HIV drug resistance mutations in an ART-naive individual by aligning sequence reads of HIV genome obtained from a patient to a reference pHMM built from **gag-pol** polypeptide sequences.


## Tasks
We will be replicating parts of the work done [here](https://academic.oup.com/bioinformatics/article/35/12/2029/5165375#393864650).

- From UniProtKB, collect HIV gag-pol protein sequences. Accumulate at least 20 sequences representing various subtypes. Prioritize the Reviewed (Swiss-Prot) sequences since these are better curated.
- Build a multiple sequence alignment of the sequence using a tool mentioned in the MSA section. 
- Build a pHMM using [HMMER](http://eddylab.org/software/hmmer/Userguide.pdf). Again, take note of the options and parameters 
- Align the reads from the dataset you used for the last hands-on to the pHMM, using HMMER.
    - To align DNA reads to a protein profile HMM, you will need to compute the translations of the reads in 6 possible frames.
- Compare your results against the results you obtained in the previous hands-on.


## References
- https://academic.oup.com/bioinformatics/article/35/12/2029/5165375#393864650
- https://academic.oup.com/jid/article/228/11/1583/7244781
- [Overview of HIV life cycle](https://www.youtube.com/watch?v=-sNjOZL_Sbg)