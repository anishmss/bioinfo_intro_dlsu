# Exploring our own genomes

We will now turn our attention to **genomes**, which just means *all DNA in a cell*.
Given that genomes are "blueprints", there are going to be differences among species and even among individuals of the same species. We can't possibly go through all genomes, so to start out with, let's just look at arguably the most interesting genome: our own. 

In a human cell, DNA is packaged tightly into chromosomes which are found inside a nucleus. 
There is also some small amount of DNA in the mitochondria (yes, the powerhouse of the cell :D), but let us ignore the mitochondrial genome for now. Ignoring also the 3D structure of the chromosome, we can think of each chromosome as a string over the alphabet {a,c,g,t}.  

There are many questions we can ask about this sequence:

- How are genes and other elements organized along the genome?
- Is there any pattern in the sequence composition ?
- How does the genome differ among different populations ?
- How does our genome compare to that of say a chimpanzee or a mouse?

Some of these questions, we will investigate in this module; some in later modules.

## The not so reference-y reference human genome
There is actually one publicly available human genome sequence called the GRCh38 assembly. It is also called *the reference* human genome sequence, since it is widely used by researchers as a basis for comparing sequences produced by their studies. However many people are complanining about the reference-y-ness of that sequence since it was obtained from the genomes of multiple individuals, mostly from North America, which is not really representative of the global human population. For us though, it will serve as a wonderful dataset to explore; and if you are a normal human being, your genome is going to be very, very, very close to this sequence anyway.

## The neighborhood of BRCA1 
The GRCh38 assembly contains sequence from all chromosomes, which if you concatenate would result in a string ~3 Gbases long. That's a loooong sequence of just a,c,g,ts, and nothing will come out of just eyeballing it.
Let's instead zoom in to one region in this sequence.
The snapshot below taken using the Ensembl Genome Browser is of the neighborhood of chromosome 17 position 43.10 Mb.
The image is quite detailed, so you might want to open it up on a separate browser window.
Let's go through some of the elements we find in this region.

```{figure} ./images/Human_1742926099_43247380.png
---
width: 800px
name: BRCA1_neighborhood
---
Ensembl Genome Browser snapshot of the region around Chromosome 17 position 43.10 Mb of the Human GRCh38 assembly \
```

### Protein-coding genes
Inside the blue (red) box are genes in the forward (reverse) strand.
Perhaps, the most notable of the genes is BRCA1.
BRCA1 is a DNA damage repair gene, whose mutant allele is associated with an increased risk of breast cancer. Hence the name, and hence the [Angelina Jolie connection](https://time.com/3450368/the-angelina-effect/). 

There are ~20,000 protein-coding genes in the human genome.


### Variant transcripts
Splice variants of each gene is also shown. For example, 6 variants of  BRCA1 transcripts are shown, although many more are known. You can see that each transcript has short exons (shown as boxes or almost vertical lines when the width is small) and long introns (shown as horizotal lines with a slight dip connecting two exons). This is generally true for any gene, and  to the point where the exons of protein-coding genes only account for ~1% of our entire genome.

### Non-coding genes
Apart from the protein-coding genes, we can also see inside the blue and red boxes, non-coding RNA genes of several types: lncRNA, snoRNA, snRNA. 

### Regulatory elements
The green boxes contain information about regulatory elements.

### Pseudogenes
Also in the blue and red boxes are the so called **psuedogenes**, which are defective copies of genes. See here for more details on these interesting elements. 

### Transposable elements
The pink box shows transposable elements, which are/were mobile DNA sequences capable of moving about or replicating within the human genome.

