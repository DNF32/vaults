---
aliases:
  - llm-deployment
tags: []
title: llm-deployment
---

# llm-deployment
Given the size of LLM models there are some optimizations that one can make when deploying the model. 

We are going to see three forms of this model reductions. 

## Distillation 
Given a pre trainned LLM (teacher), we take a set of completions and created a set of completions. This trainning set will be used to create a new smaller LLM.

Frezze the teacher's weights and consider and forward pass theprompt through both models. In the final softmax layer we use temperature setting bigger than 1, and compare them using cross entropy.

On another hand, we compute the hard predictions of the student model, T=1, and compare them with the grouth truth generatedby the LLM. 

Take a linear combination of both loss functions and backward pass.

This technique is typically used with encoder models and not generative ones.

## Quantiziton and prunning 
Quantizaton chooses a simpler format to store the model weights. There is some nuaces to consider. 

Prunning removes weight that are close to 0, so they don't contribute for activations.

## RAG
Can help with the knowdlege cut off problem and with allucinations. 

## Interacting with external apps
LLM can be used as a kind of 'reasoning' engine via completions to trigger different API call. Prompts need to be carefully formatted. 

For instance PAL (program-aided language models) can solve the lack of math reasoning an LLM lacks by acessing a python interpreter.  

The basic idea is that when one wants to solve problem of this form add an example of a question and a template for a solutions using python code. This will trigger the LLM to produce python code that can correctly do tasks like arithamatic. 

## React

A react template consists of:
- Question
- Thought - example on how to decompose the question; actions to take 
- Action - take this action 
- Obseravation - combine the thought with the information receive from the action

This will loop until finish action is triggered. 

To use this methodology preappend the instruction (high level guidelines and possible actions). Add the react template with examples. Finish by adding the question. 


## Infrastructure LLM architectures




