# Multiple sequence alignment

## Sequences come in families
Sequences come in families. They might be based on common recent ancestry, structural similarity, or functional similarity. 
For example, in the previous hands-on, we looked at a family of ACE2 sequences. 
Other examples are: protein domains, family of HIV *pol* poly-protein sequences from different HIV subtypes, families of different types of mobile genetic elements, family of trans-membrane proteins found on bacterial cell surfaces that have a [beta barrel](https://en.wikipedia.org/wiki/Beta_barrel) structure. 

## Aligning multiple sequences
Multiple sequence alignment (MSA) extends the idea of pairwise sequence alignment to more than 2 sequences. Like the pairwise case, an msa arranges sequences into columns of homologous residues.

The figure below shown a portion of an MSA of ACE2 orthologs. You can see that one MSA of $n$ sequences provides a lot of information that would be hard to extract from pairwise alignments of all the $n(n-1)/2$ pairs.


```{figure} ./images/ace2_msa_1-51.svg
---
name: ace2_msa_all
---
The first 51 columns of a multiple sequence alignment of ACE2 orthologs, computed by MUSCLE, visualized by Jalview using the [Clustal color scheme](https://www.jalview.org/help/html/colourSchemes/clustal.html).
```


## Computing an MSA
MSA computation can be modeled as a discrete optimization problem.
This requires first defining a scoring scheme. One way to score an MSA is to simply take the sum of the scores of $n(n-1)/2$ pairwise alignments that can be obtained from the MSA. Unfortunately, under this scheme, finding an optimal MSA is NP-hard. This opens the problem to popular search meta-heuristics like simulated annealing and genetic algorithm. However, this approach is slow and also not amenable to probabilistic or statistical interpretations. Most modern MSA tools rely on a different kind of heuristics called **progressive alignment*.


## Progressive alignment 
### Overview
As the name suggests, this technique grows an MSA by progressively adding more sequences to it.
It can be summarized as below:
````{card} Progressive alignment 

Step 1: Compute pairwise distances between each pair of sequences.\
Step 2: Build a bifurcating **guide tree** which has the input sequences as its leaves.\
Step 3: For each internal node, merge the alignments at its two children.\
Step 4: Return the alignment at the root
````
Let's fill in the details below.

### Guide tree

- UPGMA
- Simple chaining

### Merging two alignments

### Iterative refinement


## Further reading

Do and Katoh: Protein Multiple Sequence Alignment 10.1007/978-1-59745-398-1_25