# Introduction to Hidden Markov Model (HMM)

An HMM is used to model sequential data. Sequential data are everywhere: weather, stock market, speech signals, natural languages, and importantly for us, biological sequences like DNA or protein.  

## Toy example for motivation
Let's get acquainted to the idea of HMMs through a toy example.
HMM folks seem to like examples concering weather, and 
[here](https://web.stanford.edu/~jurafsky/slp3/A.pdf) is a nice one for estimating weather from ice-cream consumption.


## A more relatable toy example
{cite}`Eddy2004-yu` shows a more relatable example of using an HMM for splice site estimation.

## Super concise mathematical description
To summarize, an HMM is used to model a sequence of **symbols** or **observations** $O = o_1, o_2, \ldots, o_T$.  

The model assumes that there is a corresponding unobserved sequence $Q = q_1, q_2, \ldots, q_T$ of hidden states that generated the observation sequence. 

The model assumes **Markovian property** on the states, which is that the probability of being on a particular state only depends on the previous state: 

$p (q_t \mid q_1, q_2, \ldots q_{t-1}) = p (q_t \mid q_{t-1})$.

It further assumes **output independence**, meaning that the probability of producing an output symbol depends only on the state that produced it and not on any other states or observations, i.e.
$p (o_t \mid q_1, \ldots q_T, o_1, \ldots o_T ) = p (o_t \mid q_{t})$.


::::
### Model specification
````{card} An HMM is specified by:  

- a set $\{S_1,S_2, \ldots, S_N\}$ of hidden states
- an alphabet of symbols 
- transition probabilities 
- emission probabilities
- an initial probablity distribution over the states 
````

### Probabilities on HMM

Let $O = o_1, o_2, \ldots, o_T$ be a sequence of observed symbol, and let $Q = q_1, q_2,\ldots, q_T$ be a sequence of states.

Given a fully specified HMM, we can compute various probabilities.

:::{dropdown} Forward probability

- The forward probability ${\alpha}_t(i)$ is the probability of observing the first $t$ symbols in $O$ and $o_t$ being emitted from state $S_i$, i.e. : \
    ${\alpha}_t(i) = p(o_1,o_2,\ldots, o_t, q_t=S_i )$.

- It is computed by the **forward algorithm**.

- The algorithm lets us compute the full probability of the observation $p(O)$.

:::

:::{dropdown} Backward probability
- The backward variable ${\beta}_t(i)$ is the probability that given $q_t = S_i$, we observe the remaining partial sequence $o_{t+1}$ to $o_T$: \
${\beta}_t(i) = p(o_{t+1},o_{t+2},\ldots, o_T \mid q_t=S_i)$.


- It is computed by the **backward algorithm**.
:::

:::{dropdown} Posterior state probability
- The posterior probability is the probability that $o_t$ was emitted from state $S_i$ given the entire observation sequence:
${\gamma}_t(i) = p(q_t = S_i | O)$

- It is computed using the forward-backward algorithm, since:\
${\gamma}_t(i) = \frac{{\alpha}_t(i){\beta}_t(i)}{p(O)}$.

:::


### Problems on HMM
There are three fundamental problems to solved with an HMM.

:::{dropdown} Evaluation
- The evaluation problem is to compute the probability $p(O)$ of the observation sequence given the model.

- It can be computed using the forward algorithm since:\
    $p(O) = \sum\limits_{i=1}^{N} {\alpha}_T(i)$

- It lets us define a probability distribution on the observation space.
- It can for when the HMM used as a classifier.
:::



:::{dropdown} Decoding (Viterbi) 
- Finding a path (state sequence) that "best" describes the observations is called decoding.

- One definition of best is a path $Q^*$ that maximizes the joint probability $p(O,Q)$.
$Q^* = \underset{Q}{\mathrm{argmax}}\ p(O,Q) $

- It is computed by the **Viterbi algorithm**, and is therefore called a **Viterbi path**.

- A problem with this decoding might be that there might be many (similar) paths with similarly high joint probability. 
:::

:::{dropdown} Decoding (posterior)
- Another way to define decoding is to find a path $\hat{Q} = \hat{q_1}, \hat{q_2}, \ldots \hat{q_T}$ such that 
  $q^*_t$ is the state with the highest posterior probability at time $t$, i.e.:

    $q^*_t = \underset{i}{\mathrm{argmax}}\ (\gamma_t(i))$ 

- A problem with this decoding is that $Q*$ might not be a valid state sequence if there are transitions that have zero probability.
:::


:::{dropdown} Model Training
- If state sequences are provided along with observation sequences, then the transition and emission probabilities are easily estimated just based on counts.

- If state sequences are not provided, then using Baum-Welch algorithm.
:::








## Bioinformatics application examples
Bioinformatics is full of examples of application of HMMs. They were the go-to model in the 90s and 2000s, and remain relevant todya.

They have been used for gene finding in prokaryotes and eukaryotes, for predicting chromatin states, etc.

A special kind of HMM called **profile HMMs** are used to model protein families or RNA families or transposon families
PFAM, DFAM, RFAM. More on profile HMMs later in the course. 

Another special kind of HMM called **pair HMMs** provide a probability distribution over the sequence alignment space allowing probabilistic interpretation of sequence alignment. More on this later when we deal with sequence alignments.

## Further reading
{cite}`Rabiner1989-ij` provides a tutorial on HMM.
{cite}`Yoon2009-rk` provides a summary of HMMs and examples of application to bioinformatics. 


https://bio.libretexts.org/Bookshelves/Computational_Biology/Book%3A_Computational_Biology_-_Genomes_Networks_and_Evolution_(Kellis_et_al.)/08%3A_Hidden_Markov_Models_II-Posterior_Decoding_and_Learning/8.02%3A_Posterior_Decoding

## References
```{bibliography} 
:filter: docname in docnames
```