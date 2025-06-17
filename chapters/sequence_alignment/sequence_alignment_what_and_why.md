# Sequence alignment: what and why

We decided earlier in this course that we will think of our three favorite biomolecules (DNA, RNA, protein) as strings/sequences, ignoring their secondary and 3D structures.
Naturally we want to be able to compare two (or more) sequences to identify similarities or dissimilarties between them.
For example, this need might arise when:

- Comparing a newly assembled genome to a well-annotated one to borrow annotations
- Comparing human and mouse genomes to figure out how and when we have diverged from our common ancestor
- Comparing normal and cancer genomes to identify mutated, aberrant genes 
- Sequence database search


## Can't we just use spell checkers?
Given large volumes of sequence data, we need an algorithm for comparing sequences. But first, we first need a mathematical definition for (dis)-similarity between two sequences. This might not seem like a problem unique to bioinformatics, since for example the field of natural language processing has many ways to compare sequences like words, sentences, documents, etc. Can't we just use the idea of something like a spell checker on biological sequences? To some extent, maybe, but not really. This is because the differences you might see between, say,  human and mouse genomes came about through  mechanisms very different to how you make spelling errors when you are typing messages on teeny tiny keyboard on a smartphone. 

The go-to method for comparing biological squences is called **sequence alignment**. Before we delve into this important and fundamental topic, let's look at how sequences evolve. 

## How do sequences evolve? 
Suppose you wanted to compare the sequence of a gene that is common in human and mouse. It is estimated that the human and mouse lineages diverged from their common ancestor roughly 80 million years ago. The figure below shows a toy example of portions of human and mouse DNA sequences and how they might have evolved from a hypothetical sequence of their most recent common ancestor. Some of the nucelotides are color coded so that it is easier to track their evolution. 
```{figure} ./images/human-mouse-seq-evolution.svg
---
width: 600px
name: sequence_evolution
---
Toy example of evolution of a DNA segment of human and mouse since their divergence.
```

In this example, the branch leading to Human, there was a **nucleotide substitution** from $\texttt{g}$ to $\texttt{t}$. This means that somewhere along this branch, there was a **mutation** of the ancestral $\texttt{g}$ to $\texttt{t}$ and the mutation spread through that entire ancestral population. You can also see a substitution from a to t in the branch leading to Mouse. 

How often do these substitutions happen and how many substitutions might you expect to see in this human-mouse comparison? Substitution rates vary depending on the region of the genome (coding vs. non-coding) or the kind of substitution(synonymous vs. non-synomymous or trasversion vs. transition)  or the kind of gene (housekeeping genes vs. other genes). For example, the table below shows the substitution rates in a few mammalian genes. Why do you think they vary?

````{card} Substitution rates (per site per billion years) in mammals (Source: Table 4.1 of Graur and Li (2000), *Fundamentals of Molecular Evolution, 2nd edition* )

| Gene            | Non-synomymous | Synonymous        |
| --------------- | ---------------| ----------------- |
| actin $\alpha$  |  0.01 $\pm$ 0.01 | 2.92 $\pm$ 0.34 |
| insulin         |  0.20 $\pm$ 0.01  | 3.03 $\pm$ 1.02 |
| $\gamma$ interferon | 3.06 $\pm$ 0.37 | 5.50  $\pm$ 1.45 |

````


Going back to {numref}`sequence_evolution` we also see that a $\texttt{t}$ got **deleted** in the lineage leading to Mouse. Deletions or insertions are rarer than single-nucleotide substitutions. (See e.g. https://academic.oup.com/mbe/article/26/7/1523/1120476)


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


These mutations can also be classified as small-scale or large-scale depending on how many nucleotides are affected. In this course, we will mainly be concerned with substitutions and small insertions or deletions (jointly called **indels**).

## Mechanisms by which mutations arise
Some mechanisms :
- DNA replication error
- Replication slippage
- Homologous recombination
- Chromosomal breakage and joining
- Improper repair of DNA double-stranded breaks 
- Transposition
- Viral genome insertions, etc.


## Sequence alignment is a hypothesis about how the sequence pair might have evolved
Given two sequences, a **sequence alignment** is a one-to-one correspondence between the residues of common ancestry (aka **homologous** residues). An alignment can be visualized by placing one sequence on top of another such that homologous residues are in the same **column**. A deletion or insertion is mapped to a **gap** character "-". For the example in {numref}`sequence_evolution`, a correct alignment between the pairs can be visualized as shown below.

```{figure} ./images/human-mouse-seq-alignment.svg
---
width: 600px
name: sequence_evolution_alignment
---
A sequence alignment (right) describing the evolution of sequence pair (left).
```

Given two sequences, an alignment between them is a hypothesis about how the sequences have evolved from a common ancestry, or if they have a common ancestry at all. 

Because we don't have the ancestral or the intermediate sequences, 
a sequence alignment cannot fully explain how the sequence pair has evolved.
It is going to miss important details: back substitutions, parallel substitions, coincidental substitutions, etc. These are important especially if we wish to count the actual number of substitutions. This is needed for example to compute evolutionary distance between sequences. There are ways to correct for some of these.

We will next look at how to compute alignments given two sequences. 
