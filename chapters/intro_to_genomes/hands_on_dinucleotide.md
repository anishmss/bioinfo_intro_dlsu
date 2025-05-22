# Hands-on activity: Di-nucleotide frequency differences in organisms
## Objective

The objective of this assignment is to compare the nucleotide and di-nucleotide frequencies in the human and fruit fly genomes, and to discuss possible biological justifications for the observations. You will be replicating parts of the results in {cite}`Gentles2001-pj,Burge1992-fq`.

Your genome sequence can be represented by a string over the alphabet {a,c,g,t}. Are the frequencies of a,c,g,t uniform? How about di-nucleotides, are their frequencies uniform? 


## Method

Perform the following for human and fruit-fly genome.

Step 1: Let $S$ be a DNA string of length 50 kilo-bases, taken from a random position in the genome. 

Step 2: Observe the frequencies of all possible dinucleotides (see notes below on how to deal with double-strandedness of DNA).

Step 3: Compute the over-representation or under-representation of the dinucleotides by computing the odds ratio of observed and expected frequencies.

Step 4: Repeat 100 times.

Step 5: Visualize and discuss your results. 

## A note on computing (di)nucleotide frequencies

If we were to treat $S$ as a single string (i.e. ignore the double-stranded-ness of RNA), for a dinucleotide $xy$ , its odds ratio (i.e. ratio of observed frequency and expected frequency) would be $ R_{xy} = f_{xy}/f_xf_y$,
where $f_{xy}$ is the observed frequency of $xy$ in $S$ and $f_x$ is the frequency of nucleotide $x$ in $S$. 


However, since $S$ is double stranded, we need to consider its reverse complementary sequence $S_{RC}$. 
Let $S'$ be the sequence obtained by concatenating $S$ and $S_{RC}$. The presence of say a $\tt{ cc}$ in $S$ means there is a $\tt{ gg}$ in $S_{RC}$, and the frequency of $\tt{ cc}$ and $\tt{ cc}$ in $S'$ would be the same. So we could club together  $\tt{ cc}$ and $\tt{ cc}$ into one group. Overall there will be ten groups from the 16 possible dinulceotides.


For a nucleotide $x$, its frequency $f'_{x}$ in  $S'$ is:

$f'_{x} = (1/2) \times (f_{x} + f_{\bar{x}})$, 

where $f_x$ and $f_{\bar{x}}$ are the frequencies $x$ and its reverse complement nucleotide $\bar{x}$ in $S$.


Similarly, the frequency of a di-nucleotide $xy$ in $S'$ is:

$f'_{xy} =(1/2) \times (f_{xy} + f_{\bar{xy}})$, 

where $f_{xy}$ and $f_{\bar{xy}}$ are the frequencies of $xy$ and its reverse complement dinucleotide $\bar{y}\bar{x}$ in $S$.

Therefore the odds ratio that considers both strands is:

$R'_{xy} = \frac{f'_{xy}}{f'_{x}f'_{y}} = 2\times\frac{f_{xy} + f_{\bar{xy}}}  {(f_{x} + f_{\bar{x}}) \times (f_{y} + f_{\bar{y}})}.$


## References
```{bibliography} 
:filter: docname in docnames
```
