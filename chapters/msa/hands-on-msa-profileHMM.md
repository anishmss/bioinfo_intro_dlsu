# Hands-on: Building a profile HMM of the HIV pol region

## Background
We will build on our previous hands-on activity on identifying HIV drug resistance mutations.

Earlier, we used pairwise alignment to compare short reads from a patient to the HXB-2 reference sequence. 
Mutations identified from the alignments were used to characterize drug resistance. 

As HIV-1 is [highly genetically diverse](https://academic.oup.com/jid/article/228/11/1583/7244781), using a single sequence as reference is perhaps not a good idea. So in this hands-on activity, we will use as reference a profile HMM built using protein sequences from various subtypes, and align the reads to this profile HMM. We will replicating parts of the work done [here](https://academic.oup.com/bioinformatics/article/35/12/2029/5165375#393864650).

For the profileHMM, we will use the gag-pol polypeptide sequences available from UniProt.
ART drugs mainly target proteins encoded by the *pol* region, and the drug resistance databases mainly maintain information about amino acid changes in the proteins encoded in this region. However, in HIV, the proteins in the pol region are not translated separately, as a single, large poly-protein from an unspliced mRNA that contains the gag and pol region. Since the gag and pol regions overlap, and an interesting thing called programmed frameshift is needed to synthesize the gap-pol poly-protein. Watch [this](https://www.youtube.com/watch?v=-sNjOZL_Sbg) for more.

## Tasks
You will be replicating parts of this [paper](https://academic.oup.com/bioinformatics/article/35/12/2029/5165375#393864650)

- From UniProtKB, collect HIV Gag-pol sequences. Accumulate at least 20 sequences representing various subtypes. Prioritize the Reviewed (Swiss-Prot) sequences since these are better curated.
- Build a multiple sequence alignment of the sequences. Some MSA tools: MAFFT, Clustal Omega. Try to understand the options and parameters you set. 
- Build a profile HMM using HMMER. Again, take note of the options and parameters 
- Align the reads from the dataset you used for the last hands-on.
    - To align DNA reads to a protein profile HMM, you will need to compute the translations of the reads in 6 possible frames.
- Compare your results against the results you obtained in the previous hands-on.


## References
- https://academic.oup.com/bioinformatics/article/35/12/2029/5165375#393864650
- https://academic.oup.com/jid/article/228/11/1583/7244781
- [Overview of HIV life cycle](https://www.youtube.com/watch?v=-sNjOZL_Sbg)