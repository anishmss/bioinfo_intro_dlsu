# Sequence alignment: what and why

We decided earlier in this course that we will think of our three favorite biomolecules (DNA, RNA, protein) as strings/sequences, ignoring their secondary and 3D structures.
Naturally we want to be able to **compare** two (or more) sequences to identify similarities or dissimilarties between them.
For example, this need might arise when:

- Comparing a newly assembled genome to a well-annotated one to borrow annotations
- Comparing human and mouse genomes to figure out how and when we have diverged from our common ancestor
- Comparing normal and cancer genomes to identify mutated, aberrant genes 
- Sequence database search


## Can't we just use spell checkers?
Comparing sequence is not a problem unique to bioinformatics. For example the field of natural language processing has many ways to compare sequences like words, sentences, or documents. Can't we just use something like a **spell-checker** on biological sequences? To some extent, maybe, but not really. This is because the differences you might see between, say, human and mouse genomes came about through  mechanisms very different to how you make spelling errors when you are typing messages on teeny tiny keyboard on a smartphone. 

## How do sequences evolve? 
Imagine comparing the sequences of a gene that is found in human and mouse. It is estimated that the human and mouse lineages diverged from their common ancestor roughly 80 million years ago. The figure below shows a toy example of portions of human and mouse DNA sequences and how they might have evolved from a hypothetical sequence of their most recent common ancestor. Some of the nucelotides are color coded so that it is easier to track their evolution. 
```{figure} ./images/human-mouse-seq-evolution.svg
---
width: 600px
name: sequence_evolution
---
Toy example of evolution of a DNA segment of human and mouse since their divergence.
```

In this example, the branch leading to human, there was a **nucleotide substitution** from $\texttt{g}$ to $\texttt{t}$. This means that somewhere along this branch, there was a **mutation** of the ancestral $\texttt{g}$ to $\texttt{t}$ and the mutation spread through that entire ancestral population. You can also see a substitution from a to t in the branch leading to mouse. 

How often do these substitutions happen, and how many substitutions might you expect to see in this human-mouse comparison? Substitution rates vary depending on the region of the genome (coding vs. non-coding) or the kind of substitution(synonymous vs. non-synomymous or trasversion vs. transition)  or the kind of gene (housekeeping genes vs. other genes). For example, the table below shows the substitution rates in a few mammalian genes. Why do you think they vary?

````{card} Substitution rates (per site per billion years) in mammals (Source: Table 4.1 of Graur and Li (2000), *Fundamentals of Molecular Evolution, 2nd edition* )

| Gene            | Non-synonymous | Synonymous        |
| --------------- | ---------------| ----------------- |
| actin $\alpha$  |  0.01 $\pm$ 0.01 | 2.92 $\pm$ 0.34 |
| insulin         |  0.20 $\pm$ 0.01  | 3.03 $\pm$ 1.02 |
| $\gamma$ interferon | 3.06 $\pm$ 0.37 | 5.50  $\pm$ 1.45 |

````


Going back to {numref}`sequence_evolution` we also see that a $\texttt{t}$ got **deleted** in the lineage leading to Mouse. Deletions or insertions are much rarer than single-nucleotide substitutions. (See e.g. https://academic.oup.com/mbe/article/26/7/1523/1120476)


## Types  of mutations
In the example above, we saw two kinds of mutations. What other kinds are there?
Figure below shows different types of mutations.

```{figure} ./images/mutation_types.svg
---
width: 600px
name: mutation_types
---
Toy example of evolution of a DNA segment of human and mouse since their divergence.
```


## Mechanisms by which mutations arise
Some mechanisms :
- [DNA replication error](https://www.youtube.com/watch?v=3Izi_7ewKOo)
- Replication slippage
- [Homologous recombination](https://www.youtube.com/watch?v=Xe-83tBcxhs)
- Chromosomal breakage and joining
- Improper repair of DNA double-stranded breaks 
- [DNA transposition](https://www.youtube.com/watch?v=XYZHMGUGq6o)
- [Viral genome insertions](https://www.youtube.com/watch?v=pF3L4hISZnw), etc.


## Sequence alignment 
The go-to method for comparing biological squences is called **sequence alignment**.
Given two sequences, a **sequence alignment** is a one-to-one correspondence between the residues of common ancestry (a.k.a. **homologous** residues). 

An alignment can be visualized by placing one sequence on top of another such that homologous residues are in the same **column**. A deletion or insertion is shown by mapping to the **gap** character "-". For the example in {numref}`sequence_evolution`, a correct alignment between the pairs is as shown below.

```{figure} ./images/human-mouse-seq-alignment.svg
---
width: 600px
name: sequence_evolution_alignment
---
A sequence alignment (right) describing the evolution of sequence pair (left).
```

We will only be concerned with substitutions and small indels. This means that alignment columns are **non-crossing**. This makes the problem  of finding alignments computationally tractable as we will see later when we discuss algorithms to find algorithms.

As you might have noticed, a sequence alignment, even a correct one, cannot fully explain how the sequence pair has evolved.
It is going to miss important details: back substitutions, parallel substitions, coincidental substitutions, etc. These are important especially if we wish to count the actual number of substitutions. This is needed for example to compute evolutionary distance between sequences. There are ways to correct for some of these.



## What can a sequence alignment tell us

Given two homologous sequences, an alignment between them provides a hypothesis about **how** the sequences have evolved from a common ancestry.

Given two sequences, a sequence alignment can also be used to test the hypothesis of  **whether** they are homologous or not, in the first place.

Finally, given two sequences with homology only between parts of the sequences (and not across the entire sequences), an alignment can show us **which parts** are homologous. This case where only parts of the sequences are aligned is called **local alignment**, as opposed to **global alignment**  in which every residue in the sequences is accounted for in the alignment.

In the following, we will treat global and local alignments separately, and look at how to compute them and the algorithmic and statistical aspects of sequence alignment.
