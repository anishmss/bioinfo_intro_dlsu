# Sequence alignment methods
- Hypothesis
- Small-scale mutations

## Scoring an alignment
Before thinking of how to compute a ''best'' alignments, we need a way to score them.
Shown below are two different alignments of the same pair of sequences. 
Which one is a better alignment? Which one seems to be a better hypothesis of how these sequences have evolved?


The commonly used scoring scheme has two component: a **substiution matrix** to score alignment columns with matches or mismatches, and a **gap penalty** to score the indels. The gap penalty can be **linear** in the sense that a gap of length $l$ is given a score of $gl$.  It is typical to use something called an **affine** gap penalty.  This is based partly on indel size distributions and partly because it is easier to fit it into the dynamic programming alignment algorithms we will look at below.
## Algorithms

### Global alignment 

Needleman-Wunsch algorithm



### Local alignment
Smith-Waterman-Gotoh algorithm


## Next questions

- How to find alignments faster since quadratic time complexity just too slow for the amount of sequence data we generate these days. 
- What is the statistical significance of the best score?
- What is a good scoring scheme?
