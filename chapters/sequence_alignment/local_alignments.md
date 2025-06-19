# Local alignment

## Use cases:
 - Searching a protein database with a query sequence
 - Comparing human and mouse genomes to find regions of local similarity, etc.

## Scoring a local alignment
We will use the same scoring scheme as we did with global alignemnt, except that we would want only parts of the sequences that are homologous to contribute to the score (e.g. the green segments below). 
```{figure} ./images/local_alignment.svg
---
width: 400px
name: local_alignment
---
Local alignment scoring
```

## Smith-Waterman algorithm for local alignment
Like the global alignment problem, the problem of finding a highest-scoring local alignment can also be solved by dynamic programming.

### Optimal substructure property
Again, let $A$ and $B$ be the two input sequences; let $A[i]$ be the $i$-th residue of sequence $A$ and $A[i:j]$ be the substring $A[i], A[i+1],\ldots, A[j]$. Again, for simplicity, let's assume linear gap penalty for now.

We have to be a bit more clever with defining subproblems here, since an optimal local alignment between $A[1:i]$ and $B[1:j]$ isn't necessarily obtained by adding columns to the right end of an optimal local alignments of prefixes of $A[1:i]$ and $B[1:j]$.

Instead, define $S_{ij}$ to be the highest score among global alignments of suffixes of $A[1:i]$ and $B[1:j]$. That is, let $SA_i$ and $SB_i$  be the set of all suffixes (include the empty string) of $A[1:i]$ and  $B[1:j]$, respectively. Then 

````{card}
:width: 75%
```{math}
S_{ij} = \max_{\substack{X \in SA_i \\ Y \in SA_i}} \left( \text{score of global alignment between $X$ and $Y$} \right)
```
````

Given this definition of $S_{ij}$, the following recurrence relation can be derived:

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

### Backtracking

### Demo

[Here](https://rna.informatik.uni-freiburg.de/Teaching/index.jsp?toolName=Smith-Waterman) is an online demonstration.

### Time complexity
Let $m,n$ be the lengths of sequences $A,B$, respectively.
There are $\Theta(mn)$ cells to compute and each cell takes $\Theta(1)$ time to compute. 
So the running time is $\Theta(mn)$
Even though the search space is much larger than global alignment, interestingly the running time is the same.

### Affine gap penalty



## Heuristics for faster local alignments

### Seed and extend
 

### How to find seeds quickly?

## Statistical significance 