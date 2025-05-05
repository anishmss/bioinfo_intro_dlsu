# What is bioinformatics?
There are differing opinions on what makes up the field of bioinformatics, especially since there are similar overlapping fields with names like computational biology, systems biology, mathematical biology, etc.

In a broad sense, bioinformatics is the application of computational sciences (computer science, statistics, machine learning, mathematics, etc.) to problems in biology. Both these fields are evolving so fast, it's futile to fixate on the exact defintion of bioinformatics.

Let's instead look at how we have arrived at this point in time where modern biology and computational sciences go hand in hand.

## Why bioinformatics?

### The art of seeing

First, let's go back in time to somewhere around the 17th century. 
The state of biology back then is described by the award winning writer, scientist, doctor Siddhartha Mukherjee, in his book *The Song of the Cell* as:

> [Cell biology] was simply the art of seeing: the world measured, observed, and dissected by the eye."

 
Indeed, curious folks like Robert Hooke and von Leeuwenhoek were busy peering into the lens of their fancy toy called the **microscope**. 
Here's the one that Robert Hooke used.
```{figure} ./images/Hooke-microscope.png 
---
width: 400px
name: microscope
---
Microscope that Robert Hooke used (?) \
Source: https://en.wikipedia.org/wiki/Robert_Hooke#/media/File:Hooke-microscope.png
```

And were they seeing some really cool stuff ! \
Just by looking, they were able to discover cells and a lot about the morphology of cells.

Even until the early 20th century, microscopes -- more sophisticated ones, of course -- were still the mainstay of important biological discoveries. For example, David von Hansemann and Theodor Boveri observed dividing cancer cells in their microscopes, leading to the idea that cancers are a consequence of chromosomal abnormalities.
https://www.cshlpress.com/default.tpl?cart=1743749853588049005&fromlink=T&linkaction=full&linksortby=oop_title&--eqSKUdatarq=659
(seecancer genome stratton)

### The new lens
Fast-forward back to present day. 
Scientists today have access to more powerful ''lenses'' -- e.g. electron microscopy, mass spectrometry, etc. 
But one technology that has propelled computer science directly to the center stage of biology is the **sequencing technology**.

A sequencer, to describe simply, is a machine that takes in a fragment of DNA molecule and produces the sequence of bases (a,c,g,t) in that molecule. 

There are two interesting things about the history of sequencing technology.
The first is the rapid pace of development, especially in the last two decades or so.
One of the earliest versions of sequencers was developed by Frederick Sanger and colleagues back in 1977 (leftmost point in the image below), and this technology was the mainstay of major projects, e.g. the human genome project which published a draft version of the human genome sequence in 2001. 
However, Sanger sequencing is very slow and expensive, and not really suited to sequence big genomes. 
Sometime around mid-late 2000s, we started seeing sequencer with dramatically higher throughput.
With prices coming down, this has resulted in a rush of sequence-your-favorite-organism projects, all over the world.

The second interesting thing is the versatility of this technology. 
Although the biochemistry of sequencers are only good to read DNA, 
clever people have come up with ways to utilize sequencers to measure all sorts of biological stuff.



```{figure} ./images/History_of_sequencing_technology.jpg 
---
width: 800px
name: sequencing_history
---
History of sequencing technology
Source: https://en.wikipedia.org/wiki/DNA_sequencing#/media/File:History_of_sequencing_technology.jpg
```

### To see, we need to more than look
Each run of modern-day sequencer can produce tons of sequence data.

Let's say you wish to identify mutations that might be involved in the initiation of acute myeloid leukemia. 
To do so, you might need to sequence tumor and normal genomes from a patient. To ensure generalizability of your observation, you might want to collect samples from multiple patients. 
When the sequencing is done and you look at the raw dataset, you will be facing a whopping several hundreds of Gigabytes of text data, even when compressed.

Or, let's say you are interested in epidemiology of a pathogen, say HIV/AIDS or SARS-Cov-2/Covid or TB.  Compared to mammalian genomes, bacterial and viral genomes are smaller by many, many orders, but then you will likely want to sample hundreds of patients to be able to establish some phylodynamic patterns. Again, you are looking at several tens of Gigabytes of text data. 

So how do we go from mountains of sequence data to insights into biological questions and hypotheses.
It really depends on the question at hand, but it general, you will first need efficient tools to process the sequence data into some form that can be fed into statistical/machine-learning/artificial intelligence (what's the difference anyway?) model, and then use those models to find patterns, make prediction, draw inferences, etc.

Being able to do this requires knowledge of data-structures, algorithms, statistics, machine learning, what we collectively call bioinformatics. 

## Further reading
A brief history of bioinformatics https://doi.org/10.1093/bib/bby063.
