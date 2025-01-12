---
aliases:
  - fine-tunning-llm
tags:
  - LLM
  - PEFT
title: fine-tunning-llm
---

# fine-tunning-llm

## Introducing to fine tunning.
During pre-trainning models are trained in a self supervived way, for instance in BERT using the masking of tokens. During fine tunning tasks we work in a supervised learning regim, using the format 
PROMPT(), COMPLETION()

If we want to instruct the model to summarize text then we would give the following:

Summarize the following text:
(example text)
(example completion)

Recall that T5 had a list of template, see [genAI coursera](0-inbox/2024-11-06_genai-coursera.md), for prompting that worked better than a "random input". This explanes why it works. 

For full fine tunning we need need enough GPU ram to train a model of this size. 

Since the output of an LLM will be a token distribution in this supervised learning approch we use cross entropy loss. 

Fine tunning can lead to catastrophic forgetting. 

## Multi-task instruction fine tunning
Same as fine tunning but we train with multiple tasks in mind. 
For instance, FLAN (fine tuned language net) is exacly that. FLAN-T5 is the instruct version of of T5. 

Furthermore, when fine tunning for a task we can make the model more robust to human pertubations
To summarize a text, we can use 

(dialogue) Briefly summarize that dialogue (summary)
 Dialogue: (dialogue) What are the main points in that conversation? (summary)

Paper on FLAN: https://arxiv.org/pdf/2210.11416
## How to evaluate model performance 
 

## Parameter efficient fine-tunning (PEFT)
In this set of fine-tunning techniques most of the models weights are keeped frozen, so the chance to occur a catastrophic forgettings is smaller.

Methods 
  - Select a subset of initial LLM paramets
  - Reparametrize model weights using a low rank representation - LORA
  - Add trainable layers
    - add layers between attention or after feed forwards
    - prompt tunning


### Lora
Typically used to retrain the self attention layers, (Q,K,V). The idea is as follow:
  - Let Q be a matrix of dimension dxk, and freeze it's parameters
  - Consider matrices A, dxr, and B, rxk, where r is small interger. Then, AB has dimensions dxk, and so can be added to Q
  - Update Q->Q + AB for model trainning

In the end to update Q we only train (dxr) + (rxk) parameters, much less than (dxk).


This pertubations of the attention matrices can be see as extra modules. We can train different LoRa matrices for different tasks. Compared to full fine tunning, Lora typically is a little bit less performante but still achieves great results.


### Soft prompts
It's not prompt engineering. 
With the end goal of tunning a model to perform well in a specific task we can add a set of token 20-100 to the prompt, and throught supervised learning approach we learn the most optimal choice. 

The tokens don't generally represent typical words of natural language. They can instead be seen as optimal pertubations for the prompt for the designed task. Since there isn't a bijection between the token dictionary and the embedding space (only injectivity) the result likely won't be a word, but by looking at the nearest words in embedding space we can see they all have a similar semantic meaning.

As in the case of Lora, we can train different addaptive modules for different tasks.
