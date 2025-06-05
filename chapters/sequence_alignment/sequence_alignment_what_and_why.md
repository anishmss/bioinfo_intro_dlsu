# Sequence alignment: what and why

We decided early on that we will think of our three favorite biomolecules (DNA, RNA, protein) as strings/sequences, ignoring their secondary and 3D structures.
Naturally we want to be able to compare two (or more) sequences to identify similarities or dissimilarties between them.
For example, this need might arise when:

- Comparing a newly assembled genome to a well-annotated one to borrow annotations
- Comparing human and mouse genomes to figure out how and when we have diverged from our common ancestor
- Comparing normal and cancer genomes to identify mutated, aberrant genes 
- Comparing DNA sequences collected from urban wastewater to antimicrobial resistant gene databases to discover the abundance and diversity of such resistant genes


## Can't we just use spell checkers?
Given large volumes of sequence data, we need an algorithm for comparing sequences. But first, we first need a mathematical definition for (dis)-similarity between two sequences. This might not seem like a problem unique to bioinformatics, since for example the field of natural language processing has many ways to compare sequences like words, sentences, documents, etc. Can't we just use the idea of something like a spell checker on biological sequences? To some extent, maybe, but not really. This is because the differences you might see between, say,  human and mouse genomes came about through  mechanisms very different to how you make spelling errors when you are typing messages on teeny tiny keyboard on a smartphone. 

The go-to method for comparing biological squences is called **sequence alignment**. Before we delve into this important and fundamental topic, let's look at how sequences evolve. 

## Sequence evolution and sequence alignment
Suppose you wanted to compare the sequence of a gene that is common in human and mouse. It is estimated that the human and mouse lineages diverged from their common ancestor roughly 80 million year ago. The figure below shows a portion of the DNA sequences in human and mouse and a hypothetical sequence of the common ancestor. Some of the nucelotides are color coded so that it is easier to track their evolution. 
```{figure} ./images/human-mouse-seq-evolution.svg
---
width: 600px
name: sequence_evolution
---
Toy example of evolution of a DNA segment of human and mouse since their divergence.
```

In the branch leading to Human, there was a **nucleotide substitution** from g to t. This means that somewhere along this branch, the g mutated to a t and the mutation spread through and became **fixed** in that ancestral population, and all the descendants going forward. You can also see a substitution from a to t in the branch leading to Mouse. As a side note, how many substitutions might you expect to see? How often do these substitutions happen?

We also see that a t gets deleted in the mouse lineage. Deletions or insertions are rarer than nucleotide substitutions. 


## Types  of mutations
We can classify mutations into small-scale ones that affect up to several nucleotides or large-scale ones that involve re-arrangements of larger segments of DNA.

Here are some small-scale mutations. 
- Substitution
- Deletion
- Insertion
- Inversion
- Recombination

## Molecular mechanisms of mutations
- DNA replication error
- Replication slippage
- Homologous recombination
- Chromosome breakage and joining
- Transposition

In this course, we will only focus on small-scale mutations. 

## Sequence alignment
Given two DNA sequences, a **sequence alignment** is a one-to-one correspondence between homologous nucleotides, i.e. nucleotides of common ancestry.  We can also define sequence alignment in a similar way for RNA or protein sequences.  An alignment can be visualized by placing one sequence on top of another such that the corresponding nucleotides are in the same **column**. A deletion or insertion is mapped to a **gap** character "-". For the example in {numref}`sequence_evolution`, its correct alignment can be visualized as shown below.

```{figure} ./images/human-mouse-seq-alignment.svg
---
width: 600px
name: sequence_evolution_alignment
---
A sequence alignment is a hypothesis about how the sequences have evolved.
```

### What can you do with sequence alignment
A sequence alignment is a hypothesis about how the two sequences have evolved. It can answer questions like:
- Are the two sequences homologous?
- What parts are homologous ?
- How have the sequences evolved?

### What is missed?
A caveat is that because we don't have the ancestral or intermediate sequences it is going to miss a few important details: back substitutions, parallel substitions, coincidental substitutions, etc. These are important especially if we wish to count the actual number of substitutions. This is needed for example to compute evolutionary distance between sequences. There are ways to correct fors some of these, but for now we will just gloss over this inadequacy.

We will next look at how to compute alignments. 


