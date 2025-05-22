# Genome annotation

## A vast sea of a,c,g,ts
Say you sequenced and assembled the genome of your favorite organism.
At this point, the sequence is just a vast sea of a,c,g, and ts.
To make any sense of it, you need to locate the genes and other elements in the genome sequence, a process called **genome annotation**. In the previous module, we viewed some of the annotations of the human genome on a genome browser. How are they obtained? Surely nothing come out of just visual inspection of sequences. 
This is a task for computers. 

## The annotation problem
Before looking at algorithms for annotation, let's discuss the problem a bit. 

The annotation problem takes a DNA sequence as input and applies labels to each nucleotide.

Take for example the problem of **gene finding**.
Recall the structure of a typical eukaryotic gene.

So given a sequence like so:


you want it to be labeled like so:



This problem is not new, similar versions of it have arisen in other domains.
In audio signal processing, the task of speech recognition is to label intervals of raw audio signals by words. 
In natural language processing, the problem of parts-of-speech tagging is to label words of a sentence by what part of speech (verb, noun, adjective) it is, or the problem of named entity recognition is to label words in a document by entries in a set of predefined categories (e.g. person, place, movie) . 


## The approaches

### By comparing against already annotated sequences
One approach is to take reference sequence(s) that are already well annotated, and find (sub-)sequences in the reference that are similar to (parts of) the input sequence. One way to find and measure sequence similarity is using **sequence alignment**, in which nucleotides of the query are aligned to those of the reference. We will discuss sequence alignment in greater detail in the next module. Based on the alignment(s) found, annotations on the reference are copied onto the query.

### Using hidden Markov models
Another method is to build a probabilistic model that incorporates the differences in statistical features of the labels. For example, the distribution of abundances of 3-tuples (aka 3-mers) inside exons vs. introns are quite different. The model can be trained on well-annotated reference sequences. We then run the input sequence through the model to compute a most likely annotation. 

A hidden Markov model provides an excellent framework for doing all of this. It is widely used in many bioinformatics tools, so let's spend some time on it. 