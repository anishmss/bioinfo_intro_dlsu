# Comparing ACE2 orthologs

Remember few years ago when you got COVID-19 ?  And interestingly your dog too?

ACE2 is a protein found in the surface of various kinds of human cells, including (perhaps most importantly) at the surface of lung epithelial cells. ACE2 serves as a receptor for SARS-Cov-2 and other related coronaviruses like MERS-Cov and SARS-Cov-1. The first step in the infection process is that spike glycoprotein present on the viral envelope of a coronavirus binds with ACE2 receptors on the host cell surface. See [here](https://commons.wikimedia.org/wiki/File:Microorganisms-08-01259-g001.webp) for a cartoon depiction. 

What got some people worried in 2020 was that if dogs and cats could get COVID, what other animals that live in human proximity could get infected by or facilitate the transmission of SARS-Cov-2?

One clue is to compare the human ACE2 sequence to its orthologs in other vertebrates.
[This paper](https://www.pnas.org/doi/10.1073/pnas.2025373118) did just that (and a bit more). 
Let's replicate parts of it. 

## Steps
- Download the ACE2 ortholog sequences of at least 10 animals using the NCBI accessions provided in the paper above.
- Using an implementation of the Needleman Wunsch algorithm, compute pairwise global alignment of each of those sequences against the human ACE2. 
    - No need to compute multiple sequence alignment since this is something we will look at later in the course
    - What scoring scheme will you choose?
- The paper mentions that the amino acids in positions 31, 35, 38, 82, and 353 are important in deducing host susceptibility. What do you observe?
- From each pairwise alignment, ignoring the gap columns, compute the **p-distance** (See e.g. Section 4.3 of https://www.megasoftware.net/mega1_manual/Distance.html).
- For each pairwise alignment, compute  also the Poisson corrected distance. (Why is the correction necessary?)
- Discuss your findings.


## References and resources
- https://www.pnas.org/doi/10.1073/pnas.2025373118
