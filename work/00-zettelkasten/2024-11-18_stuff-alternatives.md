---
aliases:
  - stuff-alternatives
tags:
  - LLM
  - RAG
title: stuff-alternatives
---

# stuff-alternatives
When retreving document we need a way to feed that information back into de LLM followed by the Prompt.

1. Stuff just takes all the information and puts it into context
2. Map reduce map part of the task to an LLM, i.e, the input is further split into chuncks an are processed separatly. The results are agreggated and further processed.
3. Refine loops over the retrieved chunks. The answer gradually becames bigger.
4. Map rerank - A bit confusing  #TODO

