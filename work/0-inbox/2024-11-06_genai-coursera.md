---
aliases:
  - GenAI coursera
tags: []
title: genai-coursera
---

# GenAI coursera

## Attention
Take the following settence:
 The teacher taught the student with a book.

To the question who owns the book there isn't a definitive answer. The book can be from the student, the teacher or from the library even (information that is not present in the context).

A machine that judges a word by it's neighboors can't detect this nuace, i.e, if one focus on the word "book" it's only neighboor is "a" which doesn't give meaninful information. On the other hand, if we quadraticaly judge each word we can have some of the nuace a human can detect.

For instance, now there is an attention score between teacher-book and between book-student.

Side note on the mechanism:
In the context of NLP. One might think of the relation between word embedding and attention in the following way.

Consider an embedded sequence, i.e, a data matrix whose rows are of the corresponding embbed tokens. By using a large vector one can effectlivay encode a large array of possibility for the semanatic meaning of that token. By way of the attention mechanism, there is a mix of different features between different vectores, so we can see that we are going to get a 'collapse'

## Overview of architecture

Tokenizer - One needs to encode the words/phrases into numbers, by way of a dictionary.

- This dictionary can countain characters, words, or subwords. 
- exemple: Teacher can be decomposed into teach-er, i.e, two tokens. 

Embedding - At this stage, each token in the tokenized sequence is coverted into a vector.

- There is a second set to this stage. I don't get the details, but the idea is that the tokens are processed in parallel so to take the order information into account one need the embedding to preserve that. A word being the first token or second token has a completely different semantic meaning.

Self-attention - Apply the attention mechanism to the sequence. We can have multiple sets of self-attention(by way of learning parameters).

Feed forward/Output - Apply the fully connected network and then softmax in relation to the token dictionary.


## Types of prompting 
Zero shot learning is the act of ashking a model to perform a task it was directly trained to do. For instance performe sentiment analyzes on some new data:
```stdin
classify this review:
I loved this movie!
Sentiment:
(Expect model output)
```
Typically small models are not good in doing this. They benefict of getting some additional information. For instance by providing some exemples of the task we want it to perform it can help the model, the processe of adding a additonal information is called few shot learning. (typically more than 4-5 examples are not need).
This extra information has to be provided inside the context width; this is model dependent. If the max token lenght is excedded the input can't be fully processed, two possible approaches are: chucking or truncating.

Furthermore, FLAN-T5 has a set of templates available on git. This provide examples where the model `perfomed good` on the task. I don't really now why they work, but some of them have to be present on the trainning data. 

## Generative settings
There are some hyperparameters that can tune the generation of token.
Max new tokens - limits how many new token can be generated 

Hard sampling is simply taking an argmax in the final set. 
On another hand in random sampling the final token selection is decided based on the computed probabilty distribuiton; i.e, if one of the token is "cake" and it has 0.20, then 20% of the time the selected token would be cake. 
  - Sample top K - in the softmax layer only the K results are considered to be the generated token.

  - Sample top P - in the softmax layer, the classes are sorted by the highest probability. Then, only the classes contributing for the cummulative probability of P (for highest to lowest) are considered for the final choice.

Temperature - parameter that introduces some entropy on the probability distribution of token. 
$$
\frac{exp(z_{i}/T)}{\sum_{j}exp(z_{j}/T)}.
$$
For $T<1$ make the peak of the distribution more focused on the highest logit. For $T=1$ is the normal soft max. For $T>1$, it smoothly transforms the distribution 


