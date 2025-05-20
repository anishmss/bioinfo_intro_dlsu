# Living things are made of living cells

## To study life is to study cells
Biology is the study of life. 
There is an amazing diversity of life -- you'd be forgiven for thinking there was nothing common between you and, say, a penguin roaming about somewhere in Antartica, or a bacterium somewhere deep in your gut happily digesting the complex carbohydrate you had for lunch. 
If the nature of every organism was governed by its own set of specific rules, biology would be an impossible science.
```{figure} ./images/diversity_of_life.png
--- 
width: 400px
name: diversity_of_life
---
Life is diverse, but there are common underlying principles.
```

Luckily, it is not as unweildy, thanks to one defining feature of living things: that they are made of cell(s). (Actually, *living* cells, which makes the definition circular, but let's not open that can of worms.) Modern biology thus has become mostly the study of cells: how they function, how they malfunction, what their origin story is, and so on.

The underlying processes that govern the functioning of all cells are largely the same. Indeed, some processes that happen inside your cells also happen in a bacterium. Of course, there are many differences among different kinds of cells, which has allowed for different flavors of biology to flourish.
But let us first focus on the commonalities.

## Molecular components of a cell
If you break open a cell, say a bacterial cell or one in your body, what molecules would you find inside?
{numref}`cell_composition` shows a breakdown. 

What you will find inside will mostly just be water. How boring.
But there are many other interesting kinds of molecules lying or floating around. 

```{figure} ./images/U1CP1-3_CellComposition_v2_ksm.jpg
--- 
width: 400px
name: cell_composition
---
Composition of a typical bacterial cell. Proportions by dry mass.
Source: https://www.nature.com/scitable/topicpage/what-is-a-cell-14023083/
```

Of the major macromolecules, you will find **lipids**,  **polysaccharides**, **DNA**, **RNA**, and **proteins**. You will also find small organic and inorganic molecules.
But let's not go into the biochemistry of all these molecules, and instead delve a bit more on the three molecules that bioinformaticians love: DNA, RNA, and proteins, and see them in the light of bioinformatics.

## Bioinformatic abstractions of DNA, RNA, and proteins

### DNA

**DNA**, as you surely know, as you know carries hereditary information. 
And because it does so imperfectly (more on this when we discuss about sequence evolution), it is also a *document of evolutionary histroy*{cite}`Zuckerkandl1965-kg`. 

DNA is a double-stranded polymer in a double-helix form. A monomeric sub-unit of a strand is called a **nucleotide**, which can be one of four types depending on the nitrogen-containing **base** it carries: adenine, cytosine, guanine, thymine.

```{figure} ./images/0322_DNA_Nucleotides.jpg
--- 
width: 400px
name: DNA_nucleotides
---
Structure and structural units of DNA \
Source: https://commons.wikimedia.org/wiki/File:0322_DNA_Nucleotides.jpg
```

In bioinformatics, we just represent DNA as a string over the alphabet {a,c,g,t}.
This considers just one of the strands, as the other can be determined easily given the complementary a-t and c-g base-pairing. So for example, the following 210 **nucleotide long** sequence (or 210 *basepairs long** if you are thinking of both strands together) is a portion of human DNA somewhere 1/4th along Chromosome 3.  This is near the region that [this naughty scientist](https://www.science.org/content/article/crispr-bombshell-chinese-researcher-claims-have-created-gene-edited-twins) edited in human embryos and got into hot water for doing so.

> $ {\tt agaagagctgagacatccgttcccctacaagaaactctccccgggtggaacaagatggattatcaagtgt}$
> $ {\tt caagtccaatctatgacatcaattattatacatcggagccctgccaaaaaatcaatgtgaagcaaatcgc}$
> $ {\tt agcccgcctcctgcctccgctctactcactggtgttcatctttggttttgtgggcaacatgctggtcatc}$

A string representation is not the most accurate abstaction of DNA as it ignores the fact that DNA is an actual macromolecule with a 3D structure occupying 3D space. There are people who do study this structure, but much of genomics seems to be happy with the string representation, so we will just stick to it as well.

### RNA

**RNA** molecules can have regulatory functions or can be carriers of information sourced in the DNA which is used for protein synthesis. 

RNA is a single-stranded polymer with nucleotides as the units, similar to DNA but with the exception that instead of thymine, it has uracils. So like DNA, we could just represent RNA simply as a string over the alphabet {a, c, g, u}.  

However, it is known that RNA likes to fold onto itself by pairing between bases, to form structures that are necessary for its function. 
For example, {numref}`tRNA_2D_3D` right shows the structure that a transfer-RNA might take up for it to be able to carry out its function.
The so-called **secondary structure** ({numref}`tRNA_2D_3D` left) describes bases-pair interactions, and can be represented, e.g. by a 0-1 triangular matrix. The problem of estimating a secondary structure given a RNA string is an active research topic.

We could go even further and represent the tertiary structure describing the position of each atom in the polymer ({numref}`tRNA_2D_3D` right), but we won't venture into this aspect of structural biology in this course. 

```{figure} ./images/TRNA_structure_2D_3D.jpg
--- 
width: 400px
name: tRNA_2D_3D
---
Secondary structure and tertiary structure of a tRNA \
Source: https://commons.wikimedia.org/wiki/File:OSC_Microbio_10_03_tRNA.jpg
```

### Proteins
Proteins are the so-called *workhorses* of the cell, carrying out many different functions in a cell.

Proteins too are polymers, with amino acids as subunits. There are 20 kinds of amino acids : alanine (A), arginine (R), asparagine (N), aspartic acid (D), cysteine (C), glutamic acid (E), glutamine (Q), glycine (G), histidine (H), isoleucine (I), leucine (L), lysine (K), methionine (M), phenylalanine (F), proline (P), serine (S), threonine (T), tryptophan (W), tyrosine (Y), and valine (V). So a protein can be represented as a string over the alphabet of amino acids. Here's a protein sequence that saved the world. It is part of the spike glyco-protein of SARS-Cov-2, on which the RNA vaccines were designed.

> $ {\tt MFVFLVLLPLVSSQCVNLTTRTQLPPAYTNSFTRGVYYPDKVFRSSVLHSTQDLFLPFFSNVTWFHAIHV}$
> $ {\tt SGTNGTKRFDNPVLPFNDGVYFASTEKSNIIRGWIFGTTLDSKTQSLLIVNNATNVVIKVCEFQFCNDPF}$
> $ {\tt LGVYYHKNNKSWMESEFRVYSSANNCTFEYVSQPFLMDLEGKQGNFKNLREFVFKNIDGYFKIYSKHTPI}$


Like RNA, a protein assembles itself into is important to its ability to carry out its function. [Here](https://3d.nih.gov/entries/10379/2) for example is the structure of the human insulin monomer, the protein hormone that signals cells to increase glucose uptake. 
Protein structural is so important that part of the [2024 Nobel Prize in Chemistry](https://www.nobelprize.org/prizes/chemistry/2024/press-release/) was given to people working on computational prediction of protein structures.
Therefore, we should also consider the structure of proteins, but for this course, we will ignore structural information, and stick to sequence analysis.

## Further reading
- Cell Biology by the Numbers: What is the macromolecular composition of the cell https://book.bionumbers.org/what-is-the-macromolecular-composition-of-the-cell/

- The Molecular Composition of Cells from The Cell: A Molecular Approach. 2nd edition. https://www.ncbi.nlm.nih.gov/books/NBK9879/
## References

```{bibliography} 
:filter: docname in docnames
```
