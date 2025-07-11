# Modeling a family of sequences by a profile hidden Markov model
There are cases when we need to decide if a query sequence is a member of a certain family or not. 
Example: viral metagenomics, promoter sequence annotation, mobile genetic element identification, etc.


One approach to membership problem could be to find pairwise alignments of the query to each member of the family. 
There are drawbacks to this approach.
There is going to be many pairwise alignments to deal with, one to each member of the family, and so we need a way to incorporate these results, which is not straightforward. 
Pairwise alignments cannot incorporate information about conserved sites in the family.  
Pairwise alignments are not sensitive in identifying remote homologs.
Also, alignments are more accurate when taking into consideration the family.

## Profile HMM
A profile hidden Markov model (pHMM) is special kind of HMM that models a family of sequences. 
It capture position specific information that you might otherwise see in an MSA. 
Here is a toy example:
```{figure} ./images/phmm_embl_ebi.png
---
width: 400px
name: phmm_embl_ebi
---
A toy example of a profile HMM showing its correspondence to an MSA.\
Source: https://www.ebi.ac.uk/training/online/courses/pfam-creating-protein-families/what-are-profile-hidden-markov-models-hmms/
```

As you can see, a pHMM has a left-to-right structure with no cycles, and has repetitions of triplets of match states ($M$), insertion states ($I$), and deletion states ($D$).
The $M$ and $I$ states emit amino acid $a$ (or nucleotides for DNA profile HMM) with some emission probabilities. 
The $D$ states are silent.



## Building a pHMM from a multiple sequence alignment
It is typical to build a pHMM from a given MSA (although in theory we could build one without MSA and instead use a pHMM to compute an MSA).

A simple approach is to estimate the pHMM parameters is to represent by match states the columns of the MSA that have more residues than gap characters, 
and by insertion states columns that have more gaps than residues. This decides the number of triplet (M,I,D) blocks there will be in the pHMM thus deciding the model architecture.
The transition probabilities can then be estimated by counting the number of each transition made by the sequences in the MSA when their paths are traced on the pHMM
The emission probabilities of the match and insert states can be similarly estimated from the sequences in the MSA.


Here's an actual example from PFAM.
```{figure} ./images/pF00049_insulin_family_msa.png
---
width: 600px
name: pF00049_insulin_family
---
An MSA of Insulin/IGF/Relaxin family from PFAM/InterPro.\
Source: https://www.ebi.ac.uk/interpro/entry/pfam/PF00049/entry_alignments/?type=seed
```

And profile HMM "logo" representation.

```{figure} ./images/pF00049_insulin_family_profile.png
---
width: 600px
name: pF00049_insulin_family_profile
---
A *profile* of Insulin/IGF/Relaxin family from PFAM/InterPro.\
Source: https://www.ebi.ac.uk/interpro/entry/pfam/PF00049/entry_alignments/?type=seed
```

## Aligning a query to a pHMM

Given a fully specified pHMM and a query sequence $x$, we can compute the Viterbi probability path or a full probability. 
This probability can be used to determine the membership of $x$ to the family. 

## Some pHMM databases
- PFAM
- vFAM
- DFAM

## References
- Byung-Jun Yoon: Hidden Markov Models and their Applications in Biological Sequence Analysis, Current Genomics 2009, 10 402-415.

- https://www.ebi.ac.uk/training/online/courses/pfam-creating-protein-families/

- https://ics.uci.edu/~xhx/courses/references/krogh_anintroduction.pdf