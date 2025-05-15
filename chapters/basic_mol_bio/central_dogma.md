# A cell is an information system 
A cell can be thought of as an information system with DNA, RNA, and proteins as the key players. 
There are some differences in how this works in prokaryotic vs. eukaryotic cells. 
Let's take the simpler case first.

## DNA is transcribed into RNA
There are segments of DNA called **genes**, whose sequence information is used to synthesize RNA molecules. (As a side note, biology uses the word gene to mean so many different things. See {cite}`Gerstein2007-si` for the evolution of this term.)
The biological process by which this happens is called **transcription**. 
A key molecule in this process is **RNA polymerase**. 
Here is a microscope image of a DNA being transcribed. Notice how many RNA molecules are being synthesized from a single DNA molecule.
```{figure} ./images/Transcription_label_en_(cropped).jpg
--- 
width: 600px
name: transcription_microscope
---
Microscope image of transcription in action \
Source: https://commons.wikimedia.org/wiki/File:Transcription_label_en_%28cropped%29.jpg
```

Here's a cartoon depicting transcription which shows what happens at the sequence level. 
The DNA sequence is simply copied into an RNA sequence.

```{figure} ./images/Process_of_transcription.jpg
---
width: 600px
name: transcription_cartoon
---
Transcription zoomed in to sequence level \
Source: https://commons.wikimedia.org/wiki/File:Transcription_label_en_%28cropped%29.jpg
```
## RNA is translated to protein (or not)
Depending on the DNA sequence transcribed, different kinds of RNAs are synthesized.
Of these, **non-coding RNAs** go on to carry out whatever functions they have as RNAs.
On the other hand **coding RNAs** (or **messenger RNAs** or **mRNAs**) merely hold sequence information which is used for the synthesis of proteins by a process called **translation**.
A key player in translation is the molecule called **ribosome**.

Here's a microscope image of translation in action (simultaneously with transcription). 
Can you guess what is what in the image?

```{figure} ./images/protein_synthesis_microscope.png
---
width: 600px
name: protein_synthesis_microscope
---
Microscope image of translation and transcription\
Source: Picture taken from {cite}`Miller1970-so` , O. L., Hamkalo, B. A., & Thomas, C. A. (1970). Visualization of Bacterial Genes in Action. Science, 169(3943), 392–395. doi:10.1126/science.169.3943.392
```

Here's a cartoon showing what happens at the sequence level during translation.
Three nucleotides of mRNA, called a **codon**, get translated into an amino acid in the growing protein molecule.

```{figure} ./images/translation_cartoon.png
---
width: 400px
name: translation_cartoon
---
Translation at the sequence level
Source: {cite} Miller, O. L., Hamkalo, B. A., & Thomas, C. A. (1970). Visualization of Bacterial Genes in Action. Science, 169(3943), 392–395. doi:10.1126/science.169.3943.392
```

## The genetic code specifies which codon is translated to which amino acid
So then, what is the correspondence between codons and amino acids? 
It turns out there is a deterministic rule about which codon codes for which amino acid. 
This is called the **genetic code**, although it's more of a look-up table than a code. 
The figure below shows the ''standard'' genetic code. This is almost universal, but some deviations are known.


```{figure} ./images/GeneticCode21-version-2.png
---
width: 600px
name: genetic_code
---
Genetic code
Source: https://en.m.wikipedia.org/wiki/File:GeneticCode21-version-2.svg
```

## Flow of information in a eukaryotic cell
Although the idea of passing information from DNA to RNA to proteins remains the same for eukaryotes,
the process is more complicated. 

DNA is first transcribed into **premature RNA** or **nascent RNA** with a similar mechanism as in prokaryotes.
There are differences, of course. The RNA polymerase is of a different kind and so are the proteins necessary for the initiating transcription.
Also, since eukaryotic DNA is organized inside its nucleus, transcription happens inside the nucleus and there is no simultaneous translation. 

The **nascent RNA** then undergoes **splicing** in which some segments of the polynucleotide chain is removed and some other are retained. 
The ones removed are called **introns** and the ones retained are called **exons**. 
The resulting molecule is called a **mature RNA**. 
To complicated matters further, the same nascent RNA molecule can give rise to a slightly or entirely different mature RNA depends on the choice of introns and exons. 
This is called **alternative splicing**.
See figure below.

```{figure} ./images/DNA_alternative_splicing.gif
---
width: 600px
name: alternative_splicing
---
Splicing and alternative splicing
Source: https://en.wikipedia.org/wiki/Alternative_splicing#/media/File:DNA_alternative_splicing.gif
```

The mature RNA can be non-coding or coding. 
If latter, then like in the case of  it is translated into a protein sequence based on the genetic code as in {numref}`genetic_code`. 

## The Central Dogma of molecular biology
This one-way transfer of sequential information from nucleic acids to proteins (but not from protein to nucleic acids or protein to protein) is called the **central dogma of molecular biology**. Dogma ?! Now that's one word you wouldn't expect in a science context, but oh well.

## Further reading
Transcription and translations are both complex processes and highly regulated by many different factors.
See {cite}`transcription` and {cite}`translation` for a more detailed treatment of the two topics.

# References

```{bibliography} 
:filter: docname in docnames
```
