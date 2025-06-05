# Introduction to hidden Markov model 

A hidden Markov model (HMM) is used to model sequential data. Sequential data are everywhere: weather, stock market, speech signals, natural languages, and importantly for us, biological sequences like DNA and protein sequences.  

## Toy example for motivation
Let's get acquainted to the idea of HMMs through a toy example.
HMM folks seem to like examples concering weather, and 
[here](https://web.stanford.edu/~jurafsky/slp3/A.pdf) is a nice one for estimating weather from ice cream consumption.


## A more relatable toy example
{cite}`Eddy2004-yu` shows a more relatable example of using an HMM for splice site estimation.

## Super concise mathematical description
To summarize, an HMM is used to model a sequence of **symbols** or **observations** $O = o_1, o_2, \ldots, o_T$.  

The model assumes that there is a corresponding unobserved sequence $Q = q_1, q_2, \ldots, q_T$ of hidden states that generated the observation sequence. 

The model assumes **Markovian property** on the states, which is that the probability of being on a particular state only depends on the previous state: 

$p (q_t \mid q_1, q_2, \ldots q_{t-1}) = p (q_t \mid q_{t-1})$.

It further assumes **output independence**, meaning that the probability of producing an output symbol depends only on the state that produced it and not on any other states or observations, i.e.
$p (o_t \mid q_1, \ldots q_T, o_1, \ldots o_T ) = p (o_t \mid q_{t})$.

### Model specification
````{card} An HMM is specified by:  

- a set $\{S_1,S_2, \ldots, S_N\}$ of hidden states
- an alphabet of symbols 
- transition probabilities 
- emission probabilities
- an initial probablity distribution over the states $\pi_{S_1},\pi_{S_2}, \ldots,  \pi_{S_N}$.
````

### Probabilities on HMM

Given a fully specified HMM, we can compute various probabilities.

:::{dropdown} Joint probability
- Given an observation sequence $O = o_1, o_2, \ldots, o_T$ and a state sequence $Q = q_1, q_2,\ldots, q_T$, the joint probability of the sequence-state pair is: 
```{math}
p(O,Q) = \pi_{q_1} p(o_1|q_1) p(q_{2}|q_{1}) \cdots p(q_{T-1}|q_{T}) p(o_T|q_T)
```
- Since $Q$ is hidden, this probably is usually not computed and is only conceptual.
:::
:::{dropdown} Forward probability

- Given an observation sequence $O = o_1, o_2, \ldots, o_T$, the forward probability ${\alpha}_t(i)$ is the probability of observing the first $t$ symbols in $O$ and $o_t$ being emitted from state $S_i$, i.e.: 
```{math}
{\alpha}_t(i) = p(o_1,o_2,\ldots, o_t, q_t=S_i ).
```

- It can be computed by the **forward algorithm**.
:::


:::{dropdown} Backward probability
-  Given an observation sequence $O = o_1, o_2, \ldots, o_T$, the backward variable ${\beta}_t(i)$ is the probability that given $q_t = S_i$, we observe the remaining partial sequence $o_{t+1}$ to $o_T$: 
```{math}
{\beta}_t(i) = p(o_{t+1},o_{t+2},\ldots, o_T \mid q_t=S_i).
```

- It can be computed by the **backward algorithm**.
:::


:::{dropdown} Posterior state probability
- The posterior probability is the probability that $o_t$ was emitted from state $S_i$ given the entire observation sequence:

```{math}
{\gamma}_t(i) = p(q_t = S_i |O).
```

- It is related to the forward and backward probabilities as:
```{math}
{\gamma}_t(i) = \frac{{\alpha}_t(i){\beta}_t(i)}{p(O)}.
```
:::



### Problems on HMM
There are three fundamental problems to solved with an HMM.

:::{dropdown} Evaluation
- Given an HMM model, and an observation sequence $O$, the evaluation problem is to compute the probability $p(O)$, marginalizing out the state sequences, i.e.:
```{math}    
p(O) = \sum\limits_{\mathrm{all} Q} p(O,Q).
```

- It can be computed using the forward algorithm since:
```{math}    
p(O) = \sum\limits_{i=1}^{N} {\alpha}_T(i).
```
- It lets us define a probability distribution on the observation space.
- It can be used when the HMM is a classifier.
:::



:::{dropdown} Decoding (Viterbi) 
- The problem of finding a path (state sequence) that "best" describes the observations is called decoding.

- One definition of best is a path $Q^*$ that maximizes the joint probability $p(O,Q)$, i.e.:
```{math}
Q^* = \underset{Q}{\mathrm{argmax}}\ p(O,Q) 
```

- It can be computed by the **Viterbi algorithm**, and is therefore called a **Viterbi path**.

- A problem with this decoding is that there might be many paths with similarly high joint probability. 
:::

:::{dropdown} Decoding (posterior)
- Another way to define decoding is to find a path $\hat{Q} = \hat{q_1}, \hat{q_2}, \ldots \hat{q_T}$ such that 
  $\hat{q}_t$ is the state with the highest posterior probability at time $t$, i.e.:
```{math}
    \hat{q}_t = \underset{i}{\mathrm{argmax}}\ (\gamma_t(i))
```

- A problem with this decoding is that $Q*$ might not be a valid state sequence if there are transitions that have zero probability.
:::


:::{dropdown} Model Training
- If state sequences are provided along with observation sequences, then the transition and emission probabilities are easily estimated just based on counts.

- If state sequences are not provided, then using Baum-Welch algorithm.
:::



## Bioinformatics application examples
Bioinformatics is full of examples of application of HMMs. 

They have been used for gene finding in prokaryotes and eukaryotes, for predicting chromatin states, etc.

A special kind of HMM called **profile HMMs** are used to model protein families or RNA families or transposon families
PFAM, DFAM, RFAM. More on profile HMMs later in the course. 

Another special kind of HMM called **pair HMMs** provide a probability distribution over the sequence alignment space allowing probabilistic interpretation of sequence alignment. More on this later when we deal with sequence alignments.

## Further reading
This was a whirlwind tour of HMM. We skipped past most of the technical details of the algorithms. For more detailed treatment, refer to one or more of the following. {cite}`Rabiner1989-ij` provides a tutorial on HMM. {cite}`Yoon2009-rk` provides a summary of HMMs and examples of application to bioinformatics. 
[Here](https://bio.libretexts.org/Bookshelves/Computational_Biology/Book%3A_Computational_Biology_-_Genomes_Networks_and_Evolution_(Kellis_et_al.)/07%3A_Hidden_Markov_Models_I/7.01%3A_Introduction) is an online book discussing HMMs along with bioinformatics applications. Chapter 3 of Durbin et al. Biological sequence analysis is another good option. 

## References
```{bibliography} 
:filter: docname in docnames
```