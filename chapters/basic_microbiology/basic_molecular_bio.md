# Living things are made of living cells

## To study life is to study cells
Biology is the study of life. 
There is an amazing diversity of life -- you'd be forgiven for thinking there was nothing common between you and, say, a penguin roaming about in the south pole, or a bacterium somewhere deep in your gut happily digesting the complex carbohydrate you had for lunch. 
If the nature of every organism was governed by its own set of specific rules, biology would be an impossible science.

Luckily, it is not as unweildly, thanks to one necessary condition that defines living things: that they are made of cell(s). (Actually it should read *living* cells, which makes the definition cylical, but let's not open that can of worms.)

Biology is therefore mostly the study of cells: how they function, how they dysfunction, what is their origin story, and so on.

Luckily for us, the underlying processes that govern the functioning of all cells are largely the same. Indeed, some processes that happen inside your cells also happen in a bacterium. Of course, there are many differences among different kinds of cells, which has allowed for different flavors of biology to flourish.
But let us first focus on the commonalities.

## Molecular components of a cell
If you break open a cell -- a bacterial cell or one in your body -- what molecules would you find inside?
It will mostly just be water. How boring.
There are many other interesting kinds of molecules floating around.
You will find lipids, which are biomolecules needed for, e.g. forming membranes, for energy storage, and signalling. 
There will also be carbohydrates that are fuel sources.
Then there will be DNA, which, as you might know carries hereditary information. 
Further, there will be different kinds of RNA molecules that are known to work as messengers of information sourced in the DNA and also have other regulatory functions. 
And then there will be tons of different kinds of proteins, which are the workhorses of the cell.
There will also be lots of other inorganic molecules, but let's stop here with the chemical composition of the cell before this starts to feel like a biochemistry course. 

Instead let's go back to the three molecules that bioinformaticians love: DNA, RNA, and proteins, and see them in the light of bioinformatics.

## Bioinformatic abstractions of DNA, RNA, and proteins

### DNA
You surely know from your high-school biology class that DNA is a double-stranded polymer in a double-helix form. A monomeric sub-unit of DNA is called a nucleotide, which can be one of four types depending on the nitrogen-containing base it carries: adenine, cytosine, guanine, thymine.

In bioinformatics, we just represent DNA as a string over the alphabet {a,c,g,t}.
This considers just one of the strands, as the other can be determined easily given the complementary base-pairing of a-t and c-g. So for example, the followig is a portion of your DNA 

A string representation is not a very accurate abstaction of DNA as it ignores the fact that DNA is a macromolecule with a 3D structure occupying 3D space. There are people who study this 3D structure, but much of genomics seems to be happy with the string abstraction, so we will just stick to it for this course.

### RNA
RNA is a single-stranded polymer with nucleotides as the units, similar to DNA but with the exception that instead of thymine, it has uracils. So we can represent RNA simply as a string over the alphabet {a, c, g, u}.  

However, we go further than just a string representation.
RNA likes to fold onto itself by pairing between bases, to form structures that are necessary for its function. 
The so-called secondary structure describes the base-pair interactions, and can be represented by a 0-1 triangular matrix. 

We could go further and represent the tertiary structure describing the position of each atom in the polymer, but we won't venture into structural biology in this course. 

### Proteins
Proteins too are polymers, with amino acids as subunits. There are 20 kinds of amino acids : alanine (A), arginine (R), asparagine (N), aspartic acid (D), cysteine (C), glutamic acid (E), glutamine (Q), glycine (G), histidine (H), isoleucine (I), leucine (L), lysine (K), methionine (M), phenylalanine (F), proline (P), serine (S), threonine (T), tryptophan (W), tyrosine (Y), and valine (V). So a protein can be represented as a string over the alphabet of amino acids. 

Like with RNA, we could also consider the structure of proteins, but for this course, we will ignore structural information.

## References

- Cell biology by the numbers https://book.bionumbers.org/
{cite}`perez2011python`
```{bibliography} 
:filter: docname in docnames
```
