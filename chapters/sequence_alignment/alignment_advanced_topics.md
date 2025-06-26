# Advanced topics

## Devising a good scoring scheme
So far, we have assumed we are given a scoring scheme consisting of a substitution matrix and gap penalty. But where do the numbers come from ? Do they have any meaning? Is there a framework that guides the choice of the parameters?
To answer these question, we turn to the concept of **statistical hypothesis testing**, in which two (or more) hypotheses battle it out based on which explains the data the better. 
```{figure} ./images/hypothesis_testing.png
---
width: 600px
name: hypothesis_testing
---
Hypothesis testing :D.
```


### Statistical hypothesis testing
Let's look at statistical hypothesis testing through a coin-toss example.  
Suppose you wish to decide whether a suspicious looking coin is fair such that probability $p$ of head is 0.5 or that it is biased such that $p=0.7$. 

We first set the **null hypothesis** $H_0: p = 0.5$ and the **alternative hypothesis** $H_1: p =0.7$. 
Next, we run an **experiment** and collect data, which in this case is to toss the coin $n$ times, and observe the number of heads, $X$. 
Then, we decide on a **test statistic** which depends on $H$ and based which we decide whether or not to reject $H_0$ in favor of $H_1$.

Statistical theory (Neyman-Pearson Lemma) tells us that using the **likelihood ratio** as the test statistic is a good idea (most powerful). 
The likelihood ratio is the ratio of the likelihood of the data under $H_0 $ and $H_1$. 
The number of heads in $n$ independent tosses is binomially distributed,
```{math}
p(X=x) = {n \choose k}p^x(1-p)^{n-x}.
```
And so, the likelihood ratio is:
```{math}
LR(x) = \frac{p(x|H_1)}{p(x|H_0)}.
```
For $n=8$, here are its values:
| $x$   | $0$   |$1$    |$2$   |$3$   |$4$   |$5$   |$6$   |$7$   |$8$  |
|-------|-------|-------|------|------|------|-------|------|------|-------|
|$LR(x)$| 0.017 |0.039  |0.091 |0.213 |0.498 |1.162  |2.711 |6.325 |14.749 |

We reject $H_0$ in favor of $H_1$ if $LR(x)$ is greater than some threshold, say 1.
The threshold is arbitrary, but controls the rate of making a false positive and false negative errors.

### Sequence alignment as statistical hypothesis testing
As we have said before **a sequence alignment is a hypothesis**, and so it fits easily into the statistical hypothesis testing framework. Here's an analogy with the coin-toss example.

|                               | Coin toss         | Sequence alignment|
| ------------------------------| ----------------  | ------------------       |
| Null hypothesis($H_0$)        | Coin is fair      | Sequences are unrelated  |
| Alternative hypothesis ($H_1$)| Coin is biased    | Sequences are homologous   |
| Experiment                    |   Coin tosses     | Alignment                |
| Test statistic                | Likelihood ratio  | Alignment score |


Let's make this more concrete. To make life easy, we will consider a gapless global alignment between two sequences $A$ and $B$. 

The null hypothesis $H_0$ is that the two sequences are random. By random, we mean that each position of $A$ and $B$ is indepedent, and at each position we observe character $x$ with probability $f_A(x)$ and $f_B(x)$, respectively. Thus the likelihood of alignment under $H_0$ is:
```{math}
p(\text{alignment} \mid H_0) = \prod_{\text{all columns}} f_A(x)f_B(y).
```

The alternative hypothesis $H_1$ is that the two sequences are homologous. 
```{math}
p(\text{alignment} \mid H_1) = \prod_{\text{all columns}} p(x,y),
```
where $p(x,y)$ is the probability of seeing a character $x$ aligned to $y$ in an alignment of homologous sequences. 
This can either be computed using models of DNA or amino-acid evolution, or can be obtained empirically from ``highly trusted'' alignments between known homologous sequences (e.g. BLOSUM).

The likelihood ratio is :
```{math}
LR(\text{alignment}) = \prod_{\text{all columns}}\frac{p(x,y)}{f_A(x)f_B(y)},
```
It's computationally more convenient to use the **log of the likelihood ratio** instead:
```{math}
LLR(\text{alignment}) = \sum_{\text{all columns}}\log \frac{p(x,y)}{f_A(x)f_B(y)},
```

Recall that the score $S$ of a gapless alignment is obtained by adding the score of each column, i.e. :
```{math}
S = \sum_{\text{all columns}}s(x,y),
```
where $s(x,y)$ is the substitution score for $x$ and $y$ appearing in an alignment column.

Since statistical theory suggests using likelihood ratio (or its log) as a test statistic, it would be nice if $S$ can be cast as a likelihood ratio. This means setting the elements of the substitution matrix such that:
```{math}
s(x,y) = \log \frac{p(x,y)}{f_A(x)f_B(x)}.
```
So this suggests that the substitution scores between $x$ and $y$ shouldn't be arbitrary, but  should depend on the background probabilities of $x$ and $y$ and on the probability that $x$ and $y$ are found aligned in alignment of homologous sequences.

Follow-up questions (with brief answers):
- Can this be extend this to compute gap penalty? (Yes)
- Can the score set this way used for local alignments? (No, it's not most powerful, but in practice we just use it.)
- Do we have a set of confident alignments for every scenario? (No, but there are [methods](https://academic.oup.com/bioinformatics/article-lookup/doi/10.1093/bioinformatics/btw742) to customize the scoring scheme to any scenario. More on this when we discuss probabilistic model of sequence alignment)


## A probabilistic model of sequence alignment
It would be nice to turn the alignment space into a probabilistic model by attaching a probability distribution. 

One way to assign probabilities to sequence alignments is to model alignments using a hidden Markov model. 
TODO: Describe **pairHMM**.

Some of the nice things that can be done with this model is that you can compute quantities like the full probability of the sequence pairs (over all possible alignments), probability of an alignment column. It also allows fitting of alignment scoring parameters from data at hand (unaligned sequence) without the need for a confident set of alignments.

## References
- Sean R Eddy, Where did the BLOSUM62 alignment score matrix come from? Nature Biotechnology, V ol 22, Number 8, 2004
- https://doi.org/10.1093/bioinformatics/btz576
- https://doi.org/10.1093/bioinformatics/btw742