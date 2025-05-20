# A cell is an information system 
A cell can be thought of as an information system with DNA, RNA, and proteins as the key players. 
Let's look at some of the ways by which information is passed from molecule to molecule.


## DNA →  DNA
Before a cell divides, it needs to prepare an entire new copy of genome.
This is done by the process of **replication**.
Differences between prokaryotes and eukaryotes (Write me).


## DNA →  RNA

There are segments of DNA called **genes**, whose sequence information is used to synthesize RNA molecules. (As a side note, biology uses the word gene to mean so many different things. See {cite}`Gerstein2007-si` for the evolution of this term.)
The biological process by which this happens is called **transcription**. 
As with replicatoin, there are difference in how this happens in prokaryotes vs. eukaryotes

### Prokaryotes
A key molecule that carries out transcription is called **RNA polymerase**. 
Here is a microscope image of a bacterial gene being transcribed. Notice how many RNA molecules are being synthesized from a single DNA molecule.
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

### Eukaryotes
In eukaryotes, DNA is first transcribed into **premature RNA** or **precursor RNA** or **nascent RNA**. 
Different to prokaryotes, three types of RNA polymerases are employed depending on the gene being transcribed. Also, since eukaryotic DNA is organized inside its nucleus, transcription happens inside the nucleus.

The nascent RNA then undergoes **splicing** in which some segments of the polynucleotide chain is removed and some other are retained. The ones removed are called **introns** and the ones retained are called **exons**. The resulting molecule is called a **mature RNA**. 

To complicated matters further, the same nascent RNA molecule can give rise to a slightly or entirely different mature RNA depends on the choice of introns and exons. 
This is called **alternative splicing**.
See {numref}`alternative_splicing` below.


## RNA → Protein
Transcription results in different kinds of RNAs being synthesized.
Of these, **non-coding RNAs** go on to carry out whatever functions they have as RNAs.
On the other hand **coding RNAs** (or **messenger RNAs** or **mRNAs**) merely hold sequence information which is used for the synthesis of proteins by a process called **translation**.
A key player in translation is the molecule called **ribosome**.

Here's a microscope image of bacterial translation in action (simultaneously with transcription). 
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

In eukaryotes, alternative splicing means that a single gene can give rise to variant proteins which are referred to as **protein isoforms**.

```{figure} ./images/DNA_alternative_splicing.gif
---
width: 600px
name: alternative_splicing
---
Splicing and alternative splicing
Source: https://en.wikipedia.org/wiki/Alternative_splicing#/media/File:DNA_alternative_splicing.gif
```


### The genetic code specifies which codon is translated to which amino acid
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

## RNA →  DNA
Since RNA and DNA speak essentially the same language, it is perhaps not surprising that RNA can be 
**reverse transcribed** to create a **complementary DNA** or **cDNA**. This happens, for example, when HIV-1 virus, which has RNA as its genetic material reverse transcribes it into DNA which then is integrated into the host genome. Another example is that of human telomere extension by an enzyme called telomerase reverse transcriptase. Experimental techniques for measuring RNA abundance or sequencing RNA also artifically carry out reverse transcription. Remember all the RT-PCR tests for SARS-Cov-2 you were forced to take during the pandemic?

## The Central Dogma of molecular biology
We have seen the various modes of transfer of sequential information between molecules. 
It turns out the transfer of information from nucleic acids to proteins (but not from protein to nucleic acids or protein to protein) is called the **central dogma of molecular biology**. Dogma ?! Now that's one word you wouldn't expect in a science context, but oh well. 

## Further reading
Replication, transcription, translations are all complex processes and highly regulated by many different factors.
See {cite}`transcription` and {cite}`translation` for a more detailed treatment.

# References

```{bibliography} 
:filter: docname in docnames
```
