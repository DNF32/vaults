---
aliases:
  - pre-trainning-scaling law
tags: []
title: pre-trainning-scaling-law
---

# pre-trainning-scaling law


## Trainning vs Inference size
At inference time only the weights are needs to be store, aprox 4 bytes (float with 32bit precision), however during trainning more information is required.
|  Adam (2 states )| 8 bytes  | 
| Gradients| 4 bytes |
|  Activations and temp | 8 bytes  |

So each parameter will need 24 bytes at trainning time.

Given the size of the models the space to store them becomes quite unresonable quite fast. At inference time there is a tenchique used to reduce this, `Quantization`. This essencially entails into projecting the data type used to store the weights into a lower dimensional one. For instance, FP32 (4 bytes) into FP16 (2 bytes).

There is another format known as BFLOAT16 (2 bytes), that is a hybrid that can also be used for trainning.

## Multi-GPU architetures
### Smaller models
When the model fits inside a single GPU we can speed up trainning with Distributed Data Parallel (`DDP`).
  - Load the model inside each GPU (with same weights)
  - Load different parts of the processes batch into different GPUs 
  - Forward pass and backwards pass.
  - Synchronize the gradients to compute a single batch gradient.

Effectivaly is doing a batch inside the batch.

### Bigger models
Fully sharded data parallel
NOt:
Model parallelism
Tensor parallelism

FSDP enables the use of data parallelism without the cost of full model replication.
[FSDP](https://www.youtube.com/watch?v=By_O0k102PY)


This are the key concepts for parallelism in NN trainning:
- Data parallelism: split the batch into multiple smaller batches. 
- Pipeline parallelism: split the model across multiple devices. Create a pipeline.
- Tensor parallelism: split the computation of tensors into mutiple devices. Each device handles part of the matrix mutiplication. This can be visualized as a horizontal split of the model layers.

Data + pipeline
- If we have 8 GPU, we can split the model into 4 GPU and then we effectivaly have to identical pipelines.

Data + pipeline + Tensor
- For instance consider the use of 16 GPU.
- Split the model into 4 pipeline stages
X---X---X---X
- Then each each stage can be split horizontaly between two GPU
X1---X1---X1---X1
|    |    |    |    X1+X2 represent the X layer
X2---X2---X2---X2

- This in total used 8GPU, so we can replicate this setup in the remaining 8 GPU (data parallelism).

## Scaling laws/ efficient compute frontier
Compute is measure in <number>petaflop/sec-day
- Number of floating point operation measure at a rate of petaFLOP per second for one day. 


There's an intimate relation between (Kaplan 'Scaling laws for neural language models'):
- Dataset size
- Compute budget
- Model size

To find the optimal balance is not a easy task. In the chinchilla paper the authors argue that model's like GPT-3 may be over-parameterized and under-trained, i.e, given a smaller model and a larger dataset we can get the same level of performance (this in theory would need less compute). 

Rough guideline 20x the number of parameter in number of tokens. Llama 65B follows this principel and in fact get's GPT-3 performance with 1/3 of the parameters.

## Pre-trainning from domain adaptation
As the name suggest some task are so specificy that a general set of pre-trainning, where the model learns relationships between different concepts, might not be enought to learn tasks like law and medical tasks.

The type of language used is law is much different than the one present in books, conversations or essays/jornalism. Given this, the proportion of trainning date will be much smaller and hence the model won't have the best of time executing tasks like summarizing a transcribt from court. 

The medical domain, a model might not be exposed to short hands of doctors, or even some non recurring rare conditions.

BloombergGPT a domain specific model. (BlombergGPT paper).


## Some papers to read
- Attention is all you need
- Language Models are Few-Shot Learners
- LLaMA: Open and Efficient Foundation Language Models
- BloombergGPT: A Large Language model - used chinchilla
- Training Compute-Optimal Large Language Models - introduced chinchilla
