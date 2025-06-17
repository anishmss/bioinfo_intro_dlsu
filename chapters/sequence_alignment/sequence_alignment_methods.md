# Sequence alignment methods
We can formulate the problem  of aligning two sequences as a discrete optimization problem, in which we define a way to score an alignment and the goal would be to find a highest scoring one. 

## Scoring an alignment
Shown below are two different alignments of the same pair of sequences. 
Which one is a better alignment, i.e. which one seems to be a better hypothesis of how these sequences have evolved?

```{figure} ./images/two_alignments.svg
---
width: 600px
name: two_alignments
---
Two alignments of the same sequence pair. Which one should score higher?
```

The commonly used scoring scheme has two components: (1) a **substiution matrix** $M = [m_{xy}]$, where $m_{xy}$ is the score for an alignment column containing residues $x$ and $y$ in the first and second sequence, respectively, and (2) a **gap penalty** to score the indels. A simple choice of gap penalty is a **linear** one in which a length-$l$ gap is given a penatly of $gl$ for some positive number $g$.  It is however typical to use something called an **affine** gap penalty in which a length-$l$ gap gets a penalty of $o + e (l-1)$, where $o,e$ are gap open and gap extension penalties.  This is based partly on the observation of  indel size distributions and partly because it is easier to fit it into the dynamic programming alignment algorithms.

In many cases, we know that the homology is contained only locally and not along the entire sequences. In such cases, we would want only parts of the sequences that are homologous to contribute to the score (e.g. the green segments below). 
```{figure} ./images/local_alignment.svg
---
width: 600px
name: local_alignment
---
Local alignment
```

Such cases where we are only interested in aligning substring of the two given sequences is called  **local alignment** (as opposed to **global** alignment where every residue contributes to the score).

## Algorithms
The number of possible global alignments between two sequences is very large, so brute-force search is not feasible. Luckily, both the global and local alignment problems under the scoring scheme described above yield nicely to dynamic programming. 

### Needleman-Wunsch algorithm for global alignment
Let $A$ and $B$ be the two input sequences. For a sequence $A$, $A[i]$ is its $i$-th residue and $A[i:j]$ is th e substring $A[i], A[i+1],\ldots, A[j]$. For simplicity, let's assume linear gap penalty for now.

Let $S_{ij}$ be the score of an optimal global alignment between the prefixes $A[1:i]$ and $B[1:j]$. The rightmost column of such an alignment can be only one of three cases: it aligns $A[i]$ with $B[1:j]$, $A[i]$ is aligned to a gap character, or $B[j]$ is aligned to a gap character. Since $S_{ij}$ has the optimal sub-structure property, we can obtain the following recurrence:
````{card}
:width: 75%
```{math}
\begin{align}
    S_{ij} &= \max \begin{cases}
            S_{i-1,j-1} + m_{A[i],B[j]}\\
            S_{i-1,j} + g\\
            S_{i,j-1} + g
           \end{cases} \\[2em]
    S_{0,j} &= gj \text{ for } 0 \leq j \leq n \\
    S_{i,0} &= gi \text{ for } 0 \leq i \leq m 
\end{align}
```
````
This just gives the optimal score; to obtain the actual optimal alignment, we need to do backtracking.

### Smith-Waterman algorithm for local alignment
We have to be a bit more clever here since an optimal local alignment between $A[1:i]$ and $B[1:j]$ isn't necessarily obtained by adding columns to the right end of an optimal local alignments of prefixes of $A[1:i]$ and $B[1:j]$.

Instead, define $S_{ij}$ to be the highest score among global alignments of suffixes of $A[1:i]$ and $B[1:j]$. That is, let $SA_i$ and $SB_i$  be the set of all suffixes (include the empty string) of $A[1:i]$ and  $B[1:j]$, respectively. Then 

````{card}
:width: 75%
```{math}
S_{ij} = \max_{\substack{X \in SA_i \\ Y \in SA_i}} \left( \text{score of global alignment between $X$ and $Y$} \right)
```
````

````{card}
:width: 75%
```{math}
\begin{align}
    S_{ij} &= \max \begin{cases}
            S_{i-1,j-1} + m_{A[i],B[j]}\\
            S_{i-1,j} + g\\
            S_{i,j-1} + g \\
            0 \\
           \end{cases} \\[2em]
    S_{0,j} &= 0 \text{ for } 0 \leq j \leq n \\
    S_{i,0} &= 0 \text{ for } 0 \leq i \leq m 
\end{align}
```
````
The optimal local alignment score is then the maximum of $S_{ij}$ over all possible $i,j$ pairs.

## Next questions

- How to find alignments faster since quadratic time complexity just too slow for the amount of sequence data we generate these days. 
- What is the statistical significance of the best score?
- What is a good scoring scheme?
